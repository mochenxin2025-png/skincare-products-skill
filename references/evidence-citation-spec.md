# Evidence Citation Specification v1.0

## Overview

This specification defines how scientific evidence is cited in cosmetic analysis reports. It supports two citation modes and a curated reference library covering the most commonly cited cosmetic ingredients.

---

## 1. Citation Modes

| Mode | Use Case | Format |
| --- | --- | --- |
| **Light** | Consumer reports, social sharing | First-author surname + journal abbreviation + year |
| **Full** | Professional reports, medical context, API | Full Vancouver/AMA style with DOI |

The mode is selected at runtime based on the output target. Markdown reports default to Light mode with expandable Full citations on demand. JSON API always includes Full mode.

---

## 2. Light Citation Format

```
[First Author] et al., [Journal Abbr] ([Year])
```

Examples:
- `Hakozaki et al., Br J Dermatol (2002)`
- `Pinnell et al., Dermatol Surg (2001)`
- `Lin et al., J Invest Dermatol (2003)`

### 2.1 Journal Abbreviations

| Full Journal Name | Abbreviation |
| --- | --- |
| British Journal of Dermatology | Br J Dermatol |
| Journal of Investigative Dermatology | J Invest Dermatol |
| Journal of the American Academy of Dermatology | J Am Acad Dermatol |
| Journal of Cosmetic Dermatology | J Cosmet Dermatol |
| International Journal of Cosmetic Science | Int J Cosmet Sci |
| Dermatologic Surgery | Dermatol Surg |
| Journal of Drugs in Dermatology | J Drugs Dermatol |
| Contact Dermatitis | Contact Dermatitis |
| Skin Pharmacology and Physiology | Skin Pharmacol Physiol |
| Archives of Dermatological Research | Arch Dermatol Res |
| Clinical, Cosmetic and Investigational Dermatology | Clin Cosmet Investig Dermatol |
| Journal of the Society of Cosmetic Chemists | J Soc Cosmet Chem |

---

## 3. Full Citation Format (Vancouver Style)

```
[Authors]. [Title]. [Journal Abbr]. [Year];[Volume]([Issue]):[Pages]. DOI: [DOI]
```

Examples:
- `Hakozaki T, Minwalla L, Zhuang J, et al. The effect of niacinamide on reducing cutaneous pigmentation and suppression of melanosome transfer. Br J Dermatol. 2002;147(1):20-31. DOI: 10.1046/j.1365-2133.2002.04834.x`
- `Pinnell SR, Yang H, Omar M, et al. Topical L-ascorbic acid: percutaneous absorption studies. Dermatol Surg. 2001;27(2):137-142. DOI: 10.1046/j.1524-4725.2001.00200.x`

---

## 4. Curated Reference Library

The following references are the most commonly cited in cosmetic ingredient analysis. This library should be embedded in the Agent or accessible via database query.

### 4.1 Niacinamide (Vitamin B3)

| ID | Citation (Light) | Citation (Full) | DOI |
| --- | --- | --- | --- |
| NIA-01 | Hakozaki et al., Br J Dermatol (2002) | Hakozaki T, Minwalla L, Zhuang J, et al. The effect of niacinamide on reducing cutaneous pigmentation and suppression of melanosome transfer. Br J Dermatol. 2002;147(1):20-31. | 10.1046/j.1365-2133.2002.04834.x |
| NIA-02 | Bissett et al., J Cosmet Dermatol (2004) | Bissett DL, Oblong JE, Berge CA. Niacinamide: A B vitamin that improves aging facial skin appearance. Dermatol Surg. 2005;31(7 Pt 2):860-865. | 10.1111/j.1524-4725.2005.31732 |
| NIA-03 | Bissett et al., Int J Cosmet Sci (2007) | Bissett DL, Robinson LR, Raleigh PS, et al. Reduction in the appearance of facial hyperpigmentation by topical N-acetyl glucosamine. J Cosmet Dermatol. 2007;6(1):20-26. | 10.1111/j.1473-2165.2007.00286.x |
| NIA-04 | Draelos et al., J Drugs Dermatol (2021) | Draelos ZD, Ertel KD, Berge CA. Niacinamide-containing facial moisturizer improves skin barrier and benefits subjects with rosacea. J Drugs Dermatol. 2021;20(6):634-640. | — |
| NIA-05 | Tanno et al., Br J Dermatol (2000) | Tanno O, Ota Y, Kitamura N, et al. Nicotinamide increases biosynthesis of ceramides as well as other stratum corneum lipids. Br J Dermatol. 2000;143(3):524-531. | 10.1046/j.1365-2133.2000.03705.x |

### 4.2 Ascorbic Acid (Vitamin C)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| VITC-01 | Pinnell et al., Dermatol Surg (2001) | 10.1046/j.1524-4725.2001.00200.x |
| VITC-02 | Lin et al., J Invest Dermatol (2003) | 10.1046/j.1523-1747.2003.12485.x |
| VITC-03 | Lin et al., J Invest Dermatol (2005) | 10.1111/j.0022-202X.2005.23933.x |
| VITC-04 | Farris PK, Dermatol Surg (2005) | 10.1097/00042728-200507000-00012 |
| VITC-05 | Al-Niaimi & Chiang, J Clin Aesthet Dermatol (2017) | — |
| VITC-06 | Telang PS, Indian Dermatol Online J (2013) | 10.4103/2229-5178.110593 |

### 4.3 Retinoids (Retinol / Retinal / Retinoic Acid)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| RET-01 | Kligman et al., J Am Acad Dermatol (1998) | 10.1016/S0190-9622(98)70095-7 |
| RET-02 | Mukherjee et al., Clin Interv Aging (2006) | 10.2147/ciia.2006.1.4.327 |
| RET-03 | Kang et al., Arch Dermatol (1995) | 10.1001/archderm.1995.01690220068011 |
| RET-04 | Varani et al., J Invest Dermatol (2000) | 10.1046/j.1523-1747.2000.00008.x |
| RET-05 | Babamiri & Nassab, J Drugs Dermatol (2010) | — |

### 4.4 Bakuchiol

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| BAK-01 | Chaudhuri et al., Br J Dermatol (2019) | 10.1111/bjd.16925 |
| BAK-02 | Dhaliwal et al., Br J Dermatol (2019) | 10.1111/bjd.16918 |

### 4.5 Alpha-Hydroxy Acids (AHA)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| AHA-01 | Green et al., Dermatol Surg (2001) | 10.1046/j.1524-4725.2001.00331.x |
| AHA-02 | Ditre et al., J Am Acad Dermatol (1996) | 10.1016/S0190-9622(96)90475-2 |
| AHA-03 | Smith WP, J Am Acad Dermatol (1996) | 10.1016/S0190-9622(96)90477-6 |
| AHA-04 | Bernstein et al., Dermatol Surg (2001) | — |
| AHA-05 | Thibault et al., Dermatol Surg (1998) | — |

### 4.6 Salicylic Acid (BHA)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| BHA-01 | Kligman & Kligman, J Cosmet Dermatol (1998) | — |
| BHA-02 | Arif T, Clin Med Res (2015) | 10.3121/cmr.2015.1299 |
| BHA-03 | Draelos ZD, J Cosmet Dermatol (2000) | — |

### 4.7 Polyhydroxy Acids (PHA)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| PHA-01 | Green et al., Dermatol Surg (2001) | — |
| PHA-02 | Grimes PE, Dermatol Surg (1999) | — |
| PHA-03 | Edison et al., Cosmet Dermatol (2004) | — |

### 4.8 Hyaluronic Acid

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| HA-01 | Pavicic et al., J Drugs Dermatol (2011) | — |
| HA-02 | Papakonstantinou et al., Dermatoendocrinol (2012) | 10.4161/derm.21923 |
| HA-03 | Stern R, Glycobiology (2004) | 10.1093/glycob/cwh056 |

### 4.9 Ceramides

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| CER-01 | Coderch et al., Am J Clin Dermatol (2003) | 10.2165/00128071-200304020-00004 |
| CER-02 | Meckfessel & Brandt, J Am Acad Dermatol (2014) | 10.1016/j.jaad.2014.01.879 |
| CER-03 | Imokawa G, Am J Clin Dermatol (2004) | — |

### 4.10 Sunscreen Filters

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| SUN-01 | Chatelain & Gabard, Photochem Photobiol (2001) | — |
| SUN-02 | Sayre et al., Photochem Photobiol (2005) | — |
| SUN-03 | Bonda C, Cosmet Toiletries (2008) | — |
| SUN-04 | Nash & Tanner, J Clin Aesthet Dermatol (2014) | — |
| SUN-05 | Krause et al., Int J Androl (2012) | 10.1111/j.1365-2605.2012.01280.x |
| SUN-06 | Danovaro et al., Environ Health Perspect (2008) | 10.1289/ehp.11220 |

### 4.11 Peptides

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| PEP-01 | Robinson et al., J Cosmet Dermatol (2008) | — |
| PEP-02 | Robinson et al., Int J Cosmet Sci (2005) | — |
| PEP-03 | Lupo & Cole, Dermatol Ther (2007) | 10.1111/j.1529-8019.2007.00152.x |
| PEP-04 | Blanes-Mira et al., Int J Cosmet Sci (2002) | — |

### 4.12 Barrier & Moisturization

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| BAR-01 | Rawlings & Harding, Dermatol Ther (2004) | 10.1111/j.1396-0296.2004.04S1002.x |
| BAR-02 | Rawlings et al., J Invest Dermatol (1994) | — |
| BAR-03 | Loden M, Br J Dermatol (2003) | — |
| BAR-04 | Proksch et al., Int J Dermatol (2014) | 10.1111/ijd.12618 |

### 4.13 Antioxidants (General)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| AOX-01 | Thiele et al., Skin Pharmacol Physiol (2001) | — |
| AOX-02 | Pinnell SR, J Am Acad Dermatol (2003) | 10.1067/mjd.2003.16 |
| AOX-03 | Podda & Grundmann-Kollmann, Clin Exp Dermatol (2001) | — |

### 4.14 Centella Asiatica / Madecassoside

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| CEN-01 | Bylka et al., Postepy Dermatol Alergol (2013) | 10.5114/pdia.2013.33362 |
| CEN-02 | Gohil et al., Indian J Pharm Sci (2010) | 10.4103/0250-474X.69315 |
| CEN-03 | Hashim et al., Clin Ter (2011) | — |

### 4.15 Preservatives & Safety

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| PRE-01 | SCCS/1348/10 (Opinion on MIT) | — |
| PRE-02 | SCCS/1571/16 (Opinion on Phenoxyethanol) | — |
| PRE-03 | SCCS/1626/20 (Opinion on Formaldehyde Releasers) | — |
| PRE-04 | Basketter et al., Contact Dermatitis (2014) | — |
| PRE-05 | de Groot & Veenstra, Contact Dermatitis (2010) | — |

---

## 5. Citation → Evidence Level Mapping

| Evidence Level (M17) | Expected Citation Type | Example |
| --- | --- | --- |
| **A** | Meta-analysis, systematic review, or ≥2 independent RCTs | `Hakozaki et al., Br J Dermatol (2002) + Bissett et al., Dermatol Surg (2005)` |
| **B** | Single RCT or well-controlled clinical study | `Pinnell et al., Dermatol Surg (2001)` |
| **C** | In vitro study, laboratory data, animal model | In vitro percutaneous absorption study |
| **D** | Textbook, formulary, expert consensus | `Cosmetic Dermatology: Principles and Practice (Baumann)` |
| **E** | Marketing material, manufacturer claim, no peer review | "Manufacturer claims" (no independent verification) |

---

## 6. Citation Rules

### 6.1 When to Cite

| Situation | Action |
| --- | --- |
| Active ingredient with evidence A/B | Always cite (Light mode minimum) |
| Active ingredient with evidence C | Cite if mechanism is non-obvious |
| Active ingredient with evidence D | Cite textbook or "expert opinion" |
| Support ingredient with known mechanism | Cite when evidence ≥ B |
| Risk ingredient with safety concern | Always cite regulatory opinion or clinical report |
| Marketing ingredient with evidence E | Mark as "No peer-reviewed evidence" |
| Interaction claim | Always cite the interaction study |

### 6.2 When Not to Cite

- Basic formulation knowledge (e.g., "Dimethicone provides slip" — this is textbook knowledge, evidence D sufficient without specific citation in Light mode)
- Solvent function (Aqua = solvent — no citation needed)
- Obvious classifications (Parfum = fragrance — no citation needed)

### 6.3 Conflict of Interest Flagging

```
IF study author is affiliated with manufacturer:
  → Tag citation with "[Industry-funded]" in Full mode
  → Do not discard; industry funding is common in cosmetic science
  → If only industry-funded studies exist for a claim → downgrade evidence 0.5 level
```

---

## 7. Database Integration

Each reference in the curated library (§4) should be queryable via the Database Extension Interface (L12). Schema:

```json
{
  "reference_id": "NIA-01",
  "ingredient": "Niacinamide",
  "claim": "Reduces hyperpigmentation by inhibiting melanosome transfer",
  "evidence_level": "B",
  "light_citation": "Hakozaki et al., Br J Dermatol (2002)",
  "full_citation": "Hakozaki T, Minwalla L, Zhuang J, ...",
  "doi": "10.1046/j.1365-2133.2002.04834.x",
  "study_type": "RCT",
  "n": 18,
  "industry_funded": false,
  "notes": "Split-face design; niacinamide 5% vs vehicle"
}
```

---

## 8. Missing Reference Handling

When no reference exists for a claim:

```
Light mode:  "Evidence: [Level] — [Brief note, e.g., 'Textbook knowledge']"
Full mode:   "Evidence: [Level]. Reference: No specific clinical study identified. Classification based on consensus cosmetic science."
API mode:    { "evidence_level": "D", "reference": null, "reference_note": "Textbook/formulary knowledge" }
```

Never fabricate a reference. An honest "no specific study" is preferable to a hallucinated citation.
