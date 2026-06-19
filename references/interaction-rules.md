# Ingredient Interaction Rules Database v1.0

## Overview

This database defines known cosmetic ingredient interactions for M16 (Interaction Engine). Each rule is tagged with an evidence level and must not be applied unless the interaction is confirmed. Absence of a rule = "Independent" (1.00), never "Synergy" or "Conflict" by default.

---

## 1. Antioxidant Synergies

### Rule 1: Ascorbic Acid + Tocopherol (Vitamin C + Vitamin E)
| Field | Value |
| --- | --- |
| **Type** | Synergy |
| **Evidence** | A (Multiple clinical studies) |
| **Mechanism** | Vitamin E quenches lipid peroxide radicals; Vitamin C regenerates oxidized Vitamin E back to active form. This creates a redox cycle that extends antioxidant protection. |
| **IM** | 1.10 |
| **Conditions** | Both must be present at effective concentrations. L-Ascorbic Acid ≥ 5% optimal; Tocopherol ≥ 0.5%. |
| **Reference** | Lin et al., J Invest Dermatol (2003); Pinnell et al., Dermatol Surg (2005) |

### Rule 2: Ascorbic Acid + Ferulic Acid
| Field | Value |
| --- | --- |
| **Type** | Synergy |
| **Evidence** | A |
| **Mechanism** | Ferulic acid stabilizes ascorbic acid against photo-oxidation and doubles its photoprotective efficacy. Also stabilizes the formula itself against oxidation. |
| **IM** | 1.10 |
| **Conditions** | Ferulic acid at 0.5% typical; ascorbic acid 10–20%. |
| **Reference** | Lin et al., J Invest Dermatol (2005) |

### Rule 3: Ascorbic Acid + Tocopherol + Ferulic Acid (CEF Triple)
| Field | Value |
| --- | --- |
| **Type** | Synergy (compounding) |
| **Evidence** | A |
| **Mechanism** | Triple combination provides 8× photoprotection vs. any single agent alone. Ferulic stabilizes both C and E. |
| **IM** | 1.15 |
| **Conditions** | All three present at effective levels (C 10–20%, E ≥0.5%, Ferulic 0.5%). |
| **Reference** | SkinCeuticals CE Ferulic patents; Lin et al. (2005). |

### Rule 4: Ascorbyl Glucoside + Tocopherol
| Field | Value |
| --- | --- |
| **Type** | Synergy (mild) |
| **Evidence** | C |
| **Mechanism** | Stabilized Vitamin C derivative releases ascorbic acid gradually via skin glucosidases; still participates in E-regeneration cycle but with lower peak concentration. |
| **IM** | 1.05 |
| **Conditions** | Ascorbyl glucoside ≥ 2%; tocopherol ≥ 0.5%. |

---

## 2. Retinoid Interactions

### Rule 5: Retinol + Niacinamide
| Field | Value |
| --- | --- |
| **Type** | Synergy |
| **Evidence** | B |
| **Mechanism** | Niacinamide improves barrier function and reduces irritation, making retinol more tolerable. They act on complementary pathways (retinol: RAR/RXR nuclear receptors; niacinamide: NAD+ pathways). No antagonism. |
| **IM** | 1.05 |
| **Conditions** | Both at effective concentrations. Retinol 0.1–1%; Niacinamide 2–10%. |
| **Note** | Historical concern about niacinamide "deactivating" retinol is not supported by evidence. They work well together. |
| **Reference** | Draelos et al., J Drugs Dermatol (2021) |

### Rule 6: Retinol + AHA (Glycolic Acid / Lactic Acid)
| Field | Value |
| --- | --- |
| **Type** | Antagonism (pH conflict) |
| **Evidence** | B |
| **Mechanism** | Retinol requires skin esterases to convert to retinoic acid; these esterases are pH-sensitive. AHA lowers skin surface pH, which may alter retinol conversion kinetics. Additionally, simultaneous use increases irritation additively. |
| **IM** | 0.85 |
| **Recommendation** | Separate application (AM/PM) or alternate nights. If in same formula, pH must be carefully buffered (5.0–6.0). |
| **Reference** | Kligman et al., J Am Acad Dermatol (1998) |

### Rule 7: Retinol + Benzoyl Peroxide
| Field | Value |
| --- | --- |
| **Type** | Conflict |
| **Evidence** | B |
| **Mechanism** | Benzoyl peroxide is a strong oxidizer that directly degrades retinol on contact. In the same formula, retinol is rapidly destroyed. On skin in layered use, oxidation still occurs at the interface. |
| **IM** | 0.70 |
| **Recommendation** | Never in same formula. If both used: BP in AM cleanser, retinol PM — or separate fully. |
| **Reference** | Martin et al., J Am Acad Dermatol (2008) |

### Rule 8: Retinal + Bakuchiol
| Field | Value |
| --- | --- |
| **Type** | Independent (no interaction) |
| **Evidence** | C |
| **Mechanism** | Bakuchiol acts via different molecular targets than retinoids (primarily retinoic acid receptor-independent pathways). They do not compete or degrade each other. Additive anti-aging benefit possible but not synergistic. |
| **IM** | 1.00 |
| **Reference** | Chaudhuri et al., Br J Dermatol (2019); Dhaliwal et al., Br J Dermatol (2019) |

---

## 3. Acid Interactions (AHA / BHA / PHA)

### Rule 9: Glycolic Acid + Salicylic Acid
| Field | Value |
| --- | --- |
| **Type** | Synergy (complementary) |
| **Evidence** | B |
| **Mechanism** | Glycolic acid (AHA, water-soluble) exfoliates the surface; salicylic acid (BHA, lipid-soluble) penetrates pores. They target different layers. No chemical conflict. |
| **IM** | 1.05 |
| **Caution** | Additive irritation potential. Combined concentration should be assessed carefully for sensitive skin. |
| **Reference** | Comite de Evaluación, J Cosmet Dermatol (2017) |

### Rule 10: Salicylic Acid + Niacinamide
| Field | Value |
| --- | --- |
| **Type** | Independent (pH caution) |
| **Evidence** | C |
| **Mechanism** | Salicylic acid requires low pH (3.0–4.0) for optimal activity as BHA. Niacinamide is stable and active at pH 5.0–7.0. If formulated at low pH, niacinamide may partially hydrolyze to nicotinic acid (causes flushing). |
| **IM** | 1.00 (1.00 if pH ≥ 5.0; 0.90 if pH < 4.5 due to niacinamide hydrolysis risk) |
| **Recommendation** | Formulate at pH ≥ 5.0, or use non-acid form of salicylic acid (e.g., betaine salicylate). |
| **Reference** | Matts et al., Int J Cosmet Sci (2011) |

### Rule 11: AHA + PHA Combination
| Field | Value |
| --- | --- |
| **Type** | Synergy (tolerance enhancement) |
| **Evidence** | B |
| **Mechanism** | PHA (gluconolactone, lactobionic acid) has a larger molecular structure → slower penetration → less stinging. When combined with AHA, PHA provides antioxidant and humectant benefits while buffering AHA irritation. |
| **IM** | 1.05 |
| **Reference** | Green et al., Dermatol Surg (2001) |

### Rule 12: Citric Acid (high %) + Any pH-Sensitive Active
| Field | Value |
| --- | --- |
| **Type** | Antagonism (pH) |
| **Evidence** | B |
| **Mechanism** | Citric acid is a stronger AHA than often recognized. At ≥ 5%, it drives pH low enough to destabilize: peptides (hydrolysis), some Vit C derivatives, and pH-sensitive preservatives (potassium sorbate ineffective above pH 6, but citric acid pushes the OTHER direction). |
| **IM** | 0.90 |
| **Recommendation** | Check pH of final formula against stability range of each active. |
| **Reference** | General cosmetic formulation textbooks |

---

## 4. Niacinamide Combinations

### Rule 13: Niacinamide + N-Acetyl Glucosamine (NAG)
| Field | Value |
| --- | --- |
| **Type** | Synergy |
| **Evidence** | B |
| **Mechanism** | Both are tyrosinase inhibitors via different mechanisms. Together they show greater reduction in hyperpigmentation than either alone. |
| **IM** | 1.10 |
| **Reference** | Bissett et al., J Cosmet Dermatol (2007); Kimball et al., J Drugs Dermatol (2010) |

### Rule 14: Niacinamide + Tranexamic Acid
| Field | Value |
| --- | --- |
| **Type** | Synergy |
| **Evidence** | B |
| **Mechanism** | Niacinamide inhibits melanosome transfer; tranexamic acid inhibits the plasmin/plasminogen pathway that triggers melanogenesis after UV/inflammation. Complementary mechanisms with no chemical conflict. |
| **IM** | 1.05 |
| **Reference** | Maeda et al., J Dermatol Sci (2007); Hakozaki et al., Br J Dermatol (2002) |

### Rule 15: Niacinamide + Kojic Acid
| Field | Value |
| --- | --- |
| **Type** | Independent |
| **Evidence** | C |
| **Mechanism** | Different mechanisms (tyrosinase inhibitor vs melanosome transfer inhibitor). No known synergy or antagonism. Kojic acid stability concerns are independent of niacinamide presence. |
| **IM** | 1.00 |
| **Reference** | Formulation textbooks |

---

## 5. Peptide Interactions

### Rule 16: Copper Tripeptide-1 + Ascorbic Acid
| Field | Value |
| --- | --- |
| **Type** | Conflict |
| **Evidence** | C |
| **Mechanism** | Ascorbic acid can chelate copper ions from the peptide complex, potentially inactivating both. Copper also catalyzes ascorbic acid oxidation. |
| **IM** | 0.75 |
| **Recommendation** | Separate application times (AM/PM split recommended). |
| **Reference** | In vitro compatibility studies |

### Rule 17: Matrixyl Peptides + Retinol
| Field | Value |
| --- | --- |
| **Type** | Synergy |
| **Evidence** | B |
| **Mechanism** | Retinol stimulates collagen via RAR/RXR nuclear receptors; matrixyl peptides (Palmitoyl Pentapeptide-4) stimulate collagen via matrikine signaling. Different pathways; no chemical conflict; complementary effects on ECM remodeling. |
| **IM** | 1.10 |
| **Reference** | Robinson et al., Int J Cosmet Sci (2005); Robinson et al., J Cosmet Dermatol (2008) |

### Rule 18: Acetyl Hexapeptide-8 (Argireline) + Any Strong Acid
| Field | Value |
| --- | --- |
| **Type** | Antagonism |
| **Evidence** | C |
| **Mechanism** | Peptide hydrolysis is accelerated at low pH. Strong AHA formulations (pH < 3.5) can degrade Argireline before meaningful skin penetration occurs. |
| **IM** | 0.85 |
| **Recommendation** | Formulate at pH ≥ 5.0; or use peptide in separate step. |
| **Reference** | Peptide stability studies |

---

## 6. pH-Dependent Interactions

### Rule 19: Ascorbic Acid (L-AA) Requires pH < 3.5
| Field | Value |
| --- | --- |
| **Type** | Formulation Constraint |
| **Evidence** | A |
| **Mechanism** | L-Ascorbic acid is only stable and skin-permeable at pH < 3.5 (pKa = 4.17). At higher pH, it ionizes and cannot penetrate the stratum corneum; also rapidly oxidizes. |
| **IM** | If pH > 4.5 with L-AA → reduce Core Effectiveness PS for Vitamin C by 0.50. |
| **Reference** | Pinnell et al., Dermatol Surg (2001) |

### Rule 20: Sodium Ascorbyl Phosphate Requires pH ~7
| Field | Value |
| --- | --- |
| **Type** | Formulation Constraint |
| **Evidence** | B |
| **Mechanism** | SAP is a stable Vitamin C ester designed for neutral pH. At acidic pH, it may hydrolyze prematurely. |
| **IM** | If pH < 4.5 with SAP as main Vit C → flag formulation mismatch. Do not penalize PS. |
| **Reference** | Stabilized Vitamin C derivative literature |

### Rule 21: Potassium Sorbate + Low-pH Formula + Ascorbic Acid
| Field | Value |
| --- | --- |
| **Type** | Conflict |
| **Evidence** | B |
| **Mechanism** | At low pH (ascorbic acid formulas, pH < 3.5), potassium sorbate can form sorbic acid which reacts with ascorbic acid, potentially generating oxidative degradation products. |
| **IM** | 0.80 |
| **Recommendation** | Use alternative preservative system in low-pH Vitamin C serums. |
| **Reference** | Preservative compatibility studies |

---

## 7. Preservative & Stability Interactions

### Rule 22: Phenoxyethanol + Ethylhexylglycerin
| Field | Value |
| --- | --- |
| **Type** | Synergy |
| **Evidence** | B |
| **Mechanism** | Ethylhexylglycerin acts as a preservative booster by disrupting microbial membranes, enhancing phenoxyethanol penetration into microbes. Also provides humectant function. |
| **IM** | Not scored (preservative system evaluation; not efficacy). Affects Architecture +0.05 if present. |
| **Reference** | Euxyl PE 9010 literature |

### Rule 23: EDTA + Phenoxyethanol
| Field | Value |
| --- | --- |
| **Type** | Synergy |
| **Evidence** | B |
| **Mechanism** | EDTA chelates divalent cations (Mg²⁺, Ca²⁺) that stabilize gram-negative bacterial outer membranes, making them more susceptible to phenoxyethanol. Broadens preservative spectrum. |
| **IM** | Not scored. Affects Architecture +0.03 if both present. |
| **Reference** | Preservative formulation textbooks |

### Rule 24: Multiple Formaldehyde Releasers
| Field | Value |
| --- | --- |
| **Type** | Conflict (cumulative risk) |
| **Evidence** | B |
| **Mechanism** | Formaldehyde release is cumulative. If 2+ formaldehyde releasers are present (e.g., DMDM Hydantoin + Imidazolidinyl Urea), total formaldehyde burden may exceed safety thresholds despite each being within individual limits. |
| **IM** | 0.85 (safety dimension penalty) |
| **Reference** | EU SCCS opinions on formaldehyde releasers |

---

## 8. Surfactant & Cleanser Interactions

### Rule 25: SLS + SLES Combination
| Field | Value |
| --- | --- |
| **Type** | Synergy (mildness improvement) |
| **Evidence** | B |
| **Mechanism** | SLES is ethoxylated SLS — it has lower critical micelle concentration and lower protein denaturation. Blending SLS with SLES reduces the overall irritancy of the surfactant system while maintaining foam. |
| **IM** | 1.05 (Safety dimension — reduced irritation vs. SLS alone) |
| **Reference** | Ananthapadmanabhan et al., J Soc Cosmet Chem (1998) |

### Rule 26: Anionic + Amphoteric Surfactant
| Field | Value |
| --- | --- |
| **Type** | Synergy |
| **Evidence** | A |
| **Mechanism** | Amphoteric surfactants (e.g., Cocamidopropyl Betaine) form mixed micelles with anionics (SLS, SLES), reducing the charge density of micelles → lower protein denaturation → less skin irritation. Also improves foam quality. |
| **IM** | 1.10 (Safety dimension) |
| **Reference** | Rhein et al., Surfactants in Cosmetics (1997) |

### Rule 27: Anionic + Nonionic Surfactant
| Field | Value |
| --- | --- |
| **Type** | Synergy (mildness) |
| **Evidence** | B |
| **Mechanism** | Nonionics (Decyl Glucoside, Coco-Glucoside) dilute the charge density of anionic micelles, reducing irritancy. Also improve foam creaminess. |
| **IM** | 1.05 (Safety dimension) |
| **Reference** | Surfactant chemistry textbooks |

---

## 9. Sunscreen-Specific Interactions

(Cross-reference with bootstrap-database.md §1 — Key Interactions table)

### Rule 28: Avobenzone + Octocrylene
| Field | Value |
| --- | --- |
| **Type** | Synergy (photostabilization) |
| **Evidence** | A |
| **Mechanism** | Octocrylene acts as a triplet-state quencher for avobenzone, preventing its photodegradation. Avobenzone alone photodegrades ~50% in 1 hour of sunlight; with octocrylene, degradation is < 5%. |
| **IM** | 1.10 (UV Protection dimension) |

### Rule 29: Avobenzone + Octinoxate
| Field | Value |
| --- | --- |
| **Type** | Conflict |
| **Evidence** | A |
| **Mechanism** | Octinoxate and avobenzone undergo a [2+2] photocycloaddition reaction under UV, forming non-UV-absorbing products. Both filters are destroyed. |
| **IM** | 0.70 (UV Protection dimension) |
| **Recommendation** | Never formulate together without a stabilizing system (e.g., Tinosorb S encapsulation). Best practice: avoid combination entirely. |

### Rule 30: Avobenzone + Tinosorb S
| Field | Value |
| --- | --- |
| **Type** | Synergy (stabilization + broadening) |
| **Evidence** | A |
| **Mechanism** | Tinosorb S stabilizes avobenzone via triplet quenching + broadens spectrum into UVA. Also enables avobenzone to be safely paired with octinoxate when Tinosorb S is present at sufficient concentration (≥3%). |
| **IM** | 1.10 (UV Protection dimension) |

---

## 10. Summary Matrix

```
                     Synergy (IM > 1.00)        Conflict (IM < 0.90)
                     ──────────────────────      ──────────────────────
Antioxidant          C+E, C+Ferulic, CEF triple  —
Retinoid             Retinol+Niacinamide         Retinol+AHA, Retinol+BP
Acid                 AHA+BHA, AHA+PHA            Salicylic+Niacinamide (low pH)
Niacinamide          +NAG, +Tranexamic Acid      —
Peptide              Matrixyl+Retinol            Cu-Peptide+Ascorbic Acid
                                                   Argireline+strong acid
Sunscreen            Avo+Octocrylene             Avo+Octinoxate
                     Avo+Tinosorb S
Surfactant           SLS+SLES, Anionic+Ampho     —
Preservative         Phenoxy+Ethylhexylglycerin  Multiple formaldehyde releasers
                     EDTA+Phenoxy
```

---

## 11. Interaction Engine Application Rules

1. **Only evaluate pairs where both ingredients are present** in the ingredient list.
2. **Only apply rules with Evidence ≥ C** to the scoring calculation. Rules with Evidence D or E are informative only (report, don't score).
3. **IM is applied per dimension** — an interaction tagged for "Safety" only affects the Safety dimension score.
4. **Multiple interactions multiply** — IM = IM₁ × IM₂ × ... × IMₙ, capped at [0.50, 1.20].
5. **No rule = Independent** — IM = 1.00. Never fabricate interactions.
6. **Report all found interactions** — even those not affecting scoring (preservative synergies) should appear in the report.
