# Shampoo Specification v1.0

Enhanced shampoo analysis rules. Replaces the basic Shampoo entry in SKILL.md. Load when product is identified as "Shampoo", "Anti-Dandruff Shampoo", or "Scalp Treatment Shampoo".

---

## 1. First Principle (Revised)

Shampoo is a **rinse-off cleanser**, not a treatment product. Contact time is generally 1–3 minutes.

Medical objectives:
1. Remove excess sebum, sweat, and environmental contaminants
2. Reduce microbial metabolites
3. Maintain scalp barrier integrity while cleaning

Any ingredient requiring prolonged penetration should be assigned low confidence unless supported by strong clinical evidence.

---

## 2. Seborrheic Dermatitis Pathogenesis

When analyzing anti-dandruff shampoos, evaluate against this pathogenic chain:

```
Sebum ↑
   ↓
Malassezia overgrowth
   ↓
Free fatty acid production (lipase activity)
   ↓
Inflammatory response
   ↓
Scaling + Itching + Erythema

Barrier disruption → further aggravates inflammation
```

**Intervention priority**:
```
Anti-fungal > Anti-inflammatory > Barrier maintenance > Sebum control > Marketing ingredients
```

---

## 3. Anti-Fungal Ingredient Evidence Hierarchy

### Level 1: Strong Medical Evidence (★★★★★)

| Ingredient | Mechanism | Evidence | Best For |
| --- | --- | --- | --- |
| Ketoconazole | Anti-fungal (azole); inhibits ergosterol synthesis | A — Multiple RCTs; gold standard | Moderate-severe seborrheic dermatitis |
| Selenium Sulfide | Anti-fungal + reduces keratinocyte proliferation | A — Strong clinical evidence | Oily dandruff; seborrheic dermatitis |
| Piroctone Olamine | Anti-Malassezia | B — Effective for mild-moderate dandruff | Mild seborrheic dermatitis; lower irritation |
| Zinc Pyrithione | Anti-fungal + anti-bacterial + anti-inflammatory | A — Strong evidence (where permitted) | Broad-spectrum dandruff |

### Level 2: Adjunctive Ingredients (★★★★)

| Ingredient | Role | Evidence | Notes |
| --- | --- | --- | --- |
| Salicylic Acid | Keratolytic — removes scalp scale | B | Adjunctive only; does not treat underlying cause |
| PCA Zinc | Mild sebum regulation + antibacterial | C | Auxiliary ingredient |
| Panthenol | Barrier support + moisturization | C | Limited efficacy in rinse-off |
| Allantoin | Soothing + barrier support | C | Auxiliary role only |
| Coal Tar | Anti-proliferative | B | Effective but cosmetic acceptability low; carcinogen concern |

---

## 4. Surfactant System Evaluation

### Cleansing Strength (higher = more sebum removal, higher irritation risk)

| Level | Surfactants | Best For |
| --- | --- | --- |
| High | SLS, ALS | Very oily scalp only; not for sensitive/damaged |
| Moderate (Preferred) | SLES | Most scalp types; good balance |
| Mild | CAPB, Glucosides, Amino acid surfactants | Sensitive scalp; used as co-surfactants to reduce irritation |

### Preferred Surfactant Systems

| System | Irritation | Cleansing | Recommendation |
| --- | --- | --- | --- |
| SLES + CAPB | Low-Medium | Good | Gold standard for most shampoos |
| SLES + CAPB + Glucoside | Low | Good | Excellent for normal to dry scalp |
| Amino acid-based + CAPB | Very Low | Moderate | Sensitive / seborrheic dermatitis |
| SLS/ALS dominant | High | Strong | Oily scalp only; not for daily use |

### SLS/ALS in Shampoo
- High SLS/ALS → −0.10 Safety PS for sensitive scalp
- If SLS/ALS is sole surfactant → −0.15 Safety PS
- If SLS/ALS is blended with CAPB → reduced penalty (−0.05)

---

## 5. Hair Conditioning Ingredients

These improve cosmetic feel only. **No therapeutic effect on scalp disease.**

| Ingredient | Mechanism | Classification |
| --- | --- | --- |
| Dimethicone | Lubrication, reduced friction | [TM] Texture Modifier |
| Amodimethicone | Conditioning, anti-static | [TM] |
| Polyquaternium-10/7 | Anti-static, combability | [TM] |
| Guar Hydroxypropyltrimonium Chloride | Deposition aid, conditioning | [TM] |

**Rule**: Conditioning ingredients should not contribute to functional/efficacy scoring. They affect only user experience, not scalp health.

---

## 6. Marketing Ingredients in Shampoo

Evidence is weak in rinse-off products with 1–3 minute contact time:

| Ingredient | Claim | Reality |
| --- | --- | --- |
| Ginger extract | Hair growth | No clinical evidence in rinse-off |
| Ginseng | Hair strength | Oral benefits; no topical rinse-off evidence |
| Polygonum multiflorum (He Shou Wu) | Anti-grey, hair growth | Hepatotoxicity concern; no topical evidence |
| Rosemary oil | Hair growth | Limited evidence; mostly fragrance role |
| Peptides | Hair repair | Cannot penetrate in 1–3 min rinse-off |
| Biotin | Hair health | Deficiency-related only; no topical evidence |
| Collagen | Hair strength | No topical absorption |
| Stem cell extract | Regeneration | Cells are dead in formula; no mechanism |
| Plant extracts (general) | Various | Trace levels in rinse-off |

**Rule**: All of the above → [M] Marketing when in rinse-off shampoo, unless a specific leave-on clinical trial is cited.

---

## 7. Shampoo Weight Profile

| Dimension | Weight | Rationale |
| --- | --- | --- |
| Core Effectiveness (Anti-fungal/Cleansing) | 40 | Anti-fungal evidence + surfactant quality — the dominant factors |
| Safety / Barrier Friendliness | 30 | Surfactant mildness + irritant assessment |
| Architecture | 10 | Preservative system, pH, formulation logic |
| Support System | 10 | Adjunctive ingredients (salicylic acid, panthenol, allantoin) |
| Skin Adaptation | 5 | Scalp type matching (oily, dry, seborrheic, sensitive) |
| Marketing | 5 | Marketing ingredient ratio (penalty dimension) |

**Key difference from generic Cleanser**: Core Effectiveness is dominated by anti-fungal evidence for dandruff shampoos. For non-medicated shampoos, surfactant quality fills this dimension. Safety weight is higher (scalp is more vascularized, irritation risk is real).

---

## 8. Core Effectiveness Scoring (Shampoo-Specific)

For anti-dandruff / medicated shampoos, Core Effectiveness PS is determined by the **highest-priority anti-fungal present**:

| Anti-Fungal Present | CE_PS Base |
| --- | --- |
| Ketoconazole | 0.90 |
| Selenium Sulfide | 0.85 |
| Piroctone Olamine | 0.80 |
| Zinc Pyrithione | 0.80 |
| Salicylic Acid (as keratolytic) | 0.50 (adjunct only — insufficient alone) |
| None (non-medicated shampoo) | Surfactant quality evaluation |

For non-medicated shampoos: CE_PS is based on surfactant system quality and cleansing adequacy.

**Additive bonuses** (applied after base PS):
- Ketoconazole + any other anti-fungal → +0.05 (combination therapy)
- Salicylic Acid + anti-fungal → +0.05 (scale removal + anti-fungal)
- Panthenol present → +0.03 (barrier support)

---

## 9. Safety Scoring Adjustments (Shampoo-Specific)

| Condition | Adjustment |
| --- | --- |
| High fragrance (position ≤ 5) | −0.10 Safety PS |
| Multiple essential oils (≥3) | −0.10 Safety PS |
| SLS/ALS as sole surfactant | −0.15 Safety PS |
| MIT/CMIT preservative | −0.20 Safety PS (potent sensitizer on scalp) |
| Formaldehyde releaser (DMDM Hydantoin, etc.) | −0.10 Safety PS |
| Fragrance-free + sulfate-free + MIT-free | +0.10 Safety PS (ideal for sensitive/seb derm) |

---

## 10. Shampoo Anti-Hallucination Rules

- "Anti-hair-loss shampoo" without Ketoconazole/Minoxidil → marketing claim; flag
- "Anti-grey shampoo" → no topical mechanism exists; flag as unsupported
- Ginger / Ginseng / He Shou Wu / Biotin in rinse-off → [M] regardless of marketing
- Essential oils ≠ treatment: Tea tree has mild anti-fungal but is also a sensitizer; do not over-weight
- Menthol in shampoo → cooling sensation only (TRPM8); does not treat inflammation; [M]
- "Natural" / "Organic" / "Clean" shampoo → evaluate by same medical criteria; natural surfactants can still be irritants
- Conditioner ingredients (dimethicone, polyquaternium) → cosmetic only; do not count toward scalp health scoring
