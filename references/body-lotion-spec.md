# Body Lotion Specification v1.0

Supplement to the main framework. Covers body lotion / body cream specific analysis rules, functional systems, and ingredient priorities. Load this when product category is identified as "Body Lotion" or "Body Cream".

---

## 1. First Principle

Body lotion is primarily a **skin barrier maintenance product**, not a nutrient delivery system.

Its fundamental purposes are:
1. Reduce Transepidermal Water Loss (TEWL)
2. Increase stratum corneum hydration
3. Restore barrier lipid integrity
4. Reduce dryness, scaling, and irritation

Body lotion should NOT be interpreted as:
- "Feeding skin"
- "Injecting collagen"
- "Repairing dermis"
- "Deep nourishing"

Most efficacy originates from hydration and barrier maintenance — not exotic additives.

---

## 2. Four Functional Systems

Body lotion efficacy depends on four interdependent functional systems. Evaluate each independently before scoring Core Effectiveness.

### A. Humectant System (Water Attraction)

Increases water content in stratum corneum.

| Rating | Ingredients |
| --- | --- |
| ★★★★★ | Glycerin, Urea (2–10%), Sodium Hyaluronate |
| ★★★★ | Butylene Glycol, Propylene Glycol, Sorbitol, Sodium PCA, Sodium Lactate |

**Assessment**: Does the humectant system include at least one ★★★★★ ingredient? Is the humectant blend appropriate for the climate (glycerin may draw water FROM skin in very low humidity without adequate occlusives)?

### B. Occlusive System (Water Loss Prevention)

Reduces TEWL by forming an occlusive film. **Highest evidence-supported hydration mechanism.**

| Rating | Ingredients |
| --- | --- |
| ★★★★★ | Petrolatum, Mineral Oil, Paraffin, Dimethicone |
| ★★★★ | Hydrogenated Polyisobutene, Lanolin, Beeswax |

**Assessment**: Is there at least one effective occlusive? For very dry / barrier-impaired skin, petrolatum is the gold standard. Dimethicone is lighter — suitable for normal skin or daytime use.

### C. Emollient System (Gap Filling)

Fills corneocyte gaps, improves smoothness and softness.

| Rating | Ingredients |
| --- | --- |
| ★★★★★ | Caprylic/Capric Triglyceride, Squalane, Shea Butter, Sunflower Seed Oil |
| ★★★★ | Jojoba Oil, Avocado Oil, Sweet Almond Oil |

**Assessment**: Do emollients complement the occlusive system? Is the ratio appropriate for the target skin type?

### D. Barrier Repair System (Lipid Restoration)

Restores barrier lipid organization. **Highest medical value for dry or barrier-impaired skin.**

| Rating | Ingredients |
| --- | --- |
| ★★★★★ | Ceramide NP/AP/EOP, Cholesterol, Free Fatty Acids (Linoleic/Linolenic) |
| ★★★★ | Panthenol, Beta-Glucan, Allantoin, Phytosphingosine |

**Assessment**: Does it contain the physiological lipid ratio (ceramides:cholesterol:free fatty acids ≈ 3:1:1)? Panthenol alone is insufficient — true barrier repair requires lipids.

---

## 3. Body Lotion Weight Profile

| Dimension | Weight | Rationale |
| --- | --- | --- |
| Core Effectiveness | 40 | Hydration + Occlusion + Emollient + Barrier Repair combined as the primary function |
| Architecture | 20 | Spreadability and sensory feel determine compliance for large surface area application |
| Safety | 20 | Large surface area → cumulative irritation risk; body skin less sensitive than face but still relevant |
| Support System | 15 | Whitening, KP treatment, antioxidants, anti-inflammatory |
| Skin Adaptation | 5 | Body skin varies less than facial skin across types; KP and barrier-damage are the key differentiators |

**Key difference from facial moisturizer**: Architecture weight is lower (spreadability matters more than "elegance"), Safety weight is higher (surface area effect), Support System includes KP-specific ingredients.

---

## 4. Core Effectiveness Scoring for Body Lotion

Unlike other categories where Core Effectiveness is a single dimension, body lotion's Core Effectiveness PS is the **weighted average of the four functional systems**:

```
CE_PS = (Humectant_PS × 0.25) + (Occlusive_PS × 0.30) + (Emollient_PS × 0.20) + (BarrierRepair_PS × 0.25)
```

**Rationale**: Occlusive system has the strongest evidence for TEWL reduction (0.30). Humectants and barrier repair are equally important (0.25 each). Emollients primarily affect sensory experience (0.20).

### Per-System PS Criteria

| PS | Humectant | Occlusive | Emollient | Barrier Repair |
| --- | --- | --- | --- | --- |
| 1.00 | Multiple ★★★★★ humectants including glycerin or urea | Petrolatum or mineral oil at positions 1–5 | Multiple ★★★★★ emollients + good ratio | Physiological lipid ratio with ceramides + cholesterol + FFA |
| 0.70 | At least one ★★★★ humectant | Dimethicone or lanolin at adequate position | At least one ★★★★ emollient | Panthenol + at least one lipid component |
| 0.40 | Only glycols (butylene/propylene) | Only lightweight silicones, low position | Only one basic emollient | Only panthenol or allantoin alone |
| 0.10 | No dedicated humectant (water only) | No occlusive | No emollient | No barrier repair ingredients |

---

## 5. Skin Adaptation — Body Lotion Specific

| Skin Type | Key Considerations |
| --- | --- |
| **Normal** | Standard evaluation. Light occlusive (dimethicone) sufficient. |
| **Dry** | Require strong occlusive (petrolatum/mineral oil) + humectant (glycerin/urea). |
| **Very Dry / Barrier-Damaged** | Gold standard: Petrolatum + Ceramides + Cholesterol + FFA. Urea 5–10% if no fissures. |
| **Keratosis Pilaris (KP)** | Require keratolytic agents: Urea ≥ 5%, Lactic Acid, Salicylic Acid, Glycolic Acid, or PHA. Combined with emollients for tolerance. **Flag absence of keratolytics if product claims KP benefit.** |
| **Body Acne (Back/Chest)** | Avoid highly comedogenic emollients (Coconut Oil, Cocoa Butter, Isopropyl Myristate). Prefer non-comedogenic: Caprylic/Capric Triglyceride, Squalane, Dimethicone. |
| **Sensitive** | Fragrance-free, MIT/CMIT-free, formaldehyde-releaser-free. Minimal botanical extracts. |
| **Infant** | Highest safety standard. Petrolatum-based preferred. No fragrance, no essential oils, no MIT/CMIT, no formaldehyde releasers. Minimal ingredient count. |

---

## 6. Ingredient Evaluation Priority (Body Lotion)

When analyzing body lotions, prioritize ingredients in this order:

```
1. Barrier Maintenance (petrolatum, mineral oil, dimethicone, ceramides)
      ↓
2. Hydration System (glycerin, urea, sodium hyaluronate)
      ↓
3. Occlusive System (paraffin, hydrogenated polyisobutene)
      ↓
4. Barrier Repair (cholesterol, FFA, panthenol)
      ↓
5. Anti-inflammatory (bisabolol, allantoin, madecassoside)
      ↓
6. Keratolytic (urea ≥5%, lactic acid, salicylic acid — for KP)
      ↓
7. Whitening (niacinamide, tranexamic acid, alpha-arbutin)
      ↓
8. Antioxidant (vitamin C, vitamin E, coenzyme Q10)
      ↓
9. Botanical Extracts (centella, chamomile, calendula)
      ↓
10. Marketing Ingredients (truffle, collagen, milk extracts, floral waters)
```

Lower-priority ingredients may enhance but should never dominate the evaluation. A body lotion with excellent barrier maintenance but no whitening ingredients scores HIGHER than one with multiple whitening actives but poor occlusive coverage.

---

## 7. Auxiliary Ingredients (Do NOT Score as Efficacy)

The following ingredient classes are **formulation support only**. Never count them toward Core Effectiveness, Support System, or any positive scoring dimension:

- PEG emulsifiers (PEG-100 Stearate, PEG-40 Hydrogenated Castor Oil, etc.)
- Carbomer / Acrylates crosspolymers
- Xanthan Gum / Hydroxyethylcellulose
- EDTA / Sodium Phytate (chelators)
- Citric Acid / Sodium Hydroxide (pH adjusters)
- Triethanolamine / Aminomethyl Propanol (neutralizers)
- Fatty Alcohols (Cetyl, Stearyl, Cetearyl Alcohol) — unless explicitly serving as emollient thickeners in a balm
- Stearic Acid / Palmitic Acid — unless in a ceramide-dominant barrier repair context

**Rule**: If an ingredient's primary function is to hold the formula together, it does not contribute to the efficacy score. Flag if a product markets auxiliary ingredients as actives.

---

## 8. Body Lotion Specific Anti-Hallucination Rules

- "Collagen in body lotion" → Does not penetrate stratum corneum. Marketing, not efficacy. Always classify as [M].
- "Milk / Goat Milk / Donkey Milk extract" → No evidence of topical barrier benefit. Marketing.
- "Bird Nest / Placenta extract" → No topical evidence. Marketing.
- "White Truffle / Lily / Sakura / Rose extract" → Fragrance/marketing components. No barrier benefit.
- Antioxidants in body lotion → Evidence is moderate at best. Contact time on body skin is limited. Do not over-weight.
- Body lotion whitening → Mild at best. Primary determinant of body hyperpigmentation is UV exposure. Do not claim significant whitening from body lotion alone.
- Large numbers of botanical extracts positioned after preservatives → Trace concentrations. Marketing-oriented. Apply penalty if >30% of listed ingredients.

---

## 9. Body Lotion Ingredient Quick-Reference

### Barrier-Friendly (Preferred for Chronic Use)

Glycerin, Petrolatum, Mineral Oil, Dimethicone, Panthenol, Ceramide NP/AP/EOP, Cholesterol, Free Fatty Acids, Squalane, Caprylic/Capric Triglyceride, Shea Butter, Sunflower Seed Oil

### Attention Required (Potential Irritants — Flag for Sensitive/Damaged Skin)

Fragrance/Parfum, Essential Oils, Methylisothiazolinone (MIT), Methylchloroisothiazolinone (CMIT), Formaldehyde-releasing preservatives, High-concentration Ethanol/Alcohol Denat., High-concentration AHA (in leave-on, >10%)

### Keratosis Pilaris Actives

Urea (≥5%), Lactic Acid, Salicylic Acid, Glycolic Acid, PHA (Gluconolactone/Lactobionic Acid), Ammonium Lactate

### Body Acne Considerations

- Avoid: Coconut Oil, Cocoa Butter, Isopropyl Myristate, Isopropyl Palmitate (comedogenic rating ≥3)
- Prefer: Caprylic/Capric Triglyceride, Squalane, Dimethicone, Sunflower Seed Oil (comedogenic rating 0–1)
