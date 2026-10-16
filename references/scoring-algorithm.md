# Cosmetic Analysis Agent — Scoring Algorithm v1.0

## Overview

The scoring system translates structured analysis into a numeric score (0–100) with an accompanying confidence indicator. It operates in two modes:

| Mode | Trigger | Behavior |
| --- | --- | --- |
| **Standard** | Input quality (the `I` factor) ≥ 0.60 | Full pipeline; a numeric score is emitted only if **overall** confidence ≥ 0.60 |
| **Conservative** | Input quality (`I`) < 0.60, **or** overall confidence < 0.40 | Qualitative assessment only, no numeric score |

The two thresholds measure different things and are both defined in §4.

---

## 1. Weight Profiles (from M19)

Each product category loads a distinct weight profile after recognition. All weights sum to 100%.

> **Authority:** `SKILL.md` Step 8 is the entry point for weight profiles and lists the nine categories whose profile lives in their own spec file (Body Wash, Shampoo, Body Lotion, Hair Conditioner, Lip Balm, Anti-Acne Serum, Exfoliation, Toner, Mask). The profiles below cover the remaining categories; where this file and a category spec disagree, **the spec wins**. Dimension names here are the legacy M19 names (`Function`, `UV Protection`, `Barrier Function`) — treat them as synonyms of `Core Effectiveness`.

### 1.1 Default Profile (fallback)

| Dimension | Weight |
| --- | --- |
| Core Effectiveness | 40% |
| Formula Architecture | 25% |
| Support System | 10% |
| Safety | 15% |
| Skin Adaptation | 10% |

### 1.2 Cleanser

| Dimension | Weight |
| --- | --- |
| Function (Cleansing Efficacy) | 30% |
| Architecture (Surfactant System) | 25% |
| Safety (Irritation / Barrier Impact) | 30% |
| Support System | 10% |
| Skin Adaptation | 5% |

### 1.3 Sunscreen

| Dimension | Weight |
| --- | --- |
| UV Protection | 35% |
| Architecture (Film Former / Dispersion) | 25% |
| Safety (Photostability / Penetration) | 20% |
| Support System | 15% |
| Skin Adaptation | 5% |

### 1.4 Serum / Treatment

| Dimension | Weight |
| --- | --- |
| Core Active | 35% |
| Delivery System (Architecture) | 20% |
| Safety | 20% |
| Support System | 15% |
| Skin Adaptation | 10% |

### 1.5 Moisturizer

| Dimension | Weight |
| --- | --- |
| Barrier Function (Occlusion + Humectant) | 30% |
| Architecture (Emulsion Quality) | 25% |
| Support System (Barrier Repair) | 15% |
| Safety | 20% |
| Skin Adaptation | 10% |

### 1.6 Infant / Sensitive Skin Product

| Dimension | Weight |
| --- | --- |
| Safety | 35% |
| Architecture (Minimalism) | 20% |
| Function | 15% |
| Support System | 15% |
| Skin Adaptation | 15% |

---

## 2. Dimension Scoring

Each dimension score is computed independently, then multiplied by its weight.

```
Dimension_Score = Presence_Score × Evidence_Multiplier × Interaction_Modifier
Dimension_Contribution = Dimension_Score × Weight
Total_Raw = Σ(Dimension_Contribution)   // 0–100
```

### 2.1 Presence Score (PS)

How well does this product fulfill the dimension?

| PS | Criteria |
| --- | --- |
| 1.00 | Multiple well-recognized, well-positioned ingredients directly serving this dimension |
| 0.85 | At least one strong ingredient + adequate supporting composition |
| 0.70 | One recognized ingredient, basic but functional |
| 0.50 | Weak or questionable ingredient choices; may partly function |
| 0.30 | Marginal contribution; relies mostly on indirect effects |
| 0.10 | Trace-level or non-functional presence |
| 0.00 | No ingredient serves this dimension |

**Position adjustment**: An ingredient listed after fragrance/parfum in the INCI list (typically ≤0.5–1%) receives a −0.15 penalty to its contribution within that dimension. Ingredients in the first 5 positions receive a +0.05 bonus.

**Count cap**: Having 10 similar ingredients does not increase PS beyond what 2–3 well-chosen ones would achieve. Redundancy is neutral, not additive.

### 2.2 Evidence Multiplier (EM)

Derived from M17 evidence levels. For each dimension, use the **highest** evidence level among its key ingredients.

| Evidence Level | EM |
| --- | --- |
| A — Meta-analysis / Systematic Review | 1.00 |
| B — Clinical Trial (RCT, in vivo human) | 0.90 |
| C — In Vitro / Laboratory study | 0.70 |
| D — Expert Opinion / Textbook | 0.50 |
| E — Marketing Claim / No evidence | 0.20 |
| Unknown (no database match) | 0.40 |

**Mixed evidence**: When a dimension has multiple ingredients at different levels, the EM is a weighted blend:

```
EM = (EM_highest × 0.6) + (EM_average_of_others × 0.4)
```

### 2.3 Interaction Modifier (IM)

Derived from M16 interaction analysis. Applied **per dimension** — only interactions relevant to that dimension affect its modifier.

| Interaction Type | Default IM |
| --- | --- |
| Synergy (confirmed) | 1.10 |
| Independent (default) | 1.00 |
| Antagonism (confirmed) | 0.85 |
| Conflict (safety concern) | 0.70 |

Those four are the **type defaults**. The interaction library carries a **precise per-rule IM** for every entry, and precise values take precedence — the type is a qualitative label, the IM is a quantitative value:

| Type | IM values actually used in `interaction-rules.md` |
| --- | --- |
| Synergy | 1.05 (mild) · 1.10 (default) · 1.15 (strongest — CEF triple, Rule 3) |
| Independent | 1.00 |
| Antagonism | 0.85 (default) · 0.90 (mild) |
| Conflict | 0.70 (default) · 0.75 · 0.80 · 0.85 (mildest) |

**Resolution order:** if the pair has a rule in `interaction-rules.md`, use that rule's IM. Fall back to the type default only when a pair is graded by type without a rule of its own. A `Conflict` scored at 0.75 is therefore deliberate and correct — a milder conflict than one scored 0.70. Twelve of the 32 rules use a non-default value in this way; none of them is an error.

**Multiple interactions**: When multiple interactions affect one dimension, use the **product** of all modifiers:

```
IM = IM₁ × IM₂ × ... × IMₙ
```

**Capped** at [0.50, 1.20].

**No invented interactions**: If the interaction rules database has no entry for a given pair, assume Independent (1.00). Never fabricate.

---

## 3. Final Score

```
Final_Score = Σ(PS_d × EM_d × IM_d × Weight_d)   for each dimension d
```

Rounded to nearest integer.

---

## 4. Confidence Calculation (M15)

Confidence is a **separate indicator** reported alongside the score, not multiplied into it.

```
Confidence = 5 / (1/I + 1/D + 1/M + 1/X + 1/C)
  I = Input Quality         (M14 validation_confidence / 100)
  D = Database Match Rate   (matched / total ingredients)
  M = Mechanism Certainty   (actives with known mechanisms / total actives)
  X = Interaction Certainty (known pairs / total pairs)
  C = Concentration Certainty (average per-ingredient confidence)
```

If any factor is 0, drop that term: `Confidence = N / Σ(1/factor_i)`.

The harmonic mean is deliberate — **the weakest factor dominates**. Example from `confidence-engine-spec.md`: I/D/M/X/C = 0.80/0.85/0.10/0.90/0.80 gives an arithmetic mean of 0.69 but a harmonic mean of 0.30.

| Confidence Range | Label | Numeric score? | Language |
| --- | --- | --- | --- |
| ≥ 80% | 🟢 High | Yes | Definitive |
| 60–79% | 🟡 Medium | Yes | Hedged ("appears to", "likely") |
| 40–59% | 🟠 Low | **No** | Qualitative + caveats |
| < 40% | 🔴 Critical | No | "Insufficient data" |

### Two thresholds that are not the same threshold

| Threshold | Applies to | Trigger effect |
| --- | --- | --- |
| **Input quality (the `I` factor) < 0.60** | the input alone (M14) | request better input; enter conservative mode |
| **Overall confidence < 0.40** *(40–59% also suppresses the number)* | the whole analysis (M15) | conservative mode; no numeric score |

The first can fire on a blurry photo even when everything else is solid; the second fires when the analysis as a whole is under-determined. A product can pass the first and fail the second — read them as separate gates, never as one 60% rule.

`confidence-engine-spec.md` is the authoritative definition of both; if this section and that file ever disagree, that file wins.

### Conservative Mode Rules
- Do not output a numeric score
- Report: "Score: Insufficient data for reliable scoring"
- Use qualitative language only ("appears adequate", "may be insufficient")
- Explicitly list all data gaps
- Confidence label: the tier name from the table above + "Conservative Mode" (🟠 Low or 🔴 Critical)

---

## 5. Marketing Penalty

Marketing ingredients (from the M13 ontology: **Botanical, Marketing, Fragrance, Colorant** categories) contribute **zero to positive scoring** in every dimension. Two deduction mechanisms exist. Apply **exactly one** — never both.

### 5.1 External penalty — 5-dimension profiles

Applies to every category except Body Wash and Shampoo.

If more than 30% of listed ingredients fall into marketing categories:

```
Marketing_Penalty = (marketing_ratio - 0.30) × 15
```

Applied as a deduction from Final_Score, capped at −10 points.

### 5.2 In-profile dimension — 6-dimension profiles (Body Wash, Shampoo only)

These two profiles carry a `Marketing` dimension **inside** the 100-point weights (Body Wash 10, Shampoo 5). That dimension **is** their marketing deduction, and like the external penalty it can only subtract.

| Product category | Mechanism | Extra step |
| --- | --- | --- |
| Body Wash, Shampoo | 5.2 — in-profile Marketing dimension | Do **not** apply the 5.1 formula |
| Every other category | 5.1 — external `Marketing_Penalty` | — |

Applying both would deduct twice for the same ingredients. That double-deduction is the defect this section exists to prevent.

---

## 6. Edge Cases

| Scenario | Handling |
| --- | --- |
| Product category unrecognized | Use Default Profile; flag in report |
| Empty ingredient list | Validation → Unknown → Conservative Mode |
| All ingredients are marketing | PS = 0 for all function dimensions; score ≤ 15 |
| 100% database match, all evidence A | Max confidence; still capped at presence reality |
| Conflicting interactions in same dimension | Report all, use worst-case IM |
| Ingredient appears in 2+ ontology categories | The ontology map is single-primary (Usage Rule 6): `Risk [R]` overlays are additive, every other ingredient has exactly one section. If an input is still ambiguous, apply the Usage Rule 6 resolution principle and flag it. |

---

## 7. Example Walkthrough

**Product**: Niacinamide 10% Serum
**Category**: Serum → Weight Profile 1.4
**Ingredients**: Aqua, Niacinamide, Butylene Glycol, Dimethicone, Phenoxyethanol

### Dimension: Core Active (35%)

| Factor | Value | Reason |
| --- | --- | --- |
| PS | 0.85 | Niacinamide is a well-recognized active; good position (2nd) |
| EM | 0.90 | Niacinamide has Level B evidence (multiple RCTs for hyperpigmentation) |
| IM | 1.00 | No interactions relevant to this dimension |
| **Dimension Score** | 0.85 × 0.90 × 1.00 = **0.765** | |
| **Contribution** | 0.765 × 35 = **26.8** | |

### Dimension: Architecture (20%)

| Factor | Value | Reason |
| --- | --- | --- |
| PS | 0.70 | Simple aqueous serum with basic silicone; adequate but not sophisticated |
| EM | 0.50 | Textbook formulation; no special delivery evidence |
| IM | 1.00 | No interactions |
| **Contribution** | 0.70 × 0.50 × 1.00 × 20 = **7.0** | |

### Dimension: Safety (20%)

| Factor | Value | Reason |
| --- | --- | --- |
| PS | 0.85 | Few ingredients, low irritancy profile, adequate preservation |
| EM | 0.70 | Phenoxyethanol safety is well-documented (C-level) |
| IM | 1.00 | No conflicts |
| **Contribution** | 0.85 × 0.70 × 1.00 × 20 = **11.9** | |

### Dimension: Support System (15%)

| Factor | Value | Reason |
| --- | --- | --- |
| PS | 0.50 | Butylene glycol as humectant; Dimethicone as texture modifier; no antioxidants |
| EM | 0.50 | Standard ingredients, textbook-level evidence |
| IM | 1.00 | No interactions |
| **Contribution** | 0.50 × 0.50 × 1.00 × 15 = **3.75** | |

### Dimension: Skin Adaptation (10%)

| Factor | Value | Reason |
| --- | --- | --- |
| PS | 0.70 | Suitable for most skin types; minimal irritants |
| EM | 0.70 | Niacinamide compatibility is well-studied |
| IM | 1.00 | No interactions |
| **Contribution** | 0.70 × 0.70 × 1.00 × 10 = **4.9** | |

### Final Calculation

| Dimension | Contribution |
| --- | --- |
| Core Active | 26.8 |
| Architecture | 7.0 |
| Safety | 11.9 |
| Support System | 3.75 |
| Skin Adaptation | 4.9 |
| **Total** | **54.4 → 54** |

### Confidence

| Factor | Value |
| --- | --- |
| Input Quality (I) | 100% (complete, readable) |
| DB Match Rate (D) | 100% (5/5 ingredients matched) |
| Mechanism Certainty (M) | 100% |
| Interaction Certainty (X) | 100% |
| Concentration Certainty (C) | 90% (niacinamide is declared at 10%; the excipients are not declared) |
| **Confidence** | **98% — High** (`5 / (4×1.00 + 1/0.90) = 0.978`) |

### Marketing Penalty
0 marketing ingredients → no penalty.

**Final Output: Score 54, Confidence High**
