# Confidence Engine & Fallback Specification v1.0

## Overview

This specification defines the exact formulas for M15 (Confidence Engine) and M20 (Fallback Engine), and the precise linkage between M14 (Data Validation), M15, and M20. Together, these three modules form the **uncertainty management system**.

---

## 1. Confidence Architecture

```
M14: Data Validation Engine
  ↓ produces
Validation_Status (Complete | Partial | Unreadable | Unknown)
  + Validation_Confidence (0.0–1.0)
  ↓ feeds into
M15: Confidence Engine
  ↓ produces
Confidence_Score (0–100%)
  + Confidence_Label (High | Medium | Low)
  ↓ triggers (if < threshold)
M20: Fallback Engine
  ↓ produces
Conservative Mode decisions
```

---

## 2. M15 Confidence Score — Aggregation Formula

Five factors contribute to the overall confidence. They are aggregated using a **floor-weighted harmonic mean** — this ensures that one very weak factor drags the overall confidence down (worst-case-aware), rather than being hidden by strong factors in an arithmetic mean.

### 2.1 Factor Definitions

| Factor | Symbol | Source | Range | Description |
| --- | --- | --- | --- | --- |
| Input Quality | `I` | M14 validation_confidence | 0.0–1.0 | OCR readability + completeness + INCI pattern match |
| Database Match Rate | `D` | % of ingredients found in ≥1 database | 0.0–1.0 | How many parsed INCI names have database entries |
| Mechanism Certainty | `M` | % of active ingredients with known mechanism | 0.0–1.0 | Mechanisms documented with evidence ≥ Level D |
| Interaction Certainty | `X` | % of ingredient pairs with known interaction status | 0.0–1.0 | Pairs that have entries in interaction rules database |
| Concentration Certainty | `C` | % of ingredients with known or inferable concentration | 0.0–1.0 | Explicit declarations OR position-based inference |

### 2.2 Formula

```
Confidence = 5 / (1/I + 1/D + 1/M + 1/X + 1/C)

If any factor = 0, that term is dropped and the divisor reduces accordingly:

Confidence = N / Σ(1/factor_i)   where N = count of non-zero factors
```

### 2.3 Rationale

The harmonic mean is used because:
- It is always ≤ the minimum factor (floor-weighted)
- A single zero factor does not zero the whole score (term dropped)
- It penalizes imbalance — two factors at 0.9 + one at 0.3 gives ~0.56, not (0.9+0.9+0.3)/3 = 0.70
- This matches the design intent: "the chain is only as strong as its weakest link"

### 2.4 Example Calculations

| I | D | M | X | C | Arithmetic Mean | Harmonic Mean | Label |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1.0 | 1.0 | 1.0 | 1.0 | 1.0 | 1.00 | **1.00** | High |
| 0.95 | 0.80 | 0.85 | 0.90 | 0.90 | 0.88 | **0.88** | High |
| 0.80 | 0.70 | 0.70 | 0.80 | 0.60 | 0.72 | **0.71** | Medium |
| 0.60 | 0.50 | 0.50 | 0.50 | 0.50 | 0.52 | **0.52** | Medium |
| 0.50 | 0.30 | 0.40 | 0.60 | 0.30 | 0.42 | **0.38** | Low |
| 0.30 | 0.20 | 0.30 | 0.40 | 0.20 | 0.28 | **0.26** | Low |
| 0.80 | 0.85 | 0.10 | 0.90 | 0.80 | 0.69 | **0.30** | Low |
| 0.20 | 0.10 | 0.10 | 0.10 | 0.10 | 0.12 | **0.12** | Low |

Note row 7: even though 4/5 factors are high, a single very low factor (M=0.10) pulls confidence to **Low** — this is the intended behavior.

---

## 3. Confidence Labels & Thresholds

| Confidence Score | Label | Visual Indicator | Description |
| --- | --- | --- | --- |
| ≥ 80% | **High** | 🟢 | Reliable analysis; conclusions well-supported |
| 60–79% | **Medium** | 🟡 | Usable analysis; some gaps; interpret with caution |
| 40–59% | **Low** | 🟠 | Significant gaps; qualitative only; specific caveats |
| < 40% | **Critical** | 🔴 | Conservative mode mandatory; no numeric score |

### 3.1 Label → Behavior Mapping

| Label | Numeric Score? | Evidence Requirements | Report Wording |
| --- | --- | --- | --- |
| High | Yes | All factors ≥ 0.60 | Definitive language ("is", "has", "contains") |
| Medium | Yes | At least 3 factors ≥ 0.60 | Measured language ("appears to", "likely", "indicates") |
| Low | No | None (qualitative only) | Hedged language ("may", "suggests", "possibly") |
| Critical | No | Insufficient data | "Insufficient data for reliable analysis" |

---

## 4. Factor Computation Details

### 4.1 Input Quality (I)

Directly from M14 validation_confidence (§5.2 of input-parsing-spec.md):

```
I = validation_confidence / 100
```

### 4.2 Database Match Rate (D)

```
D = count(ingredients matched in ≥1 database) / count(total ingredients)

"Matched" means: INCI name found in at least one database with ontology classification.
```

Edge cases:
- Ingredients in Marketing [M] or Botanical [B] categories that have no database entry → count as unmatched
- Ingredients with partial match (same chemical family) → count as 0.5 match
- Water (Aqua) → always counted as matched (Solvent database)

### 4.3 Mechanism Certainty (M)

```
For each Core Active [A] ingredient:
  mechanism_score = 1.0 if evidence ≥ D  (has known mechanism)
                  = 0.5 if evidence = E   (marketing claim only)
                  = 0.0 if no evidence entry

M = Σ(mechanism_score_i) / count(Core Active ingredients)

If there are zero Core Active ingredients, M = 0.5 (cannot assess mechanism for non-actives; neutral)
```

### 4.4 Interaction Certainty (X)

```
For each pair of [A] + [A], [A] + [R], [A] + [FS] ingredients:
  pair_known = 1.0 if interaction rule exists in database
             = 0.5 if same chemical family (inferable)
             = 0.0 if no rule exists

X = Σ(pair_known) / count(relevant_pairs)

If there are ≤1 active ingredients, X = 1.0 (no interactions to assess; trivially certain)
```

### 4.5 Concentration Certainty (C)

```
For each ingredient:
  conc_known = 1.0 if explicit percentage declared (e.g., "Niacinamide 10%")
             = 0.8 if position ≤ 5 (≥1% typical; high confidence)
             = 0.5 if position 6–10 (likely >0.1%)
             = 0.3 if position > 10 (likely <0.1%)
             = 0.0 if position unknown (list order lost)

C = Σ(conc_known) / count(ingredients)
```

---

## 5. M20 Fallback Engine — Exact Rules

### 5.1 Fallback Triggers

| Trigger | Condition | Action |
| --- | --- | --- |
| **T1: Critical Confidence** | Confidence < 40% | Conservative mode: no numeric score |
| **T2: Low Database Coverage** | D < 0.30 | Flag "limited database coverage"; downgrade evidence claims |
| **T3: Unknown Ingredient** | Any single ingredient has no ontology match | Return "Unknown [INCI]" for that ingredient; do not infer function |
| **T4: Missing Concentration** | C < 0.50 | Use qualitative reasoning only; mark all concentration-dependent claims as "tentative" |
| **T5: Unsupported Interaction** | X < 0.50 | Flag "interaction uncertainty"; do not assert synergy/antagonism |
| **T6: OCR Failure** | I < 0.40 | Request clearer image; do not proceed |
| **T7: Truncated List** | Completeness < 0.50 | Flag "incomplete ingredient list"; all conclusions are partial |

### 5.2 Conservative Mode — Detailed Behavior

When Conservative Mode is active (Confidence < 40% OR any T3/T6/T7 trigger):

```
1. DO NOT output a numeric score.
   → Replace with: "Score: Insufficient data (Confidence: X%)"

2. DO NOT assert efficacy.
   → Replace definitive claims with:
     "Cannot determine whether [product] effectively [objective] due to [specific gap]"

3. DO identify what IS known:
   → "The following ingredients were identified: [list with ontology where possible]"
   → "The following could not be identified: [list of unknowns]"

4. DO list all data gaps explicitly:
   → "Missing: concentration data for 12/20 ingredients"
   → "Missing: mechanism evidence for ingredient X"
   → "Missing: interaction data for pair (A, B)"

5. DO provide a partial qualitative assessment:
   → "Based on available data, the product appears to be a [category]."
   → "The preservative system is [adequate/inadequate/cannot determine]."
   → "Risk assessment is [partial/cannot determine] due to [reason]."

6. DO suggest remediation:
   → "For a reliable analysis: [better image / complete ingredient list / etc.]"
```

### 5.3 Partial Fallback (Medium Confidence)

When Confidence is 60–79% (Medium):

```
1. Output numeric score BUT append confidence caveat.
2. Use hedged language throughout.
3. Flag each conclusion with its individual certainty.
4. Example: "Overall Score: 62 (Medium Confidence — see caveats below)"
```

---

## 6. Per-Factor Confidence Reporting

Each dimension in the M22 report should carry its own confidence sub-score:

### 6.1 Dimension Confidence

| Dimension | Confidence Factors Used | Formula |
| --- | --- | --- |
| Core Effectiveness | D(core_actives), M, C | min(D_core, M, C) |
| Formula Architecture | D(architecture), C | min(D_arch, C) |
| Support System | D(support), C | min(D_sup, C) |
| Safety | D(risk_ingredients) | D_risk |
| Skin Adaptation | D(all), C | min(D_all, C) |
| Interaction Analysis | X | X |
| Evidence Level | M | M |

### 6.2 Report Representation

```
Overall Confidence: 78% (Medium)
  ├─ Core Effectiveness:  85% 🟢 (mechanisms well-documented; concentration estimated)
  ├─ Formula Architecture: 72% 🟡 (emulsifier system identified; some stabilizers unknown)
  ├─ Support System:       80% 🟢 (humectants and antioxidants matched)
  ├─ Safety:               90% 🟢 (risk database coverage high; no flagged conflicts)
  ├─ Skin Adaptation:      65% 🟡 (some ingredients lack skin-type compatibility data)
  └─ Interaction:          75% 🟡 (2/8 active pairs have known interactions)
```

---

## 7. Confidence Decay Over Pipeline Steps

As the M18 pipeline progresses, uncertainty compounds. If a module is skipped (M18 dynamic skip rule), the downstream confidence factors must be adjusted:

| Skipped Module | Affected Factor | Adjustment |
| --- | --- | --- |
| Validation | I | Set to 0.20 (minimal) |
| Ontology Mapping | D | Set to 0 (no classification) |
| Database Query | D, M | Both set to 0 |
| Interaction Analysis | X | Set to 0.50 (neutral uncertainty) |
| Mechanism Analysis | M | Set to 0.30 (guesswork) |
| Architecture Analysis | — | No direct factor; reduce Architecture dimension weight to 0 |
| Risk Analysis | — | Flag "risk assessment skipped" in report |
| Skin Adaptation | — | Flag "compatibility not assessed" in report |

### 7.1 Skip Recording

Every skipped module MUST be recorded in the output:

```json
{
  "skipped_modules": [
    {
      "module": "Interaction Analysis",
      "reason": "Single active ingredient; no interactions to analyze",
      "confidence_impact": "X set to 1.0 (trivial certainty)"
    },
    {
      "module": "Skin Adaptation",
      "reason": "Insufficient skin-type compatibility data in database",
      "confidence_impact": "Skin Adaptation dimension scored at default 0.50"
    }
  ]
}
```

---

## 8. Summary Matrix

| Confidence | Score? | Language | Conservative? | Skip Allowed? |
| --- | --- | --- | --- | --- |
| ≥ 80% High | Yes | Definitive | No | Only trivial modules |
| 60–79% Medium | Yes | Hedged | No (partial caveats) | Non-critical modules |
| 40–59% Low | No | Qualitative + caveats | Partial | Any unavailable module |
| < 40% Critical | No | Gap report only | Full | All unavailable; core must run |
