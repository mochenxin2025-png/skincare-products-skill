# Toner Specification v1.0

Supplement to the main framework. Covers toners, fresheners, essences, and essence-toners — watery leave-on products whose job is delivery and surface-state modulation. Load this when the product category is identified as **"Toner"**.

---

## 1. First Principle

A toner delivers **water-soluble actives** in an aqueous vehicle and modulates the skin's **surface state** — hydration, pH, the sensory impression of oiliness — while leaving almost no residue.

It is a **vehicle category, not a treatment category**. Its efficacy ceiling is set by how much of a water-soluble active can cross the stratum corneum without any occlusion to help it. A toner cannot match a serum's delivered dose, and scoring it as one is an error.

A toner should NOT be interpreted as:
- "Second cleansing" — unless the formula actually contains a surfactant, it removes nothing
- "Tightening" or "shrinking" pores — astringent sensation is not a change in pore diameter
- "Deep hydration" — water applied to the surface does not hydrate the dermis
- A substitute for a moisturiser — without occlusives, added water evaporates and can increase TEWL

---

## 2. Terminology Map (read before classifying)

This is the category most often mis-classified, because the same word means different products in different markets. Resolve the term first; the sub-type follows.

| Term | Market / language | Actual product | Category here |
| --- | --- | --- | --- |
| 化妆水 / 爽肤水 / 柔肤水 / 收敛水 | 中文 | Watery leave-on | **Toner** |
| 精华水 / 高机能水 | 中文 | Watery leave-on with a higher active load | **Toner** (essence-toner) |
| 化粧水 | 日文 | Watery leave-on | **Toner** |
| 乳液 | 中文 | Fluid emulsion, oil + water | **Moisturizer** |
| 乳液 / 化粧水 (JP usage) | Japanese brands in English | `lotion` often means the watery product | **Toner** |
| Lotion | US / EU | Fluid emulsion | **Moisturizer** |
| Toner / freshener / astringent / clarifying lotion | English | Watery leave-on | **Toner** |
| Essence | English (Asian brands) | Watery leave-on | **Toner** |
| 喷雾 / facial mist | 中文 / English | Sprayed watery product | **Toner** (same vehicle logic) |
| 刷酸水 / acid toner | 中文 | Acid exfoliant | **Exfoliation** — see §9 |

**If the input is ambiguous between `Toner` and `Moisturizer`, ask which texture the product has** (watery vs fluid/creamy) rather than guessing. Two-letter differences here change the entire evaluation.

---

## 3. Sub-types

Classify into exactly one primary sub-type before scoring.

| Sub-type | Marker ingredients | Primary purpose | Main risk |
| --- | --- | --- | --- |
| **Hydrating** | Glycerin, butylene glycol, hyaluronic acid, betaine, panthenol | Surface hydration | Low; over-claiming is the risk, not irritation |
| **Astringent** | Ethanol (high), witch hazel, alum, aluminium salts, tannins | Sebum/oil sensory reduction, transient tightening | Barrier disruption, stinging, reactive sebum |
| **Residue-removal** | A genuine surfactant (PEG-xx glyceryl esters, polysorbates, micelle formers) | Remove cleanser residue / light makeup | Surfactant left on skin; irritation in sensitive skin |
| **Essence-toner** | Multiple declared actives at meaningful positions | Deliver water-soluble actives | Over-loading actives at sub-effective concentrations (marketing dilution) |
| **Acid toner** | AHA/BHA/PHA + declared or low pH | Exfoliation | → route to Exfoliation (§9) |

A hydrating toner and an astringent toner share a container and nothing else. Do not average them into one "toner" judgement.

---

## 4. Toner Weight Profile

| Dimension | Weight |
| --- | --- |
| Core Effectiveness | 30 |
| Architecture | **30** |
| Safety | 25 |
| Support System | 10 |
| Skin Adaptation | 5 |

Architecture carries 30 — as high as the core dimension — because in a water-only vehicle the carrier **is** most of the product: solvent system, penetration support, preservative adequacy, and pH all live in the architecture layer.

---

## 5. Core Effectiveness Scoring (Toner)

| Level | Criteria |
| --- | --- |
| 0.9 – 1.0 | A water-soluble active with clinical evidence, declared at an effective concentration, in a vehicle that supports its stability and penetration (co-solvent present, no incompatible pH) |
| 0.7 – 0.89 | One good active at a plausible concentration, adequate vehicle, no architectural flaws |
| 0.5 – 0.69 | Actives present only at humectant or marketing positions; or a good active diluted below any effective range |
| 0.3 – 0.49 | Only humectants and water; actives in the last third of the list |
| 0.0 – 0.29 | Water + fragrance + colour; "essence" claims with no declared active above trace |

Mandatory:

- **Water-soluble only.** A lipophilic active in a purely aqueous toner without a co-solvent or solubiliser is not delivered — reduce Core PS and say why.
- Concentration matters more here than in any other category: a toner at 20,000 ppm glycerol and a toner at 1% of a clinical active are not comparable products. Do not reward the length of the ingredient list (the framework's marketing-overuse penalty applies).
- **No occlusion → no penetration enhancement.** Do not credit a toner with the penetration profile of a serum or an occlusive mask.

---

## 6. Architecture (Weight 30)

| Element | Evaluate |
| --- | --- |
| Solvent system | Water alone, or water + co-solvents (butylene glycol, dipropylene glycol, 1,2-hexanediol, propanediol) — co-solvents raise both solubility and penetration |
| Alcohol content | Ethanol in the first five positions of an astringent → see §7 |
| pH | Declared or derivable; matters for acid toners (→ Exfoliation) and for actives with pH demands (see `references/interaction-rules.md` Rule 21, Rule 22) |
| Preservation | **A water-based leave-on with a single preservative, or with no declared preservative system, is a flag** — this is the framework's standing rule, and it applies most often in this category |
| Penetration support | Solubilisers, glycols, mild surfactant actives — absence limits everything above it |
| Fragrance / essential oils | Position and count; fragrance in a leave-on water product is the commonest sensitisation source in this category |

---

## 7. Risk Profile

| Risk | Trigger | Action |
| --- | --- | --- |
| Barrier disruption from alcohol | Ethanol in the first five positions of an astringent toner | Safety PS −0.15, flag for dry / sensitive / barrier-damaged skin |
| Reactive oiliness | High-alcohol astringent marketed as oil control | Explain that stripping surface lipids can increase sebum output; flag the claim |
| Sensitisation | Fragrance, essential oils, or botanical extracts in a leave-on water product | Safety PS −0.10; ⚠️/❌ in Skin Adaptation for sensitive and rosacea |
| Preservative inadequacy | Single preservative or none in a water-based leave-on | Flag (standing framework rule) |
| Extreme pH | pH < 3.5 (acid toner) or > 7 sustained (some "mineral" toners) | Reduce Safety PS; for acid toners route to Exfoliation |
| Irritant residue | Residue-removal toner left on skin rather than wiped/rinsed | Flag; contact time defeats the design intent |

---

## 8. Skin Adaptation — Toner

| Skin type / condition | Suitability | Note |
| --- | --- | --- |
| Normal | ✅ | |
| Dry | ⚠️ | Hydrating sub-type only; astringents worsen dryness |
| Oily | ✅ | |
| Combination | ✅ | |
| Sensitive | ⚠️ / ❌ | Fragrance-free, alcohol-free hydrating toners only |
| Acne-prone | ✅ | Prefer hydrating or BHA-based (→ Exfoliation) over alcohol astringents |
| Seborrheic dermatitis | ⚠️ | Avoid fragrance and fatty alcohol-free "clarifying" products with alcohol |
| Rosacea | ❌ / ⚠️ | Alcohol and fragrance are common triggers |
| Barrier-damaged | ❌ | No acids, no alcohol, no fragrance; hydrating only |
| Keratosis pilaris | ⚠️ | Not a body format; see Exfoliation |
| Body acne | ⚠️ | Not a body format |
| Infant | ❌ | Water + fragrance products are inappropriate |

---

## 9. Category Boundary Rules

Precedence: `Exfoliation > Acne Serum > Mask > Toner > Moisturizer`

| Product | Category | Reason |
| --- | --- | --- |
| Acid toner / 刷酸水 with declared low pH and AHA/BHA | **Exfoliation** | Primary intent is keratolysis; the toner vehicle is incidental |
| Essence-toner with a clinical active and no acid | **Toner** | |
| "Emulsion" / 乳液 / fluid lotion | **Moisturizer** | Oil phase present |
| Toner used as a mask (compressed sheet soaked in toner) | **Mask** | Contact mode changes the physics |
| Facial mist | **Toner** | Same vehicle logic; score as a toner with negligible contact |

---

## 10. Anti-Hallucination Rules (Toner)

- **"Second cleansing" requires a surfactant.** Without one, the product removes nothing — flag the claim.
- **"Pore tightening" has no mechanism.** Astringent tightening is a temporary protein/astringent effect, not a change in pore size.
- **"Deep hydration" / "dermal hydration"** from a topical water product → unsupported. Water added to the surface evaporates; without occlusives it can raise TEWL.
- **A long ingredient list is not efficacy.** Apply the framework's marketing-overuse penalty when plant extracts and ferments dominate.
- **"Alcohol-free" claims:** verify against the ingredient list — cetearyl alcohol and benzyl alcohol are not the same as ethanol. Do not penalise fatty alcohols.
- **"pH-balanced"** without a number is marketing. Do not credit it.
- A toner containing no declared active above trace → Core Effectiveness ≤ 0.29, regardless of how many botanicals appear.
- Do not infer hydration from the word "moisture" in the product name.

---

## 11. Ingredient Quick Reference

**Useful in a toner vehicle**
Glycerin · Butylene glycol · Dipropylene glycol · Propanediol · Panthenol · Allantoin · Sodium hyaluronate (surface hydration) · Niacinamide (water-soluble, 2–5%) · Betaine

**Needs a co-solvent or solubiliser to be delivered**
Tocopherol · Retinoids · Oil-soluble botanical extracts · Ceramides (require liposomal or glycol-based delivery)

**Flag**
Ethanol in the first five positions · Fragrance in a leave-on water product · Witch hazel distillate at high concentration · Essential oils presented as actives · Single or absent preservative system in a water-based leave-on

**No mechanism — marketing only**
"Mineral water" claims · "Oxygenating" · "Collagen-infused" (no penetration) · Ferment filtrates without declared metabolites · "Detox"
