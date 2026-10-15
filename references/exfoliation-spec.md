# Exfoliation Specification v1.0

Supplement to the main framework. Covers exfoliating and keratolytic treatments — acid toners/serums/peels, scrubs, and peel-off films. Load this when the product category is identified as **"Exfoliation"**.

---

## 1. First Principle

An exfoliant's job is to **accelerate desquamation of corneocytes** — to remove excess stratum corneum — **without crossing into barrier injury**.

The therapeutic window between keratolysis and barrier damage *is* the product quality question. Everything else (penetration depth, "glow", resurfacing claims) is downstream of how well a product holds that window.

An exfoliant should NOT be interpreted as:
- "Removing toxins" or "detoxifying"
- "Shrinking pores" (pore size is structural; contents can be cleared, diameter cannot be reduced)
- "Regenerating skin" or "renewing" in a dermal sense — the action is confined to the epidermis
- A route to deliver actives deep into the skin (that is a peel's clinical territory, not a cosmetic's)

---

## 2. Mechanism Classes

Classify before scoring. Different classes have different action depths, different optimal pH, and different risk ceilings.

| Class | Members | Action site | Notes |
| --- | --- | --- | --- |
| AHA (α-hydroxy acid) | Glycolic (C2, smallest → deepest AHA penetration), lactic (C3), malic, tartaric, citric, mandelic (C8, largest of the common AHAs → slowest, gentlest) | Water-soluble, stratum corneum intercellular cohesion | Effectiveness is pH-gated (§3). Glycolic has the smallest molecule and the highest irritation potential of the class. |
| BHA (β-hydroxy acid) | Salicylic acid; betaine salicylate (gentler, same class) | Lipophilic → sebaceous pore penetration | The only common BHA. Comedolytic as well as keratolytic — see the *Comedogenicity Evaluation Protocol* in `references/acne-serum-spec.md`. |
| PHA (polyhydroxy acid) | Gluconolactone, lactobionic acid, galactose | Large molecules → slow, surface-biased | Also humectant and antioxidant; generally the gentlest chemical option. Suitable first-line for sensitive or barrier-compromised skin. |
| Urea | Urea | Keratolytic **≥10%**; humectant **<10%** | Concentration-dependent role reversal — classify by the declared percentage, not by the ingredient name. |
| Enzymes | Papain, bromelain, subtilisin, keratinase | Protein-specific proteolysis | Activity depends on pH, temperature and contact time; in a 1–2 minute consumer wash-off the effective dose is unverified. Evidence level C–D. |
| Physical | Scrub particles, cleansing brushes, konjac/gauze | Mechanical abrasion | Weak evidence for benefit over chemical exfoliation, plus microtear risk. Solid plastic microbeads are banned in many jurisdictions. |
| Peel-off film | PVA/acrylic films | Physical removal of corneocytes with the film | Irritating on repeated use; barrier risk. Route to §11 Category Boundaries. |

---

## 3. pH — The Decisive Variable

Acids act in their **free-acid (protonated) form**. Total acid concentration is almost meaningless without pH: at a given concentration, raising pH converts the acid to its salt and collapses the effective fraction.

| Class | Effective pH range | Comment |
| --- | --- | --- |
| AHA | ≤ 4.0 (commonly formulated 3.5–4.0) | Above pH 4, free-acid fraction falls off rapidly |
| BHA (salicylic acid) | 3.0–4.0 | pKa ≈ 2.97; below pH 3 irritation rises steeply without proportional benefit |
| PHA | 3.5–4.5 | Larger molecules; gentler even at the low end |
| Urea | pH ~6 (not an acid mechanism) | Do not apply the acid rules to urea |

Rules:

- **If pH is not declared, do not assume it.** Derive a *suspicion*, never a value: an AHA/BHA paired with a neutralizer (sodium/potassium hydroxide, arginine, tromethamine, aminomethyl propanol) in a formula that also declares preservatives with a neutral-optimal pH is likely to sit **above pH 4** — treat as reduced efficacy and state the uncertainty in the report.
- A high declared acid with a neutralising counter-ion and no pH disclosure → **Core Effectiveness PS ≤ 0.30**, and record "pH unknown — efficacy unverifiable" as a data gap.
- pH < 3.0 on a leave-on consumer product → flag as out of the cosmetic range for consumer use (see §4 ceilings) and reduce Safety PS.
- Existing interaction rules already cover the acid↔pH cases; do not restate them here — see `references/interaction-rules.md` Rule 12 (citric acid high % + pH-sensitive active), Rule 21 (L-AA requires pH < 3.5), Rule 22 (SAP requires pH ~7).

---

## 4. Concentration Ceilings and Regulatory Limits

These are hard numbers with sources (§14). A product exceeding the ceiling for its market is not merely "strong" — it is either non-compliant as a cosmetic, or it is not a cosmetic.

| Market | AHA | Salicylic acid (BHA) | pH |
| --- | --- | --- | --- |
| **China** — 《化妆品安全技术规范》2015 | Total α-hydroxy acids + salts + esters **≤ 6.0%** | As a restricted ingredient: **≤ 2.0%** in leave-on and rinse-off skin products; **≤ 3.0%** in rinse-off hair products. Not permitted in products for children under 3 (shampoo excepted). As a preservative: **≤ 0.5%** (as acid) | AHA-containing products: **pH ≥ 3.5**. Label must state use together with sunscreen |
| **EU** — Reg. 1223/2009 Annex III/98 + Annex V | No Annex ceiling for AHAs generally; SCCNFP evaluated glycolic/lactic at a worst case of 10% at pH 3.5 | Rinse-off hair **≤ 3.0%**; other products **≤ 2.0%**; body lotion, eye shadow, mascara, eyeliner, lipstick, oral products, non-spray deodorant **≤ 0.5%**; not for under-3s (shampoo excepted) | — |
| **US** — FDA labelling guidance for AHA cosmetics (2005) | **≤ 10%** and **pH ≥ 3.5** for consumer products; must be formulated with sun protection or carry a sunburn-alert label | — | ≥ 3.5 |
| **Professional / salon** — CIR (2013) | **≤ 30% at pH ≥ 3.0**, brief and discontinuous use, thorough rinsing, trained operator only | — | ≥ 3.0 |

Scoring consequences:

- Exceeds the ceiling for the declared market → **Safety PS −0.30** and flag: either outside the cosmetic regime or a compliance failure. Never silently score it as a normal cosmetic.
- AHA product with no sunscreen warning → flag (China requires the statement; the FDA guidance requires the alert).
- Salicylic acid in a leave-on product for a child under 3 → **hard fail**, state the restriction.

---

## 5. Contact Mode — the Fourth Multiplier

Actual exposure ≈ concentration × free-acid fraction (pH) × contact time × frequency. All four matter; three of four is not enough to judge.

| Mode | Typical contact | Consequence |
| --- | --- | --- |
| Leave-on (acid toner, serum, peel) | Hours | Full effect and full irritation exposure |
| Rinse-off, wash-off (scrub, cleanser, clay mask) | 20–60 s | Effect limited by contact time; an acid in a rinse-off cleanser is largely cosmetic |
| Rinse-off, extended (mask, 10–20 min) | Minutes | Real but bounded effect — evaluate as a short, high-dose exposure |

For rinse-off formats, apply the framework's standing rule: ingredients in the last third of the list are trace and are reclassified `[M]` unless they are a recognised therapeutic active.

---

## 6. Exfoliation Weight Profile

| Dimension | Weight |
| --- | --- |
| Core Effectiveness | 35 |
| Architecture | 15 |
| Safety | **30** |
| Support System | 10 |
| Skin Adaptation | 10 |

Safety carries 30 — the same order as a cleanser — because the dominant harm in this category is **cumulative over-use**, not an individual irritant. Architecture carries only 15: an acid's vehicle matters far less than its pH and its dose.

---

## 7. Core Effectiveness Scoring (Exfoliation)

| Level | Criteria |
| --- | --- |
| 0.9 – 1.0 | Recognised keratolytic at a declared, effective concentration **and** pH in the effective range for its class, verified format suited to the claim |
| 0.7 – 0.89 | Effective acid, pH plausible or declared within range, concentration at the lower end of effective |
| 0.5 – 0.69 | Acid present but concentration or pH suboptimal; or an enzyme/urea product with a declared effective concentration |
| 0.3 – 0.49 | Neutralising system present or pH unknown; or a rinse-off format where contact time defeats the mechanism |
| 0.0 – 0.29 | No declared quantitative basis ("gentle exfoliation" with no percentage and no pH); physical scrub marketed with resurfacing claims |

Mandatory:

- **No concentration and no pH → no numeric score.** Return conservative mode for Core Effectiveness. An unverifiable exfoliant must not receive a number.
- Two acids in one formula do not stack their PS — score the effective system once, and adjust Safety for the added cumulative load.

---

## 8. Over-Exfoliation and Stacking

The realistic harm model is cumulative, not single-product.

- Count the exfoliating actives in the formula. **≥ 3 keratolytic actives** plus alcohol or fragrance → flag as a high-irritation combination and reduce Safety PS.
- Cross-product stacking is out of scope for a single-product analysis, but **must be stated**: any leave-on acid product warrants a note that concurrent use of other acids, retinoids, or high-concentration ascorbic acid multiplies the load. Cite the existing interactions rather than inventing new ones — Rule 6 (retinol + AHA), Rule 9 (glycolic + salicylic), Rule 11 (AHA + PHA).
- Frequency guidance is part of the report: daily leave-on acid use alongside other actives is a barrier-load decision, not a free choice.
- Sun sensitivity rises after AHA use. A recommendation for an AHA product without a sunscreen statement is incomplete.

---

## 9. Skin Adaptation — Exfoliation

| Skin type / condition | Suitability | Note |
| --- | --- | --- |
| Normal | ✅ | |
| Dry | ⚠️ | Low frequency; PHA or lactic over glycolic |
| Oily | ✅ | |
| Combination | ✅ | |
| Sensitive | ⚠️ / ❌ | PHA first-line only; leave-on AHA generally unsuitable |
| Acne-prone | ✅ | BHA preferred (follicular penetration) |
| Seborrheic dermatitis | ⚠️ | Do not treat the scalp with leave-on acids; risk of flare |
| Rosacea | ❌ / ⚠️ | Acids commonly trigger flushing; only under dermatological direction |
| Barrier-damaged | ❌ | Contraindicated until the barrier is restored |
| Keratosis pilaris | ✅ | AHAs (lactic, glycolic) have the best evidence here |
| Body acne | ✅ | BHA; see also the acne spec |
| Infant | ❌ | Not permitted / not appropriate |

---

## 10. Interaction Notes

No new rules are defined in this specification. The pairs that matter are already in `references/interaction-rules.md` and must be cited, not duplicated:

| Situation | Existing rule |
| --- | --- |
| Exfoliating acid + retinoid | Rule 6 — Retinol + AHA (glycolic/lactic) |
| Two acids in one formula | Rule 9 — Glycolic + Salicylic; Rule 11 — AHA + PHA |
| Acid + pH-sensitive active | Rule 12 — Citric acid (high %) + any pH-sensitive active |
| Acid + peptide | Rule 20 — Argireline + any strong acid |
| Ascorbic acid's own pH demand | Rule 21 / Rule 22 |

---

## 11. Category Boundary Rules

Assign a product to one category, by **primary intent**. When two categories could claim it, precedence is:

`Exfoliation > Acne Serum > Mask > Toner > Moisturizer`

| Product | Category | Reason |
| --- | --- | --- |
| "Acid toner", peel solution, acid serum | **Exfoliation** | Primary intent is keratolysis |
| Scrub (facial or body) | **Exfoliation** | Mechanical keratolysis |
| Peel-off film mask | **Exfoliation** | Physical removal of corneocytes |
| Cleanser with a token acid | Cleanser | Contact time defeats the acid |
| Anti-acne product whose mechanism is keratolysis only | **Exfoliation** if the claim is exfoliating; Anti-Acne Serum if the claim is lesion reduction |
| Hydrating toner containing no acid | Toner | |

---

## 12. Anti-Hallucination Rules (Exfoliation)

- **No concentration + no pH → no numeric score.** Conservative mode, list the gaps.
- Never infer pH from an ingredient list. Report it as unknown.
- "Peeling gel" / "搓泥" products: the visible rolling is polymer pilling, not exfoliated skin. Do not credit it as keratolysis.
- Claims of "deep cleansing", "detox", "pore shrinking" → no mechanism → flag as unsupported.
- A product labelled "换肤" / "刷酸" / "peel" implies a medical action; cosmetic labelling rules prohibit implying medical effect. Flag it, and do not treat the product as a normal cosmetic.
- Enzyme exfoliants without declared activity, pH, or contact time → evidence D; do not credit efficacy.
- AHA with no sun-protection statement → flag (required in China, part of the FDA labelling guidance).
- Do not treat professional-strength concentrations as consumer products. 30% at pH 3.0 belongs in a clinic; scoring it as a daily cosmetic is an error.

---

## 13. Ingredient Quick Reference

**Freely available, effective at cosmetic concentrations**
Glycolic acid (3–6% China-compliant, pH 3.5–4.0) · Lactic acid (5–10%) · Mandelic acid · Gluconolactone · Lactobionic acid · Salicylic acid (0.5–2%) · Betaine salicylate · Urea ≥ 10%

**Gentle / first-line for sensitive skin**
PHA class · Mandelic acid · Betaine salicylate (pairs with the acne spec)

**Requires a declared number to be scored**
Urea (10% threshold changes the mechanism) · Any AHA below 3% (efficacy marginal) · Enzyme blends

**Flag / reduce Safety PS**
Multiple acids + alcohol + fragrance in one formula · Leave-on pH < 3.0 · Salicylic acid in under-3s products · No sunscreen statement on an AHA product

**Not evidence of exfoliation**
Friction claims (rolling beads, brushes, "搓泥") · Charcoal · Plant enzymes without declared activity · "Skin renewal" without a keratolytic active

---

## 14. Sources

| Claim | Source |
| --- | --- |
| AHA ≤ 6.0%, pH ≥ 3.5, sunscreen labelling (China) | 《化妆品安全技术规范》(2015 年版), 国家食品药品监督管理总局, effective 2016-12-01 |
| Salicylic acid 2.0% leave-on / 3.0% rinse-off hair / 0.5% as preservative; under-3s restriction (China) | Same regulation, 表3 序号8 / 表4 序号42; as restated by 广州市市场监督管理局《普通化妆品备案问答（六十二期）》 |
| EU salicylic acid limits (3.0% / 2.0% / 0.5%) | Regulation (EC) No 1223/2009, Annex III No. 98 and Annex V; SCCS opinion SCCS/1601/18 |
| AHA ≤ 10% at pH ≥ 3.5, sunburn alert (US) | FDA, *Guidance for Industry: Labeling for Topically Applied Cosmetic Products Containing Alpha Hydroxy Acids* (2005) |
| Retail ≤ 10% at pH ≥ 3.5; salon ≤ 30% at pH ≥ 3.0 | CIR, *Safety Assessment of Alpha Hydroxy Acids as Used in Cosmetics* (2013) |
| Worst-case AHA assessment at 10% glycolic acid, pH 3.5 | SCCNFP/0799/04, *Evaluation and opinion on alpha-hydroxy acids* |
| Concentration and pH interact: at fixed pH, more acid → more irritation; at fixed concentration, lower pH → more irritation | CIR 2013, discussion of irritation data |
| pH determines free-acid availability and exfoliating effect | 香港消费者委员会, 《去角质洁面产品测试》(2023) |
| "换肤" / "刷酸" claims imply a medical action and are prohibited in cosmetic labelling (China) | 《化妆品标识管理规定》; 上海市消保委 刷酸产品比较试验 (2023) |
