# Output Format Specification v1.0

## Overview

This specification defines the exact output format for cosmetic analysis reports. Two modes are supported:

| Mode | Target | Use Case |
| --- | --- | --- |
| **Markdown Report** | Human reading | Consumer app, social sharing, dermatologist consultation |
| **JSON API** | Machine consumption | App integration, batch analysis, database storage |

Both modes cover all 14 items from M22 Report Standardization.

---

## 1. Markdown Report Format

### 1.1 Full Template

```markdown
# Cosmetic Analysis Report

**Product Type**: [Cleanser / Moisturizer / Serum / Sunscreen / Shampoo / Other]
**Analysis Date**: [YYYY-MM-DD]
**Confidence**: [🟢 High (XX%) / 🟡 Medium (XX%) / 🟠 Low (XX%) / 🔴 Critical (XX%)]
**Mode**: [Standard / Conservative]

---

## ① First Principle

The biological objective of a **[product category]** is:

> [First principle statement from L1]

---

## ② Product Objective Assessment

Based on the ingredient list, this product aims to:

- [Derived objective 1]
- [Derived objective 2]

*Alignment with first principle*: [Strong / Moderate / Weak] — [Brief explanation]

---

## ③ Ontology Summary

| Category | Count | Key Ingredients |
| --- | --- | --- |
| Core Active | N | [comma-separated] |
| Formula Support | N | [comma-separated] |
| Skin Conditioning | N | [comma-separated] |
| Texture Modifier | N | [comma-separated] |
| Preservative | N | [comma-separated] |
| Solvent | N | [comma-separated] |
| Chelator | N | [comma-separated] |
| Emulsifier | N | [comma-separated] |
| Stabilizer | N | [comma-separated] |
| Film Former | N | [comma-separated] |
| Colorant | N | [comma-separated] |
| Fragrance | N | [comma-separated] |
| Botanical | N | [comma-separated] |
| Marketing | N | [comma-separated] |
| Risk | N | [comma-separated] |

---

## ④ Core Active Ingredients

| # | INCI | Common Name | Mechanism | Evidence | Concentration |
| --- | --- | --- | --- | --- | --- |
| 1 | Niacinamide | Vitamin B3 | Melanosome transfer inhibitor; barrier lipid synthesis | B — Clinical Trial | ~10% (declared) |

**Assessment**: [2–3 sentences evaluating active ingredient quality and supporting evidence]

---

## ⑤ Formula Architecture

**Carrier System**: [e.g., Oil-in-Water emulsion / Anhydrous solution / Gel / Suspension]

**Key Structural Components**:

| Component | Ingredients | Assessment |
| --- | --- | --- |
| Emulsifier | [list] | [adequate / suboptimal / unable to determine] |
| Stabilizer | [list] | [adequate / — / unable to determine] |
| Thickener | [list] | [adequate / —] |
| Film Former | [list] | [adequate / —] |
| Oil Phase | [list] | [adequate / —] |
| Water Phase | [list] | [adequate / —] |

**Architecture Assessment**: [Does the architecture support the active delivery? Are there incompatibilities?]

---

## ⑥ Support System

| # | INCI | Role | Contribution |
| --- | --- | --- | --- |
| 1 | Butylene Glycol | Humectant | Improves skin hydration; supports active penetration |
| 2 | Tocopherol | Antioxidant | Protects formula from oxidation; mild skin antioxidant |

**Assessment**: [Is the support system adequate? What's missing?]

---

## ⑦ Marketing Ingredients

| # | INCI | Category | Functional Contribution |
| --- | --- | --- | --- |
| 1 | [Ingredient] | Botanical / Marketing / Fragrance / Colorant | Negligible / Limited / None |

**Overuse Assessment**: [X% of ingredients are marketing-category → no penalty / minor concern / overuse penalty applied]

---

## ⑧ Risk Ingredients

| # | INCI | Risk Type | Severity | Impact |
| --- | --- | --- | --- | --- |
| 1 | [Ingredient] | Irritant / Sensitizer / Endocrine / Phototoxic | High / Medium / Low | [Consequence for skin] |

**Identified Interactions**:

| Pair | Type | Effect | IM |
| --- | --- | --- | --- |
| [A] + [B] | Synergy / Antagonism / Conflict | [Description] | [0.XX] |

---

## ⑨ Skin Adaptation

| Skin Type | Suitability | Notes |
| --- | --- | --- |
| Normal | ✅ Suitable / ⚠️ Caution / ❌ Not Recommended | [Reason] |
| Dry | ✅ / ⚠️ / ❌ | [Reason] |
| Oily | ✅ / ⚠️ / ❌ | [Reason] |
| Combination | ✅ / ⚠️ / ❌ | [Reason] |
| Sensitive | ✅ / ⚠️ / ❌ | [Reason] |
| Acne-Prone | ✅ / ⚠️ / ❌ | [Reason] |
| Rosacea | ✅ / ⚠️ / ❌ | [Reason] |
| Seb Derm | ✅ / ⚠️ / ❌ | [Reason] |
| Barrier-Damaged | ✅ / ⚠️ / ❌ | [Reason] |
| Infant | ✅ / ⚠️ / ❌ | [Reason] |

---

## ⑩ Interaction Analysis

| # | Pair | Type | Mechanism | Evidence | Dimension Affected | IM |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | [A] + [B] | Synergy | [Mechanism] | [Level] | Core Effectiveness | 1.10 |

*No known interactions* (if none found).

---

## ⑪ Evidence Level

| Claim | Evidence Level | Source Quality |
| --- | --- | --- |
| [Ingredient X] effectively [mechanism] | B — Clinical Trial | [Reference] |
| [Ingredient Y] provides [function] | D — Expert Opinion | Textbook (no specific study cited) |
| [Marketing claim about Z] | E — Marketing Claim | No scientific evidence found |

**Overall Evidence Quality**: [Strong / Moderate / Weak] — [Summary statement]

---

## ⑫ Confidence

**Overall**: 🟡 Medium — 72%

| Factor | Score | Status |
| --- | --- | --- |
| Input Quality | 95% | 🟢 Complete OCR, full ingredient list |
| Database Match Rate | 80% | 🟢 16/20 ingredients matched |
| Mechanism Certainty | 60% | 🟡 2/4 active ingredients have known mechanisms |
| Interaction Certainty | 70% | 🟡 3/6 active pairs have known interaction status |
| Concentration Certainty | 55% | 🟠 Only 1 ingredient has declared concentration |

---

## ⑬ Overall Score

**Score**: **62 / 100** (Medium Confidence)

| Dimension | Weight | Raw Score | Contribution |
| --- | --- | --- | --- |
| Core Effectiveness | 35% | 0.72 | 25.2 |
| Architecture | 20% | 0.60 | 12.0 |
| Safety | 20% | 0.80 | 16.0 |
| Support System | 15% | 0.55 | 8.3 |
| Skin Adaptation | 10% | 0.65 | 6.5 |
| **Total** | **100%** | | **62.0** |

*Marketing Penalty*: −0.0 (X% marketing ingredients, no penalty)

---

## ⑭ Final Conclusion

**Strengths**:
- [Bullet 1]
- [Bullet 2]

**Limitations**:
- [Bullet 1]
- [Bullet 2]

**Recommendation**:

[2–4 sentence summary. For [skin type]: this product is [recommended / acceptable with caution / not recommended]. Key reason: ...]

---

*This analysis was generated by Cosmetic Analysis Agent Framework v2.0. Evidence levels follow the A–E classification. Confidence indicates data completeness, not product quality. Always consult a dermatologist for medical advice.*
```

### 1.2 Conservative Mode Variant

When Conservative Mode is active, sections ⑬ (Score) and parts of ④–⑨ are replaced:

```markdown
## ⑬ Overall Score

**Score**: Insufficient data for reliable scoring

⚠️ **Conservative Mode Active** — Confidence: 🔴 28%

**Data Gaps**:
- Missing: concentration data for 18/20 ingredients
- Missing: mechanism evidence for 3/4 actives
- Missing: complete interaction analysis (database incomplete)
- Input quality: Partial (OCR 62% confidence)

**For a reliable analysis**: Please provide a clearer image of the full ingredient list.

---

## ⑭ Partial Assessment (Conservative)

Based on the limited available data:

- This appears to be a **[category]** product.
- Identified active: **[ingredient]** — function uncertain without concentration data.
- [List anything that CAN be said confidently.]
- **Caution**: All conclusions below standard reliability threshold. Do not base purchase decisions on this analysis.
```

---

## 2. JSON API Format

### 2.1 Schema

```json
{
  "$schema": "https://cosmetic-analysis-agent/schema/v1/report",
  "report": {
    "meta": {
      "version": "2.0.0",
      "timestamp": "2025-01-15T10:30:00Z",
      "product_category": "serum",
      "confidence": {
        "score": 0.72,
        "label": "medium",
        "mode": "standard"
      }
    },
    "first_principle": {
      "category": "serum",
      "objective": "Deliver active ingredients to the skin."
    },
    "ontology_summary": {
      "categories": [
        {
          "name": "Core Active",
          "count": 3,
          "ingredients": ["Niacinamide", "Ascorbic Acid", "Tocopherol"]
        }
      ]
    },
    "ingredients": [
      {
        "position": 1,
        "inci": "Aqua",
        "common_name": "Water",
        "ontology": "Solvent",
        "mechanism": "Carrier solvent",
        "evidence_level": null,
        "concentration": {
          "known": false,
          "estimated_range": ">50%",
          "method": "position_inferred"
        },
        "risk": null
      }
    ],
    "architecture": {
      "carrier_system": "Oil-in-Water emulsion",
      "ph_range": null,
      "components": {
        "emulsifiers": ["Glyceryl Stearate", "PEG-100 Stearate"],
        "stabilizers": ["Carbomer"],
        "thickeners": ["Xanthan Gum"],
        "film_former": [],
        "oil_phase": ["Caprylic/Capric Triglyceride"],
        "water_phase": ["Aqua", "Butylene Glycol"]
      },
      "assessment": "Standard O/W emulsion architecture. Adequate for water-soluble actives; lipophilic actives may have limited delivery.",
      "architecture_score": 0.60
    },
    "support_system": {
      "ingredients": [
        {
          "inci": "Butylene Glycol",
          "role": "Humectant",
          "contribution": "Improves skin hydration"
        }
      ],
      "assessment": "Adequate basic support. Missing: antioxidant protection for formula stability."
    },
    "marketing": {
      "ingredients": [
        {
          "inci": "Lactobacillus Ferment",
          "category": "Marketing",
          "contribution": "Negligible"
        }
      ],
      "overuse_ratio": 0.15,
      "penalty_applied": false
    },
    "risks": {
      "ingredients": [
        {
          "inci": "Benzyl Alcohol",
          "risk_type": "Allergen",
          "severity": "Medium",
          "mechanism": "Type IV hypersensitivity; must be declared in EU",
          "impact": "May cause contact dermatitis in sensitized individuals"
        }
      ],
      "interactions": [
        {
          "pair": ["Ascorbic Acid", "Tocopherol"],
          "type": "Synergy",
          "mechanism": "Vitamin E quenches lipid radicals; Vitamin C regenerates oxidized Vitamin E",
          "evidence": "A",
          "dimension_affected": "core_effectiveness",
          "im": 1.10
        }
      ]
    },
    "skin_adaptation": {
      "compatibility": [
        {
          "skin_type": "normal",
          "suitability": "suitable",
          "notes": "No contraindications"
        },
        {
          "skin_type": "sensitive",
          "suitability": "caution",
          "notes": "Benzyl Alcohol may cause irritation in highly sensitive individuals"
        }
      ]
    },
    "interaction_analysis": {
      "total_pairs_evaluated": 4,
      "known_interactions": 1,
      "uncertain_pairs": 2,
      "details": []
    },
    "evidence": {
      "overall_quality": "Moderate",
      "claims": [
        {
          "claim": "Niacinamide reduces hyperpigmentation",
          "evidence_level": "B",
          "source": "Hakozaki et al., Br J Dermatol (2002)",
          "source_type": "clinical_trial"
        }
      ]
    },
    "confidence_detail": {
      "factors": {
        "input_quality": { "score": 0.95, "label": "high" },
        "database_match_rate": { "score": 0.80, "label": "high" },
        "mechanism_certainty": { "score": 0.60, "label": "medium" },
        "interaction_certainty": { "score": 0.70, "label": "medium" },
        "concentration_certainty": { "score": 0.55, "label": "medium" }
      }
    },
    "scoring": {
      "mode": "standard",
      "total": 62.0,
      "confidence_label": "Medium",
      "dimensions": [
        {
          "name": "Core Effectiveness",
          "weight": 0.35,
          "presence_score": 0.72,
          "evidence_multiplier": 0.90,
          "interaction_modifier": 1.10,
          "dimension_score": 0.713,
          "contribution": 24.9
        }
      ],
      "marketing_penalty": 0.0
    },
    "conclusion": {
      "strengths": [
        "Well-recognized active ingredient (Niacinamide) at declared 10% concentration"
      ],
      "limitations": [
        "Limited antioxidant support system"
      ],
      "recommendation": "Recommended for normal to oily skin seeking hyperpigmentation reduction. Caution for sensitive skin due to benzyl alcohol content.",
      "disclaimer": "Always consult a dermatologist for medical advice."
    }
  }
}
```

### 2.2 Conservative Mode JSON

```json
{
  "report": {
    "meta": {
      "mode": "conservative",
      "confidence": { "score": 0.28, "label": "critical" }
    },
    "scoring": {
      "mode": "conservative",
      "total": null,
      "reason": "Insufficient data — Confidence 28%"
    },
    "data_gaps": [
      "Missing: concentration data for 18/20 ingredients",
      "Input quality: Partial (OCR 62%)"
    ],
    "partial_assessment": "This appears to be a moisturizer. The preservative system (Phenoxyethanol + Ethylhexylglycerin) is adequate. Further analysis is not reliable due to missing data.",
    "remediation": "Please provide a clearer image of the full ingredient list."
  }
}
```

---

## 3. Field Reference

### 3.1 Suitability Enum

```
"suitable"     — No contraindications; recommended
"caution"      — Minor concerns; product may be used with awareness
"not_recommended" — Significant contraindication for this skin type
"unknown"      — Insufficient data to determine
```

### 3.2 Risk Severity Enum

```
"low"          — Minimal concern at cosmetic concentrations
"medium"       — Potential concern for sensitive populations
"high"         — Significant known risk; recommend avoidance
"prohibited"   — Banned in major regulatory regions
```

### 3.3 Evidence Level Enum (from M17)

```
"A" — Meta-analysis / Systematic Review
"B" — Clinical Trial (RCT, in vivo human)
"C" — In Vitro / Laboratory Study
"D" — Expert Opinion / Textbook
"E" — Marketing Claim / No Evidence
```

### 3.4 Interaction Type Enum (from M16)

```
"synergy"      — Combined effect > sum of individual effects
"antagonism"   — Combined effect < individual effects (no harm)
"conflict"     — Combined effect causes degradation or safety concern
"independent"  — No interaction detected or expected
```

---

## 4. Output Selection Logic

```
IF target is "api" OR "json":
  → Output JSON format (§2)
ELSE IF target is "markdown" OR "report" OR not specified:
  → Output Markdown format (§1)

IF confidence < 40%:
  → Use Conservative Mode variant (§1.2 or §2.2)

IF product_category unrecognized:
  → category = "other"
  → first_principle = generic ("Improve skin health/function")
```

---

## 5. Internationalization Hooks

All human-readable strings in the output template are candidates for i18n:

| Key | English | 中文 |
| --- | --- | --- |
| Product Type | Product Type | 产品类型 |
| Confidence | Confidence | 置信度 |
| Core Active | Core Active | 核心活性成分 |
| Suitable | Suitable | 适用 |
| Caution | Caution | 慎用 |
| Not Recommended | Not Recommended | 不推荐 |
| Strengths | Strengths | 优势 |
| Limitations | Limitations | 局限性 |
| Recommendation | Recommendation | 建议 |

Full i18n mappings are in a separate locale file (future).
