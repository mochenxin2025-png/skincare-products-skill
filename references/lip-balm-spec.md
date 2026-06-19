# Lip Balm Specification v1.0

Supplement to the main framework. Covers lip balm, lip butter, lip mask, and SPF lip balm. Load when product is identified as "Lip Balm", "Lip Butter", "Lip Mask", "Lip Treatment", or "SPF Lip Balm".

---

## 1. First Principle

Lip balm is primarily an **occlusive barrier product**, not a therapeutic skincare product.

The physiological objective:
1. Reduce Transepidermal Water Loss (TEWL) across the lip surface
2. Maintain stratum corneum hydration
3. Protect damaged lip barrier from further insult
4. Reduce fissure formation and secondary irritation

**Lip dryness is caused by insufficient barrier function and excessive TEWL — not "water deficiency."** Drinking more water does not fix chapped lips.

**Special anatomy of lips**:
- Very thin stratum corneum (3–5 layers vs 15–20 on face)
- No sebaceous glands (no natural oil production)
- Transition zone to oral mucosa (semi-mucous membrane)
- High vascularity → rapid TEWL when barrier is compromised
- Frequent mechanical stress (talking, eating, licking)

Priority chain:
```
Occlusive > Barrier Repair > Humectant > Anti-inflammatory > Antioxidant > Marketing
```

---

## 2. Core Occlusive System (★★★★★ — 40% weight)

The occlusive system determines **>80% of lip balm performance**. Evaluate first.

| Rating | Ingredients |
| --- | --- |
| ★★★★★ (Gold Standard) | Petrolatum, Mineral Oil, Paraffin, Microcrystalline Wax, Ozokerite |
| ★★★★☆ (Excellent) | Beeswax, Hydrogenated Polyisobutene, Dimethicone, Shea Butter, Synthetic Wax |
| ★★★☆☆ (Adequate) | Lanolin, Candelilla Wax, Carnauba Wax, Polyethylene |

**Assessment**: 
- Petrolatum is the medical gold standard (reduces TEWL by >98%)
- Multi-wax systems (petrolatum + beeswax + microcrystalline wax) provide superior durability
- Pure oil-based balms (jojoba, coconut oil alone) → occlusive but low durability → −0.10 Architecture PS
- "Petrolatum-free" claims → check what replaced it; often less effective

---

## 3. Barrier Repair System (★★★★★ — 25% weight)

Lips are uniquely suited for barrier repair ingredients — thin SC means better penetration.

| Ingredient | Mechanism | Best For |
| --- | --- | --- |
| Ceramide NP | Lipid lamellae restoration | Chronic dryness, chapped lips |
| Panthenol | Wound healing + humectant | Fissures, cracked lips |
| Cholesterol | Barrier lipid component | Lipid-depleted lips |
| Free Fatty Acids | Intercellular lipid | Barrier reconstruction |
| Beta-Glucan | Immune modulation + soothing | Irritated lips |
| Glycyrrhetinate (Licorice derivative) | Anti-inflammatory | Cheilitis, inflammation |
| Allantoin | Soothing + wound healing | Mild irritation |

**Assessment**: For damaged/chapped lips, barrier repair is nearly as important as occlusion.

---

## 4. Humectant System (15% weight)

Humectants in lip balm require **occlusive support** to be effective. Without an occlusive seal, humectants may draw water OUT of the lip (low-humidity environments).

| Rating | Ingredients |
| --- | --- |
| ★★★★★ | Glycerin, Panthenol, Sodium Hyaluronate |
| ★★★★☆ | Sorbitol, Sodium PCA, Butylene Glycol |

**Rule**: Humectants without adequate occlusives → flag as formulation flaw. In lip balms, humectant system only contributes when paired with a ★★★★★ occlusive.

---

## 5. Anti-Inflammatory System (10% weight)

| Ingredient | Evidence |
| --- | --- |
| Glycyrrhetinate | ★★★★☆ (B) — Licorice-derived anti-inflammatory |
| Panthenol | ★★★★☆ (B) — Dual wound-healing + humectant |
| Beta-Glucan | ★★★☆☆ (C) — Immune modulation |
| Allantoin | ★★★☆☆ (C) — Soothing |
| Bisabolol | ★★★☆☆ (C) — Chamomile-derived anti-inflammatory |

---

## 6. Antioxidants (5% weight)

Primary function: **protect formulation stability** (prevent oil rancidity). Secondary: minor antioxidant support for lip skin.

| Ingredient | Role |
| --- | --- |
| Tocopherol (Vitamin E) | Oil-phase antioxidant; formulation protection |
| Tocopheryl Acetate | Stable precursor |
| Ascorbyl Tetraisopalmitate | Oil-soluble Vitamin C derivative |
| Ascorbyl Palmitate | Oil-soluble; formulation protection |

**Do not overestimate**: Anti-aging or whitening claims for lip balm antioxidants are unsupported. Score conservatively.

---

## 7. UV Filters (SPF Lip Balm Only)

The lower lip is a high-risk site for UV-induced squamous cell carcinoma. SPF in lip balm is **medically justified**, not marketing.

| Filter | Type | Notes |
| --- | --- | --- |
| Ethylhexyl Methoxycinnamate (Octinoxate) | UVB | Common in lip balms |
| Ethylhexyl Salicylate (Octisalate) | UVB | Often paired with avobenzone |
| Avobenzone | UVA | Requires stabilizer in lip balm matrix |
| Zinc Oxide | Broad-spectrum | Physical; may leave white cast on lips |
| Titanium Dioxide | UVB/UVA2 | Physical; common in tinted SPF balms |

**Rule**: SPF lip balm without UVA filter → insufficient protection (−0.10 Core Effectiveness PS for sun protection dimension).

---

## 8. Lip Balm Weight Profile

| Dimension | Weight | Rationale |
| --- | --- | --- |
| Core Effectiveness | 50 | Occlusive + Barrier Repair combined — the dominant factors |
| Architecture | 20 | Wax matrix durability, spreadability, film persistence |
| Safety | 20 | Irritant risk is HIGH for lip mucosa; menthol/camphor/fragrance are dangerous here |
| Support System | 5 | Anti-inflammatory + humectant + antioxidant |
| Skin/Lip Adaptation | 5 | Chapped / cheilitis / normal / SPF-needed |

### Core Effectiveness Scoring

```
CE_PS = (Occlusive_PS × 0.50) + (BarrierRepair_PS × 0.30) + (Humectant_PS × 0.20)

Occlusive_PS:
  1.00 = Petrolatum or Mineral Oil + secondary wax (beeswax, microcrystalline)
  0.70 = Single effective occlusive (petrolatum, lanolin, or multi-wax without petrolatum)
  0.40 = Only light occlusives (dimethicone, shea butter alone)
  0.10 = Oil-only base (jojoba, coconut, olive oil) — low durability

BarrierRepair_PS:
  1.00 = Ceramide + Cholesterol + Fatty Acid (physiological lipid ratio)
  0.70 = Panthenol + at least one lipid component
  0.40 = Panthenol or Allantoin alone
  0.10 = No barrier repair ingredients

Humectant_PS:
  1.00 = Glycerin or Sodium Hyaluronate + strong occlusive support
  0.50 = Humectant present but weak occlusive system
  0.10 = No humectant (occlusive-only balm — acceptable for pure barrier protection)
```

---

## 9. High-Risk Irritants (Lip-Specific)

**The lip is semi-mucous membrane — irritation risk is MUCH higher than body skin.**

| Risk | Ingredients | Severity | Effect |
| --- | --- | --- |
| Fragrance | Parfum | High | Direct irritation to lip mucosa |
| Menthol / Cooling Agents | Menthol, Menthyl Lactate, Peppermint Oil | HIGH | TRPM8 activation → cooling sensation → burning/stinging on damaged lips; **delays barrier recovery** |
| Camphor | Camphor | HIGH | Similar to menthol; no therapeutic benefit; delays healing |
| Essential Oils | Peppermint, Citrus, Eucalyptus, Tea Tree, Lavender | High | Direct chemical irritation + potential phototoxicity (citrus) |
| Fragrance Allergens | Limonene, Linalool, Citral, Eugenol, Geraniol | Medium-High | Cumulative sensitization on thin lip skin |
| Citrus Extracts | Lemon, Orange, Lime, Bergamot Peel Extract | High | Phototoxic + acidic irritation on damaged barrier |
| Salicylic Acid | — | Medium | Not appropriate for lip skin unless specifically treating a diagnosed condition |
| Alcohol Denat. | — | Medium | Drying; counterproductive for a barrier product |

**Critical Rule**: Menthol + camphor + cooling agents in lip balm → **−0.20 Safety PS**. These ingredients create a "cooling" sensation that tricks users into thinking the product is working, while actually delaying barrier recovery and potentially worsening chapped lips. This is one of the strongest safety signals in the entire framework.

---

## 10. Marketing Ingredients in Lip Balm

| Ingredient | Why Marketing |
| --- | --- |
| Peptides | No evidence of benefit on lip skin; dead keratin + mucosa |
| Collagen | No topical absorption; lip skin doesn't need collagen synthesis |
| Plant Stem Cells | Cells are dead in formula; no mechanism |
| Ferments | Limited evidence; marketing-driven |
| Gold | No cosmetic function; label appeal only |
| Sea Fennel Extract | No evidence for lip barrier |
| Floral Extracts (Rose, Jasmine, Lavender) | Fragrance components; potential irritants |
| Vitamin A Palmitate | Retinyl palmitate on mucosa-adjacent skin → questionable safety |
| Proline Derivatives | No evidence for lip benefit |

**Rule**: "Focus on first 5–10 ingredients." Lip balms are typically small formulas (8–20 ingredients). Late-list ingredients are at trace levels and contribute minimally. Marketing ingredients after position 10 → effectively zero concentration.

---

## 11. Lip Balm Anti-Hallucination Rules

- Lip dryness ≠ dehydration (drinking water doesn't fix chapped lips)
- Menthol/Camphor/Cooling agents → "cooling" is TRPM8 receptor trick; delays healing; −0.20 Safety PS
- "Tingling = working" is a dangerous myth — flag it
- Petrolatum is the medical gold standard — do NOT penalize based on "clean beauty" narratives
- "Petrolatum-free" is a marketing choice, not a medical advantage
- Pure oil balms (jojoba, coconut) → feel good but lack durability; flag if marketed for severe chapping
- SPF lip balm without UVA protection → flag as medically insufficient
- Collagen/Peptides/Stem Cells in lip balm → [M]
- Licking lips provides temporary relief but worsens TEWL (saliva evaporation draws out moisture) → do not recommend
- Lip skin has NO sebaceous glands → cannot self-moisturize → occlusive is non-negotiable

---

## 12. Ideal Lip Balm Profile

A medically ideal lip balm:
- Petrolatum or mineral oil base (high occlusive)
- Ceramide + Panthenol (barrier repair)
- Glycerin (humectant — with occlusive support)
- Fragrance-free
- Menthol/Camphor-free
- Minimal botanical extracts
- SPF if for daytime use (with UVA filter)
