# Cosmetic Analysis Agent — Scoring Algorithm v1.0

## Overview

The scoring system translates structured analysis into a numeric score (0–100) with an accompanying confidence indicator. It operates in two modes:

| Mode | Trigger | Behavior |
| --- | --- | --- |
| **Standard** | Validation confidence ≥ 60% | Full numeric scoring |
| **Conservative** | Validation confidence < 60% | Qualitative assessment only, no numeric score |

---

## 1. Weight Profiles (from M19)

Each product category loads a distinct weight profile after recognition. All weights sum to 100%.

### 1.1 Default Profile (fallback)

| Dimension | Weight |
| --- | --- |
| Core Effectiveness | 40% |
| Formula Architecture | 25% |
| Support System | 10% |
| Safety | 15% |
| Skin Adaptation | 10% |

### 1.2 Cleanser / Shampoo

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

| Interaction Type | IM |
| --- | --- |
| Synergy (confirmed) | 1.10 |
| Independent (default) | 1.00 |
| Antagonism (confirmed) | 0.85 |
| Conflict (safety concern) | 0.70 |

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
Confidence = min(
    Input_Quality,        // from M14 validation
    DB_Match_Rate,        // % of ingredients found in databases
    Mechanism_Certainty,  // 1.0 - (unknown_mechanisms / total_mechanisms)
    Interaction_Certainty // 1.0 if no interactions or all confirmed, 0.7 if unknowns exist
)
```

| Confidence Range | Label |
| --- | --- |
| ≥ 80% | High |
| 60–79% | Medium |
| < 60% | Low → switch to Conservative Mode |

### Conservative Mode Rules
- Do not output a numeric score
- Report: "Score: Insufficient data for reliable scoring"
- Use qualitative language only ("appears adequate", "may be insufficient")
- Explicitly list all data gaps
- Confidence label: "Low — Conservative Mode"

---

## 5. Marketing Penalty

Marketing ingredients (from M13 ontology: Botanical, Marketing, Fragrance, Colorant categories) do not contribute positive points to any dimension.

**Overuse penalty**: If more than 30% of listed ingredients fall into marketing categories:

```
Marketing_Penalty = (marketing_ratio - 0.30) × 15
```

Applied as a deduction from Final_Score, capped at −10 points.

---

## 6. Edge Cases

| Scenario | Handling |
| --- | --- |
| Product category unrecognized | Use Default Profile; flag in report |
| Empty ingredient list | Validation → Unknown → Conservative Mode |
| All ingredients are marketing | PS = 0 for all function dimensions; score ≤ 15 |
| 100% database match, all evidence A | Max confidence; still capped at presence reality |
| Conflicting interactions in same dimension | Report all, use worst-case IM |
| Ingredient appears in 2+ ontology categories | Primary category wins; flag ambiguity |

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
| Input Quality | 100% (complete, readable) |
| DB Match Rate | 100% (5/5 ingredients matched) |
| Mechanism Certainty | 100% |
| Interaction Certainty | 100% |
| **Confidence** | **100% — High** |

### Marketing Penalty
0 marketing ingredients → no penalty.

**Final Output: Score 54, Confidence High**
