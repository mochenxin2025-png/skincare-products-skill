# Acne Serum Specification v1.0

Supplement to the main framework. Covers anti-acne serums and acne treatments. Load this when the product category is identified as **"Anti-Acne Serum"**.

---

## 1. First Principle

**First principle:** reduce acne lesions through multiple complementary pathways. Acne vulgaris is a multifactorial condition, so a single-mechanism product is rarely sufficient — the question this specification answers is *how many of the four pathways a formula covers, with actives at effective concentrations, and at what evidence level*.


Acne vulgaris is a multifactorial condition involving four primary pathogenic pathways:
1. **Follicular hyperkeratinization** — abnormal desquamation of follicular keratinocytes
2. **Increased sebum production** — androgen-driven sebaceous gland activity
3. **Cutibacterium acnes colonization** — microbial trigger of inflammation
4. **Inflammation** — both innate and adaptive immune responses

An effective anti-acne serum must address ≥2 of these pathways. Single-mechanism products are rarely sufficient for clinical acne.

---

## 2. Anti-Acne Ingredient Hierarchy

### Tier 1 — First-Line, Multi-Pathway (Evidence A/B)

| Ingredient | Pathways | Evidence | Typical Conc. | Notes |
| --- | --- | --- | --- | --- |
| Benzoyl Peroxide (BPO) | Antibacterial, Keratolytic | A | 2.5–10% | 2.5% as effective as 10% with less irritation. No bacterial resistance. Bleaches fabric. |
| Adapalene | Keratinocyte turnover, Anti-inflammatory | A | 0.1–0.3% | OTC 0.1%. Better tolerated than tretinoin. Gold standard retinoid for acne. |
| Azelaic Acid | Antibacterial, Anti-inflammatory, Keratolytic, Tyrosinase inhibitor | B | 10–20% | Excellent for acne + PIH. Well-tolerated. Limited irritation. |
| Salicylic Acid | Keratolytic (lipophilic), Anti-inflammatory | B | 0.5–2% | Penetrates pores. 2% OTC standard. Betaine Salicylate is gentler alternative. |

### Tier 2 — Adjunctive (Evidence B/C)

| Ingredient | Pathways | Evidence | Conc. | Notes |
| --- | --- | --- | --- | --- |
| Niacinamide | Sebum regulation, Anti-inflammatory, Barrier repair | B | 2–5% | Reduces sebum at 2% after 4 weeks. Above 5% → irritation without benefit for acne. |
| Retinol / Retinal | Keratinocyte turnover | B | 0.1–1% | Weaker than adapalene for acne. Better for anti-aging + mild acne. |
| Zinc PCA / Zinc Gluconate / Zinc Lactate | Sebum regulation, Anti-inflammatory | B | 0.5–2% | Zinc ions inhibit 5α-reductase. More effective in combination (Zn + niacinamide synergy IM 1.05). Zinc Lactate is common in SeboPlex-type proprietary complexes. |
| Sulfur | Keratolytic, Antibacterial | C | 2–10% | Old-school. Unpleasant odor. Better in spot treatments. |

### Tier 3 — Supporting (Evidence C/D)

| Ingredient | Pathways | Evidence | Notes |
| --- | --- | --- | --- |
| Tea Tree Oil | Antibacterial, Anti-inflammatory | C | Weak compared to BPO. Irritant at >5%. Not first-line. |
| Green Tea Extract (EGCG) | Anti-inflammatory, Antioxidant | C | Topical EGCG reduces acne lesions in some studies. Concentration-dependent. |
| Lactic Acid (≤10%) | Keratolytic, Barrier repair | B (as exfoliant) | Gentle AHA. Better for comedonal acne. |
| Willow Bark Extract | Keratolytic | D | Much weaker than isolated salicylic acid. [M] unless standardized. |
| Aloe Vera | Anti-inflammatory | C | Soothes irritation from other actives. Not an active treatment alone. |

---

## 3. Comedogenicity Evaluation Protocol

### Step 1: Flag all ingredients with known comedogenicity score

| Score | Meaning | Common Examples |
| --- | --- | --- |
| 0 | Non-comedogenic | Squalane, Caprylic/Capric Triglyceride, Glycerin, Dimethicone, C12-15 Alkyl Benzoate |
| 1–2 | Low | Shea Butter, Jojoba Oil, Argan Oil, Cetearyl Alcohol |
| 3–4 | Moderate to High | Coconut Oil, Isopropyl Myristate (IPM), Isopropyl Palmitate (IPP), Cocoa Butter |
| 5 | Very High | Highly comedogenic — avoid in acne-prone |

### Step 2: Position-weighted assessment

- **Score ≥3 AND in top 10 ingredients** → apply Safety dimension penalty: −0.10 per ingredient, max −0.30
- **Score ≥3 after position 10** → note but no penalty (lower concentration)
- **Multiple score ≥3 ingredients** → cumulative: 2 = −0.15, 3+ = −0.25
- **Coconut Oil in any position for face products** → flag as acne-unfriendly regardless of position

### Step 3: Texture profile assessment

| Descriptor | Acne-Friendly? | Notes |
| --- | --- | --- |
| Light, gel-like | ✅ | Water-based, humectant-dominant preferred |
| Oil-in-water emulsion | ✅ | If lightweight emulsifiers used |
| Water-in-oil emulsion | ⚠️ | Occlusive; may trap sebum |
| Heavy cream, balm | ❌ | Too occlusive for acne-prone skin; flag |

### Step 4: Auxiliary ingredient scans

| Ingredient | Concern | Action |
| --- | --- | --- |
| Lanolin | Comedogenic (3–4) | Flag in leave-on products, esp. face |
| D&C Red pigments | Comedogenic (certain lakes) | Flag at >3 items in ingredient list |
| Acetylated Lanolin | Comedogenic (4) | Flag |
| Myristyl Myristate | Comedogenic (2–3) | Flag if high position |

---

## 4. Multi-Pathway Analysis Rules

### Rule 1: Pathway Coverage Scoring

Rate the serum on how many of the 4 primary acne pathways it addresses:

| Pathways Covered | Score |
| --- | --- |
| 0–1 | Poor — single-target product, likely insufficient for clinical acne |
| 2 | Adequate — covers basics (e.g., keratolytic + antibacterial) |
| 3 | Good — broad coverage (e.g., BPO + retinoid + anti-inflammatory) |
| 4 | Excellent — comprehensive (rare in single product; usually regimen) |

### Rule 2: The BPO-Retinoid Separation Rule

BPO + retinoid (adapalene, retinol, retinal, tretinoin) in the **same bottle** → **Conflict (IM 0.70)**. BPO oxidizes retinoids.

If the product claims "BPO + retinoid acne treatment" and both are in the ingredient list:
- Check whether BPO is in a separate compartment (e.g., dual-chamber pump, separate pod)
- If co-formulated in a single phase → flag as **formulation error**; reduced Architecture PS (−0.20)
- If separated (dual-chamber) → acceptable; note in report

### Rule 3: Acid Overload Detection

If ≥3 of the following are present, flag potential irritation overload:

- Salicylic Acid ≥ 1%
- Glycolic Acid ≥ 5%
- Lactic Acid ≥ 5%
- Mandelic Acid ≥ 5%
- Benzoyl Peroxide ≥ 5%
- Retinol ≥ 0.3% / Retinal ≥ 0.05%
- Ascorbic Acid ≥ 10%

→ Reduce Safety PS by −0.15. Flag as "High irritation potential — caution for sensitive acne-prone skin"

### Rule 4: Barrier Support Detection

Acne treatment is inherently barrier-disrupting. The presence of barrier-support ingredients compensates:

| Ingredient | Bonus |
| --- | --- |
| Panthenol | +0.03 Safety PS |
| Niacinamide (≥2%) | +0.05 Safety PS (multi-functional) |
| Ceramides (any) | +0.03 Safety PS |
| Allantoin | +0.02 Safety PS |
| Madecassoside / Centella | +0.03 Safety PS |
| Squalane (≤3%) | +0.02 Safety PS (non-comedogenic) |
| Bisabolol | +0.02 Safety PS |

Max bonus: +0.15 Safety PS

**If no barrier support ingredients present** → note "No barrier support — prolonged use may compromise skin barrier"

### Rule 5: PIH Score Adjustment

Post-inflammatory hyperpigmentation (PIH) is a major concern in acne-prone skin, especially Fitzpatrick III–VI.

If the product treats **both** acne and PIH:
- Azelaic Acid ≥ 10% → +0.10 Core Effectiveness (dual benefit)
- Niacinamide ≥ 4% + Tranexamic Acid ≥ 2% → +0.08 Core Effectiveness
- Alpha-Arbutin / Kojic Acid in an acne serum → note but don't score (not acne mechanism)
- Retinoid + Azelaic Acid → +0.05 IM synergy (complementary pathways for acne + PIH)

---

## 5. Special Ingredient Assessments

### Benzoyl Peroxide

| Concern | Rule |
| --- | --- |
| Concentration | 2.5% = 5% = 10% efficacy (same clinical effect); 2.5% least irritating |
| Form | Gel > cream > wash (leave-on for acne; wash too short contact) |
| Pilling | Known to pill under sunscreen → note as formulation consideration |
| Bleaching | Warn: bleaches towels, clothing, bedding |

### Salicylic Acid

| Aspect | Rule |
| --- | --- |
| Optimal pH | 3.0–4.0 for free acid activity |
| Betaine Salicylate | Gentler, same BHA class, works at pH 4.5–5.5 → fewer pH conflicts |
| Wash-off | ≤2% in leave-on products in EU/US. Higher allowed but unnecessary. |

### Adapalene

| Aspect | Rule |
| --- | --- |
| OTC | 0.1% gel available without Rx in US since 2016 |
| Irritation | Peaks at week 2–4, resolves by week 12. Warn in report. |
| Combination | Adapalene + BPO (separate steps) → gold standard first-line therapy (Evidence A) |
| Pregnancy | Category C; do not recommend without medical consultation |

---

## 6. Acne Severity-Product Matching

| Acne Severity | Suitable Product Type | Not Suitable |
| --- | --- | --- |
| Mild comedonal (blackheads/whiteheads) | Salicylic acid serum, AHA toner, adapalene | Heavy occlusives, physical scrubs |
| Mild inflammatory (few papules/pustules) | BPO 2.5%, azelaic acid, niacinamide | High-concentration AHA |
| Moderate (papules + pustules, 10–50 lesions) | Adapalene + BPO (separate), azelaic acid | Single-ingredient products |
| Severe (nodules, cysts, scarring risk) | ❌ OTC insufficient → refer to dermatologist | Any OTC-only approach |

---

## 7. Anti-Acne Serum Weight Profile

| Dimension | Weight | Rationale |
| --- | --- | --- |
| Core Effectiveness | 35 | Pathway coverage — how many of the four pathogenic pathways the formula addresses, with actives at effective concentrations |
| Safety | 25 | The target skin is already inflamed and often barrier-damaged, so irritancy and barrier load weigh more than in a healthy-skin product |
| Architecture | 15 | The vehicle must carry lipophilic actives (BPO, retinoids) without destabilising them, and respect acid pH constraints |
| Support System | 15 | Barrier support (panthenol, allantoin, madecassoside, dipotassium glycyrrhizate) is clinically meaningful here — acne treatment damages the barrier it depends on |
| Skin Adaptation | 10 | Acne-prone, oily and combination skin are the primary targets; sensitivity and barrier damage are relative contraindications for parts of the arsenal |

**Multi-target requirement:** a single-mechanism product cannot exceed the 0.5–0.69 band on Core Effectiveness (SKILL.md Step 8, Domain Quick Rules → Anti-Acne Serum).

---

## 8. Anti-Hallucination Rules (Acne-Specific)

- **"Detox" or "Pore-tightening"** are marketing constructs, not mechanisms → flag as unsupported
- **"Oil-free"** does not mean non-comedogenic (many synthetic esters are oil-free but highly comedogenic)
- **"Sulfate-free"** in an acne serum is irrelevant — sulfates are cleanser ingredients; flag the marketing claim
- **"Natural acne treatment"** with only botanicals and no active drugs → insufficient for anything beyond very mild acne
- **Brewer's yeast, probiotics in topical form** for acne → insufficient topical evidence (oral probiotics are separate)
- **LED light therapy claim** in a serum ingredient list → impossible (serums don't emit light); flag as unsupported
- **Drying alcohols** (Alcohol Denat., SD Alcohol) in an acne serum → barrier-disrupting on already-inflamed skin → Safety PS −0.10
- **Phototoxic botanicals** (Hypericum Perforatum / St. John's Wort / 贯叶连翘) in an acne serum → contains hypericin, activated by UVA/visible light → causes phototoxic burns on acne-inflamed skin AND worsens post-inflammatory hyperpigmentation (PIH). If found in leave-on product → Safety PS −0.20 regardless of position. Flag with: "🚨 Contains phototoxin — must not be used without rigorous sun protection. Contributes to PIH, the exact opposite of what an acne serum should do." Use same severity as BPO-Retinoid conflict.
- **Proprietary complex traps** (SeboPlex, etc.) — active ingredients hidden inside trademarked complexes (e.g., Zinc Lactate inside SeboPlex) → concentration unverifiable. Do NOT assume therapeutic concentration. Note: "Active [X] is part of [Complex Y]; actual concentration unknown → efficacy uncertain." Reduce mechanism certainty for that active.

---

## 9. Sources

| Claim | Source |
| --- | --- |
| Four-pathway pathogenesis; multi-pathway treatment requirement; azelaic acid, topical retinoids, benzoyl peroxide and salicylic acid as established acne treatments | Zaenglein AL, et al. *Guidelines of care for the management of acne vulgaris*. J Am Acad Dermatol 2016;74(5):945-973.e33. DOI `10.1016/j.jaad.2015.12.037` (Evidence A) |
| Adapalene 0.1% gel is available over the counter — the first retinoid switched from prescription to OTC for acne | US FDA, sNDA 020380/S-010, adapalene gel 0.1% Rx-to-OTC switch, approved 2016-07-15 |
| Salicylic acid 0.5–2.0% acne range; China ≤ 2.0% leave-on / ≤ 3.0% rinse-off hair / ≤ 0.5% as a preservative, not for under-3s | 《化妆品安全技术规范》(2015 年版); EU Regulation (EC) 1223/2009 Annex III No. 98 — full table in `exfoliation-spec.md` §4 |
| Salicylic acid (BHA) clinical entries | `evidence-citation-spec.md` BHA-01, BHA-02, BHA-03 |
| Niacinamide 2–5% sebum regulation and anti-inflammatory use | `evidence-citation-spec.md` NIA-01 … NIA-05 |
| Retinoid efficacy, irritation and adaptation | `evidence-citation-spec.md` RET-01 … RET-05 |
| AHA / PHA adjunct exfoliation evidence | `evidence-citation-spec.md` AHA-01 … AHA-05, PHA-02 |
| BPO + retinoid must be split across application steps | `interaction-rules.md` **Rule 7** (Retinol + Benzoyl Peroxide) |
| Acid overload and stacking | `interaction-rules.md` **Rule 9** (Glycolic + Salicylic), **Rule 11** (AHA + PHA), **Rule 6** (Retinol + AHA) |
| Salicylic acid + niacinamide pH interaction | `interaction-rules.md` **Rule 10** |
| Azelaic acid / zinc combined with niacinamide | `interaction-rules.md` **Rule 16**, **Rule 17** |

> Where a claim has no pinned citation above, it rests on the framework's evidence grading (SKILL.md Step 7) and must be reported at that level — never upgraded.
