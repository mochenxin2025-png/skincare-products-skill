# Body Wash Specification v1.0

Supplement to the main framework. Covers body wash / shower gel specific analysis rules. Load when product is identified as "Body Wash", "Shower Gel", or "Shower Cream".

---

## 1. First Principle

Body wash is a **rinse-off cleanser** with approximately 20–60 seconds of skin contact. Its biological function is:

- Remove sebum, sweat, and environmental contaminants
- Remove sunscreen residue
- Reduce microbial metabolites
- Maintain skin barrier integrity

It is NOT designed to:
- Repair skin barrier
- Whiten skin
- Anti-age
- Firm skin
- Long-term moisturize

**Core principle: Short contact time → limited absorption → limited biological effect. Most functional ingredients have greatly reduced efficacy in rinse-off products.**

---

## 2. Ingredient Priority for Body Wash

```
Cleansing System (surfactants)
        ↓
Barrier Compatibility (mildness)
        ↓
Functional Ingredients (anti-acne, anti-fungal)
        ↓
Supporting Ingredients (stabilizers, chelators)
        ↓
Marketing Ingredients (plant extracts, peptides, etc.)
        ↓
Risk Ingredients (fragrance, SLS, colorants)
```

The surfactant system determines >80% of product performance.

---

## 3. Surfactant System Evaluation

### Preferred Surfactant Systems

| System | Mildness | Cleansing | Best For |
| --- | --- | --- | --- |
| SLES + CAPB | ★★★★☆ | ★★★★☆ | Most skin types (gold standard balance) |
| SLES + CAPB + Glucoside | ★★★★★ | ★★★★☆ | Normal to dry |
| Amino acid surfactants | ★★★★★ | ★★★☆☆ | Sensitive, barrier-damaged |
| SLS alone | ★★☆☆☆ | ★★★★★ | Oily only; not for daily use |

### Individual Surfactant Ratings

| Rating | Surfactants |
| --- | --- |
| ★★★★★ (Excellent) | SLES, CAPB, Sodium Lauroyl Glutamate, Potassium Cocoyl Glycinate, Decyl Glucoside, Lauryl Glucoside, Coco Glucoside |
| ★★★☆☆ (Acceptable — oily skin only) | SLS, ALS |

### SLS-Specific Assessment
- Strong cleansing / excellent oil removal / strong foaming
- BUT: higher irritation, increased TEWL, less barrier-friendly
- Suitable only for oily skin; avoid in sensitive, dry, or barrier-damaged skin
- If SLS is the ONLY surfactant → Safety PS penalty (−0.15)
- If SLS is part of a blend with CAPB/glucosides → reduced penalty (−0.05)

---

## 4. Functional Ingredients in Body Wash

In rinse-off products, functional ingredients have **limited efficacy** due to short contact time. Score conservatively.

| Ingredient | Function | Evidence in Rinse-Off | PS Adjustment |
| --- | --- | --- | --- |
| Piroctone Olamine | Anti-fungal, anti-Malassezia, odor reduction | ★★★★☆ (B) | +0.15 to Support PS if for seborrheic skin |
| Salicylic Acid | Body acne, keratosis pilaris | ★★★☆☆ (B) | +0.10 to Support PS for acne/KP claims |
| Ketoconazole | Anti-fungal (therapeutic) | ★★★★★ (A) | +0.20 to Support PS (Rx-level) |
| Zinc PCA | Mild oil regulation | ★★☆☆☆ (C) | +0.05 to Support PS |
| Glycerin | Humectant (most useful additive in rinse-off) | ★★★★☆ (B) | +0.10 to Safety PS (barrier support) |
| Panthenol | Barrier support | ★★★☆☆ (C) | +0.05 to Safety PS |
| Allantoin | Soothing | ★★☆☆☆ (C) | +0.05 to Safety PS |

---

## 5. Rinse-Off Efficacy Limitation (Critical Rule)

Ingredients in the **last one-third of the INCI list** in rinse-off products → assume:
- Low concentration
- Limited efficacy
- Primarily marketing enhancement

**Unless** the ingredient is a recognized therapeutic active (Ketoconazole, Piroctone Olamine, Salicylic Acid at therapeutic levels).

This applies to: Niacinamide, Hyaluronic Acid, Ceramides, Peptides, Collagen, Ferments, Plant extracts.

**Rule**: If these ingredients appear only in the last third of a body wash ingredient list → classify as [M] Marketing, not [A] or [FS].

---

## 6. Experience Ingredients (New Concept)

Some ingredients produce sensory experiences without actual physiological benefit:

| Ingredient | Mechanism | Medical Value | Experience Value | Classification |
| --- | --- | --- | --- | --- |
| Menthol | TRPM8 receptor → cooling sensation; does NOT reduce skin temperature | ★★☆☆☆ | ★★★★★ | [M] — Sensory engineering |
| Sea Salt | Sodium chloride; cannot repair barrier, whiten, or hydrate | ★☆☆☆☆ | ★★★★☆ | [M] — Marketing concept |
| Camphor | Similar to menthol; cooling sensation via TRP channels | ★★☆☆☆ | ★★★★☆ | [M] — Sensory engineering |

**Rule**: Experience ingredients contribute ZERO to efficacy scoring. Flag in report as "sensory ingredient — no therapeutic benefit."

---

## 7. Body Wash Weight Profile

| Dimension | Weight | Rationale |
| --- | --- | --- |
| Core Effectiveness (Cleansing) | 35 | Surfactant system quality — the dominant factor |
| Safety / Barrier Friendliness | 25 | Large surface area, daily use → cumulative irritation risk |
| Support System (Functional) | 15 | Anti-acne, anti-fungal — limited by rinse-off nature |
| Architecture (Formula Logic) | 10 | Preservative system, pH, stabilizer adequacy |
| Skin Adaptation | 5 | Body skin varies less than face |
| Marketing | 10 | Marketing ingredient ratio assessment (penalty dimension) |

**Key difference from facial Cleanser**: Lower Architecture weight (spreadability matters, elegance doesn't). Higher Safety weight (whole-body surface area). Marketing is a scored dimension rather than just a penalty.

---

## 8. Risk Ingredients (Body Wash Specific)

| Risk | Severity | Assessment |
| --- | --- | --- |
| Fragrance/Parfum | Medium | Most common irritation source; higher position = higher concern |
| Essential Oils (Ylang Ylang, Lavender, Rosemary, etc.) | Medium-High | Contact dermatitis risk; "natural" ≠ low irritation |
| SLS as sole surfactant | Medium | High irritation potential; −0.15 Safety PS |
| Colorants (CI 19140, CI 17200, CI 42090, etc.) | Low | Visual only; no skincare value; may irritate very sensitive skin |
| MIT/CMIT | High | Potent sensitizers; avoid entirely in body wash |
| Formaldehyde releasers | Medium | Cumulative sensitization risk with daily whole-body use |

---

## 9. Body Wash Anti-Hallucination Rules

- Plant extracts (Rose, Camellia, Lotus, Lavender, Aloe, Centella, Ginseng, Green Tea) in rinse-off → trace levels, negligible efficacy → [M]
- Peptides / Collagen / Ceramides / Niacinamide / Hyaluronic Acid in body wash last-third → [M]
- Ferments / Gold flakes → [M] regardless of position
- "Moisturizing body wash" claim → check humectant system (glycerin, panthenol); if absent → marketing claim only
- "Whitening body wash" → near-impossible in rinse-off; flag as unsupported claim
- "Anti-aging body wash" → impossible in rinse-off; flag as unsupported claim
