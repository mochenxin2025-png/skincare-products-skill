# Bootstrap Database — Cosmetic Analysis Agent

## Schema (M21)

| Field | Type | Description |
| --- | --- | --- |
| Name | string | Primary INCI name |
| Alias | string[] | Common names, trade names |
| Category | string | Database category |
| Ontology | string | M13 classification |
| Mechanism | string | How it works |
| Primary Function | string | Main role |
| Secondary Function | string[] | Additional roles |
| Evidence Level | A/B/C/D/E | M17 evidence tier |
| Risk Level | Low/Medium/High | Irritation/safety concern |
| Typical Concentration | string | Typical use range (% w/w) |
| Interaction | string[] | Known interactions |
| Photostability | Stable/Unstable/Moderate | Light sensitivity |
| Skin Compatibility | string[] | Suitable skin types |
| Reference | string | Source (DOI or textbook) |

---

## 1. Sunscreen Filter Database (30 entries)

### Physical (Inorganic) Filters

| # | Name | Alias | Mechanism | Primary | Evidence | Risk | Conc. | Photostability | Skin |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Zinc Oxide | ZnO | Reflects + scatters UV; semiconductor band-gap absorption | Broad-spectrum UV filter | A | Low | 5–25% | Stable | All; especially sensitive |
| 2 | Titanium Dioxide | TiO₂ | Reflects + scatters UV; primarily UVB + short UVA | UVB/UVA2 filter | A | Low | 2–25% | Stable (coated); photoactive uncoated | Most; may leave white cast |

### Chemical (Organic) Filters — UVB

| # | Name | Alias | Peak (nm) | Evidence | Risk | Conc. | Photostability |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 3 | Ethylhexyl Methoxycinnamate | Octinoxate, OMC, Eusolex 2292 | 310 (UVB) | B | Medium (coral, endocrine disputed) | 2–10% | Moderate — degrades with avobenzone |
| 4 | Ethylhexyl Triazone | Uvinul T150, EHT | 314 (UVB) | B | Low | 1–5% | Stable |
| 5 | Homosalate | HMS, Eusolex HMS | 306 (UVB) | B | Medium (endocrine disputed) | 5–15% | Moderate |
| 6 | Octisalate | Ethylhexyl Salicylate, ES, Eusolex OS | 305 (UVB) | B | Low | 3–5% | Stable; used as photostabilizer |
| 7 | Octocrylene | OCR, Eusolex OCR | 303 (UVB) | B | Medium (allergen potential) | 2–10% | Stable; excellent photostabilizer for avobenzone |
| 8 | Polysilicone-15 | Parsol SLX | 312 (UVB) | B | Low | 2–10% | Stable; polymeric |
| 9 | Phenylbenzimidazole Sulfonic Acid | Ensulizole, PBSA, Eusolex 232 | 306 (UVB) | B | Low | 1–8% | Moderate; water-soluble |
| 10 | Isoamyl p-Methoxycinnamate | Amiloxate, Neo Heliopan E1000 | 310 (UVB) | B | Low | 2–10% | Moderate |
| 11 | 4-Methylbenzylidene Camphor | 4-MBC, Eusolex 6300, Enzacamene | 300 (UVB) | B | Medium (endocrine) | 1–4% | Stable |
| 12 | Ethylhexyl Dimethyl PABA | Padimate O, Escalol 507 | 311 (UVB) | B | Medium (PABA derivative concern) | 1–8% | Moderate |

### Chemical Filters — UVA

| # | Name | Alias | Peak (nm) | Evidence | Risk | Conc. | Photostability |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 13 | Butyl Methoxydibenzoylmethane | Avobenzone, BMDBM, Parsol 1789, Eusolex 9020 | 357 (UVA) | B | Low | 2–5% | UNSTABLE — requires photostabilizer |
| 14 | Diethylamino Hydroxybenzoyl Hexyl Benzoate | DHHB, Uvinul A Plus | 354 (UVA) | B | Low | 2–10% | Excellent |
| 15 | Disodium Phenyl Dibenzimidazole Tetrasulfonate | Neo Heliopan AP, DPDT | 335 (UVA) | B | Low | 1–10% | Stable; water-soluble |
| 16 | Terephthalylidene Dicamphor Sulfonic Acid | Ecamsule, Mexoryl SX | 345 (UVA) | B | Low | 1–10% | Stable; patented (L'Oréal) |
| 17 | Menthyl Anthranilate | Meradimate | 336 (UVA) | B | Low | 3–5% | Moderate; weak filter |

### Chemical Filters — Broad-Spectrum

| # | Name | Alias | Peak (nm) | Evidence | Risk | Conc. | Photostability |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 18 | Bis-Ethylhexyloxyphenol Methoxyphenyl Triazine | Tinosorb S, Bemotrizinol, BEMT | 310/345 (UVB+UVA) | B | Low | 2–10% | Excellent; photostabilizer |
| 19 | Methylene Bis-Benzotriazolyl Tetramethylbutylphenol | Tinosorb M, Bisoctrizole, MBBT | 305/360 (UVB+UVA) | B | Low | 2–10% | Excellent; hybrid organic particles |
| 20 | Diethylhexyl Butamido Triazone | Iscotrizinol, DBT | 312 (UVB+some UVA) | B | Low | 1–10% | Stable |
| 21 | Drometrizole Trisiloxane | Mexoryl XL, DTS | 303/344 (UVB+UVA) | B | Low | 1–15% | Stable; silicone-compatible |
| 22 | Tris-Biphenyl Triazine | Tinosorb A2B, TBPT | Broad + visible | B | Low | 1–10% | Excellent; also protects visible light |
| 23 | Benzophenone-3 | Oxybenzone, BP-3, Eusolex 4360 | 288/325 (UVB+short UVA) | B | High (endocrine, coral) | 2–6% | Moderate |
| 24 | Benzophenone-4 | Sulisobenzone, BP-4 | 286/324 | B | Low | 5–10% | Stable; water-soluble |
| 25 | Benzophenone-5 | Sulisobenzone Sodium | 286/324 | B | Low | 5–10% | Stable; water-soluble |

### Emerging & Regional

| # | Name | Alias | Notes | Evidence | Risk | Conc. |
| --- | --- | --- | --- | --- | --- | --- |
| 26 | Methoxypropylamino Cyclohexenylidene Ethoxyethylcyanoacetate | Mexoryl 400, MCE | Long UVA (385nm peak); patented L'Oréal | B | Low | 1–5% |
| 27 | Phenylene Bis-Diphenyltriazine | TriAsorB, PBDT | Broad + visible + HEV; Avene/Pierre Fabre | B | Low | 1–5% |
| 28 | Bis-(Diethylaminohydroxybenzoyl Benzoyl) Piperazine | HAA299 | Broad UVA; BASF nanoparticle | B | Low | 1–5% |
| 29 | Ethylhexyl Bis-Isopentylbenzoxazolylphenyl Melamine | - | Broad-spectrum | C | Low | 1–5% |
| 30 | Bisoctrizole (nano) | Tinosorb M nano | Nano form of Tinosorb M | B | Low | 2–10% |

### Key Interactions (Sunscreen)

| Combination | Effect |
| --- | --- |
| Avobenzone + Octocrylene | Photostabilization of avobenzone (Synergy) |
| Avobenzone + Tinosorb S | Photostabilization of avobenzone (Synergy) |
| Avobenzone + Octinoxate | Mutual photodegradation (Conflict) |
| Avobenzone + TiO₂ (uncoated) | Photocatalytic degradation of avobenzone (Antagonism) |
| Avobenzone + Zinc Oxide (uncoated) | Potential avobenzone degradation (Antagonism) |
| Octinoxate + Titanium Dioxide (uncoated) | Photocatalytic degradation (Antagonism) |

---

## 2. Surfactant Database (40 entries)

### Anionic Surfactants

| # | Name | Alias | Mechanism | Irritancy | Risk | Conc. (Cleanser) | Typical pH |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Sodium Lauryl Sulfate | SLS | Strong anionic; high defatting | High | Medium | 5–15% | 6–8 |
| 2 | Sodium Laureth Sulfate | SLES | Anionic; ethoxylated, milder than SLS | Medium | Low-Medium | 5–20% | 6–8 |
| 3 | Ammonium Lauryl Sulfate | ALS | Anionic; similar to SLS | High | Medium | 5–15% | 5–7 |
| 4 | Ammonium Laureth Sulfate | ALES | Anionic; ethoxylated, milder | Medium | Low-Medium | 5–20% | 5–7 |
| 5 | Sodium Cocoyl Isethionate | SCI | Anionic; mild, syndet bar staple | Low | Low | 2–20% | 5–7 |
| 6 | Sodium Lauroyl Sarcosinate | SLSa | Anionic; mild, good foam | Low | Low | 2–10% | 5–7 |
| 7 | Sodium Lauroyl Glutamate | - | Anionic; amino acid based, very mild | Very Low | Low | 2–15% | 5–7 |
| 8 | Sodium Cocoyl Glutamate | - | Anionic; amino acid based | Very Low | Low | 2–15% | 5–7 |
| 9 | Sodium Cocoyl Glycinate | - | Anionic; amino acid based, good foam | Low | Low | 2–15% | 7–9 |
| 10 | Sodium Lauryl Sulfoacetate | SLSA | Anionic; sulfate-free, mild | Low | Low | 2–10% | 5–7 |
| 11 | Disodium Laureth Sulfosuccinate | - | Anionic; very mild, low foam | Very Low | Low | 2–10% | 5–7 |
| 12 | Sodium Lauroyl Methyl Isethionate | SLMI | Anionic; mild, good foam | Low | Low | 2–10% | 5–7 |
| 13 | Sodium Methyl Cocoyl Taurate | SMCT | Anionic; mild, creamy foam | Low | Low | 2–15% | 5–7 |
| 14 | Sodium C14-16 Olefin Sulfonate | - | Anionic; good foam, stable in hard water | Medium | Low-Medium | 2–15% | 5–8 |
| 15 | Potassium Cocoyl Glycinate | - | Anionic; amino acid based | Low | Low | 2–15% | 7–9 |
| 16 | Sodium Cocoamphoacetate | - | Amphoteric; very mild, low foam | Very Low | Low | 2–10% | 5–8 |

### Amphoteric Surfactants

| # | Name | Alias | Mechanism | Irritancy | Risk | Conc. |
| --- | --- | --- | --- | --- | --- | --- |
| 17 | Cocamidopropyl Betaine | CAPB | Amphoteric; viscosity builder, mild foam booster | Low | Low-Medium (allergen) | 2–10% |
| 18 | Cocamidopropyl Hydroxysultaine | - | Amphoteric; mild, good in acidic formulas | Low | Low | 2–8% |
| 19 | Coco-Betaine | - | Amphoteric; mild | Low | Low | 2–8% |
| 20 | Disodium Cocoamphodiacetate | - | Amphoteric; very mild | Very Low | Low | 2–10% |
| 21 | Sodium Cocoamphoacetate | - | Amphoteric; very mild | Very Low | Low | 2–10% |
| 22 | Lauramidopropyl Betaine | - | Amphoteric; mild | Low | Low | 2–8% |

### Nonionic Surfactants

| # | Name | Alias | Mechanism | Irritancy | Risk | Conc. |
| --- | --- | --- | --- | --- | --- | --- |
| 23 | Decyl Glucoside | - | Nonionic; glucose-based, very mild | Very Low | Low | 2–10% |
| 24 | Coco-Glucoside | - | Nonionic; glucose-based, very mild | Very Low | Low | 2–15% |
| 25 | Lauryl Glucoside | - | Nonionic; glucose-based, mild | Low | Low | 2–10% |
| 26 | Caprylyl/Capryl Glucoside | - | Nonionic; glucose-based, very mild | Very Low | Low | 2–8% |
| 27 | PEG-7 Glyceryl Cocoate | - | Nonionic; mild, refatting agent | Low | Low | 1–5% |
| 28 | PEG-40 Hydrogenated Castor Oil | - | Nonionic; solubilizer for fragrance | Low | Low | 0.5–3% |
| 29 | Polysorbate 20 | Tween 20 | Nonionic; solubilizer, emulsifier | Low | Low | 0.5–5% |
| 30 | Polysorbate 80 | Tween 80 | Nonionic; solubilizer, emulsifier | Low | Low | 0.5–5% |
| 31 | Cocamide DEA | - | Nonionic; foam booster, thickener | Medium | Medium (nitrosamine concern) | 1–5% |
| 32 | Cocamide MEA | - | Nonionic; foam booster | Low | Low | 1–5% |
| 33 | Lauryl/Myristyl Polyricinoleate | - | Nonionic; mild | Low | Low | 1–5% |

### Cationic Surfactants (Conditioning — Hair)

| # | Name | Function | Irritancy | Risk | Conc. |
| --- | --- | --- | --- | --- | --- |
| 34 | Cetrimonium Chloride | Conditioning; anti-static | Medium | Low-Medium | 0.5–3% |
| 35 | Behentrimonium Chloride | Conditioning; excellent detangling | Low | Low | 1–5% |
| 36 | Stearamidopropyl Dimethylamine | Conditioning (pH-dependent) | Low | Low | 1–5% |
| 37 | Quaternium-87 | Conditioning; heat protection | Low | Low | 0.5–3% |
| 38 | Distearyldimonium Chloride | Conditioning; heavy | Low | Low | 1–5% |
| 39 | Guar Hydroxypropyltrimonium Chloride | Conditioning polymer; deposition aid | Low | Low | 0.1–1% |
| 40 | Polyquaternium-10 | Conditioning polymer; deposition aid | Low | Low | 0.1–1% |

### Surfactant Mildness Ranking

```
Most Gentle (for sensitive/barrier-damaged skin):
  Decyl Glucoside ≈ Coco-Glucoside ≈ Sodium Cocoyl Glutamate
  > Sodium Cocoyl Isethionate > Sodium Lauroyl Sarcosinate
  > Cocamidopropyl Betaine > Sodium Laureth Sulfate
  > Sodium Lauryl Sulfate (harshest)
```

---

## 3. Preservative Database (20 entries)

Schema conforming to M21. Risk is preservative-specific safety concern.

| # | Name | Mechanism | Risk | Conc. | Effective pH | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Phenoxyethanol | Membrane disruption | Low | 0.5–1.0% | 3–10 | Broad-spectrum; often paired with booster |
| 2 | Ethylhexylglycerin | Membrane disruption (booster); humectant | Low | 0.1–1.0% | 3–10 | Boosts phenoxyethanol; multifunctional |
| 3 | Potassium Sorbate | Inhibits mold/yeast enzymes | Low | 0.1–0.5% | <6.0 | Weak vs bacteria; needs companion |
| 4 | Sodium Benzoate | Inhibits microbial enzymes | Low | 0.1–0.5% | <5.5 | Weak vs fungi; needs companion; avoid with ascorbic acid |
| 5 | Benzyl Alcohol | Membrane disruption | Medium (allergen) | 0.5–1.0% | 3–10 | Fragrance allergen; must be declared in EU |
| 6 | Sodium Dehydroacetate | Enzyme inhibition | Low | 0.1–0.5% | 3–7 | Good vs fungi; moderate vs bacteria |
| 7 | Chlorphenesin | Unknown (likely enzyme inhibition) | Medium | 0.1–0.5% | 3–10 | Broad-spectrum; less common |
| 8 | Methylparaben | Enzyme inhibition | Medium | 0.1–0.3% | 3–10 | Short-chain paraben; lowest concern |
| 9 | Propylparaben | Enzyme inhibition | Medium-High | 0.1–0.3% | 3–10 | Long-chain paraben; EU restricted |
| 10 | Methylisothiazolinone | Enzyme inhibition (potent) | HIGH | 0.005–0.01% | 3–8 | Potent sensitizer; banned in leave-on EU |
| 11 | Methylchloroisothiazolinone / Methylisothiazolinone (3:1) | Enzyme inhibition (potent) | HIGH | 0.0005–0.0015% | 3–8 | Kathon CG; banned in leave-on EU |
| 12 | DMDM Hydantoin | Formaldehyde release | Medium | 0.1–0.6% | 3–10 | Formaldehyde releaser; decreasing usage |
| 13 | Imidazolidinyl Urea | Formaldehyde release | Medium | 0.1–0.5% | 3–9 | Formaldehyde releaser; weak vs fungi |
| 14 | Iodopropynyl Butylcarbamate | Enzyme inhibition (potent) | Medium | 0.005–0.05% | 3–10 | Potent vs fungi; restricted concentration |
| 15 | Sodium Hydroxymethylglycinate | Formaldehyde release | Medium | 0.1–0.5% | 6–12 | Formaldehyde releaser; alkaline optimal |
| 16 | Caprylyl Glycol | Membrane disruption (booster); humectant | Low | 0.3–1.0% | 3–10 | Multifunctional; often paired with phenoxyethanol |
| 17 | Pentylene Glycol | Membrane disruption (booster); humectant | Low | 1–5% | 3–10 | Multifunctional; higher conc. needed |
| 18 | Levulinic Acid | pH-dependent acidification | Low | 0.5–2% | <5.5 | Natural-aligned; needs companion |
| 19 | Sorbic Acid | pH-dependent; inhibits molds | Low | 0.1–0.3% | <6.0 | Same as potassium sorbate (acid form) |
| 20 | Benzoic Acid | pH-dependent; inhibits microbes | Low | 0.1–0.5% | <5.5 | Same as sodium benzoate (acid form) |

### Preservative System Assessment Rules

- A single preservative is rarely adequate. Evaluate the SYSTEM.
- "Preservative-free" claims often use multifunctional ingredients (caprylyl glycol, pentylene glycol) at higher concentrations — functionally preserved.
- Parabens: short-chain (methyl-, ethyl-) have lower concern than long-chain (propyl-, butyl-).
- Formaldehyde releasers: acceptable in rinse-off; avoid in leave-on and aerosol products.
- MIT/MCI: avoid entirely in leave-on; restrict in rinse-off.

---

## 4. Humectant Database (20 entries)

| # | Name | Mechanism | MW | Evidence | Typical Conc. | Skin |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Glycerin | Hygroscopic; draws water into stratum corneum | 92 Da | A | 1–30% | All; gold standard |
| 2 | Butylene Glycol | Hygroscopic; light feel | 90 Da | B | 1–10% | All |
| 3 | Propylene Glycol | Hygroscopic; penetration enhancer | 76 Da | B | 1–10% | Most; may irritate sensitive at high % |
| 4 | Propanediol | Hygroscopic; natural-aligned propylene glycol alternative | 76 Da | B | 1–15% | All |
| 5 | Pentylene Glycol | Hygroscopic + antimicrobial booster | 104 Da | B | 1–5% | All |
| 6 | Hexylene Glycol | Hygroscopic + antimicrobial booster | 118 Da | B | 1–5% | All |
| 7 | Caprylyl Glycol | Hygroscopic + antimicrobial booster | 146 Da | B | 0.3–1% | All; primarily preservative booster |
| 8 | Sodium Hyaluronate | High MW: surface film; binds 1000× water | 500k–2M Da | B | 0.01–1% | All |
| 9 | Hydrolyzed Hyaluronic Acid | Low MW: deeper penetration | 10k–100k Da | B | 0.01–1% | All; may be pro-inflammatory in some studies |
| 10 | Sodium Acetylated Hyaluronate | Modified HA; longer retention on skin | 100k Da | B | 0.01–0.5% | All; superior substantivity |
| 11 | Sodium PCA | Natural Moisturizing Factor component | 137 Da | B | 0.5–5% | All; part of NMF |
| 12 | Sodium Lactate | Natural Moisturizing Factor component | 112 Da | B | 0.5–5% | All; part of NMF; pH-dependent |
| 13 | Urea | NMF; keratolytic at >5%, humectant at ≤3% | 60 Da | B | 1–10% | Dry, barrier-damaged; may sting at >5% |
| 14 | Trehalose | Cell protection (anhydrobiosis); humectant | 342 Da | B | 1–5% | All; excellent for sensitive |
| 15 | Betaine | Osmolyte; cell protection; humectant | 117 Da | B | 1–5% | All; natural-aligned |
| 16 | Sorbitol | Humectant; similar to glycerin but less sticky | 182 Da | B | 1–5% | All |
| 17 | Panthenol | Pro-Vitamin B5; humectant + wound healing | 205 Da | B | 0.5–5% | All; excellent for barrier repair |
| 18 | Erythritol | Sugar alcohol; humectant + cooling effect | 122 Da | C | 1–5% | All |
| 19 | Xylitol | Sugar alcohol; humectant | 152 Da | C | 1–5% | All |
| 20 | Polyglutamic Acid | High MW polypeptide; superior water binding to HA | >1M Da | C | 0.05–1% | All |

### Humectant Layering Strategy (formulation context)

```
High-humidity environment: Glycerin + light humectants (butylene glycol) sufficient
Low-humidity environment: Glycerin alone may draw water FROM skin → pair with occlusives
Barrier-damaged skin: NMF components (PCA, lactate, urea) + panthenol
Sensitive skin: Trehalose + betaine — cell-protective, non-irritating
```

---

## 5. Risk Ingredient Database (30 entries)

Focused on ingredients where safety evaluation directly impacts scoring.

| # | Name | Risk Type | Severity | Mechanism of Harm | Regulatory Status | Skin Impact |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Methylisothiazolinone | Sensitizer | High | Type IV hypersensitivity; potent contact allergen | Banned in leave-on (EU); restricted rinse-off | Allergic contact dermatitis |
| 2 | Methylchloroisothiazolinone | Sensitizer | High | Same as MIT; often combined 3:1 (MCI:MIT) | Banned leave-on (EU) | Allergic contact dermatitis |
| 3 | Formaldehyde | Carcinogen; sensitizer | Prohibited | IARC Group 1 carcinogen; potent sensitizer | Banned in cosmetics (EU, Japan, Canada) | Cancer; dermatitis |
| 4 | DMDM Hydantoin | Formaldehyde releaser | Medium | Slowly releases formaldehyde over product lifetime | Restricted | Cumulative sensitization |
| 5 | Quaternium-15 | Formaldehyde releaser | Medium | Most potent formaldehyde releaser | Restricted | Cumulative sensitization |
| 6 | Triclosan | Endocrine; environmental | High | Thyroid hormone disruption; antibiotic resistance; bioaccumulation | Banned OTC (FDA 2016); restricted (EU) | No direct acute skin harm |
| 7 | Triclocarban | Endocrine; environmental | High | Similar to triclosan | Banned OTC (FDA 2016) | No direct acute skin harm |
| 8 | Oxybenzone (Benzophenone-3) | Endocrine; environmental | High | Estrogenic activity (in vitro); coral bleaching; high skin penetration | Banned (Hawaii, Palau, Key West, etc.) | Photoallergy potential |
| 9 | Octinoxate | Environmental | Medium | Coral bleaching; some endocrine data (disputed) | Banned (Hawaii, Palau, etc.) | Low skin risk |
| 10 | Homosalate | Endocrine (disputed) | Medium | In vitro estrogenic/anti-androgenic activity | Under review (EU SCCS) | Low skin risk |
| 11 | Propylparaben | Endocrine (disputed) | Medium | Weak estrogenic activity in vitro; but rapid skin metabolism | EU: 0.14% limit (single); banned in some leave-on | Very low actual skin risk |
| 12 | Butylparaben | Endocrine (disputed) | Medium-High | Longer chain = higher estrogenic potential | EU: banned in leave-on for children <3; restricted | Very low actual skin risk |
| 13 | Hydroquinone | Cytotoxicity; ochronosis | High | Melanocyte toxicity; exogenous ochronosis with chronic use | Rx-only (US, EU); OTC ban in many regions | Hyperpigmentation rebound; ochronosis |
| 14 | Mercury (and compounds) | Neurotoxic | Prohibited | CNS damage; nephrotoxicity; transdermal absorption | Banned globally in cosmetics | Systemic poisoning |
| 15 | Corticosteroids (hidden in cosmetics) | Skin atrophy; systemic | Prohibited | Topical steroid withdrawal; telangiectasia; striae | Rx-only globally; illegal in OTC cosmetics | Steroid-dependent dermatitis |
| 16 | Sodium Lauryl Sulfate (SLS) — high concentration | Irritant | Medium | Disrupts lipid bilayer; denatures proteins; increases TEWL | Not banned; patch test standard irritant | Barrier disruption; dryness; burning |
| 17 | Alcohol Denat. (high %, leave-on) | Barrier disruption | Medium | Lipid extraction from stratum corneum; increased TEWL | Not banned | Dryness; irritation; barrier damage |
| 18 | Essential Oils (high conc.) | Irritant; phototoxic | Medium | Contain furanocoumarins (phototoxic); terpenes (oxidize to allergens) | IFRA restricted | Irritation; phototoxic reaction |
| 19 | Bergamot Oil (expressed) | Phototoxic | High | Contains bergapten (5-MOP); potent phototoxin | IFRA restricted; bergapten-free forms available | Severe phototoxic burns |
| 20 | Polyethylene (microbeads) | Environmental | Prohibited (rinse-off) | Non-biodegradable; enters aquatic food chain | Banned rinse-off (US Microbead-Free Waters Act 2015; EU pending) | No skin harm |
| 21 | Talc (non-certified) | Asbestos contamination | Medium | Natural talc deposits may contain asbestos fibers | Not banned; asbestos-testing required | Mesothelioma risk (inhalation of powder) |
| 22 | BHA (Butylated Hydroxyanisole) | Carcinogen (potential) | Medium | IARC Group 2B (possible human carcinogen) | Restricted (EU); not banned | Low actual risk at cosmetic levels |
| 23 | PEG Compounds (>20 EO units) | 1,4-Dioxane contamination | Low-Medium | Manufacturing byproduct; IARC Group 2B | Vacuum stripping removes; reputable manufacturers test | Low actual risk |
| 24 | Sodium Laureth Sulfate (SLES) | 1,4-Dioxane contamination | Low-Medium | Same as PEG; ethoxylation byproduct | Vacuum stripping standard | Low risk (milder than SLS) |
| 25 | Ethanolamines (DEA, MEA, TEA) | Nitrosamine formation | Medium | Can react with nitrosating agents to form nitrosamines (carcinogenic) | Restricted; avoid with nitrosating preservatives | Low direct risk |
| 26 | Retinol (high %, without sun protection guidance) | Photosensitivity | Medium | Increases skin sensitivity to UV; not harmful itself but increases sunburn risk | Concentration limits (EU: 0.3% body, 0.05% hand/face leave-on) | Sun sensitivity; peeling |
| 27 | Hydroquinone Monomethyl Ether (Mequinol) | Depigmentation | High | Permanent depigmentation at high concentrations | Rx in some regions; banned OTC | Confetti depigmentation |
| 28 | Kojic Acid (high %, unstable) | Sensitizer | Medium | Sensitization with prolonged use; unstable → degradation products may be more sensitizing | Restricted concentration (1% recommended max in leave-on) | Allergic contact dermatitis |
| 29 | Coal Tar | Carcinogen; photosensitizer | High | IARC Group 1 carcinogen; PAH content; photosensitizing | Rx or OTC depending on concentration and region | Skin cancer risk (occupational); photosensitivity |
| 30 | Nanoparticle TiO₂ (uncoated, spray) | Inhalation risk | Medium | IARC Group 2B when inhaled (occupational); safe on intact skin | EU: not allowed in sprayable formulations; coating required | No skin harm; inhalation concern only |

---

## Database Cross-Reference Matrix

```
Ingredient            Sunscreen  Surfactant  Preservative  Humectant  Risk
────────────────────  ─────────  ──────────  ────────────  ─────────  ────
Ethylhexylglycerin       -           -            ✅           ✅        -
Caprylyl Glycol          -           -            ✅           ✅        -
Pentylene Glycol         -           -            ✅           ✅        -
Sodium Laureth Sulfate   -           ✅           -            -         ✅
Oxybenzone               ✅          -            -            -         ✅
Panthenol                -           -            -            ✅        -
Glycerin                 -           -            -            ✅        -
```

---

## Version & Expansion Notes

- v1.0 bootstrap — 140 entries across 5 databases
- Next expansion: Emollient database, Silicone database, Plant extract database
- All entries follow M21 schema
- Fields marked "-" are awaiting population in subsequent versions
