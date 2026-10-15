# Evidence Citation Specification v1.0

## Overview

This specification defines how scientific evidence is cited in cosmetic analysis reports. It supports two citation **format** modes (§1) plus a curated reference library covering the most commonly cited cosmetic ingredients. The Citation **Mode** pipeline — question classification through to a cited 5-section answer — is §9.

---

## 1. Citation Format Modes (Light / Full)

Output formatting only. Not to be confused with Citation Mode (§9), which selects *whether* a cited answer is produced at all.

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

> **DOI status** — the 38 DOIs below were verified against Crossref (first author + year + title all consistent). The remaining 22 entries carry no DOI because the source is a regulatory opinion (SCCS), a trade journal, or an article Crossref does not index. For those, cite with a PubMed search link per §9.7 — never construct an identifier.

The following references are the most commonly cited in cosmetic ingredient analysis. This library should be embedded in the Agent or accessible via database query.

### 4.1 Niacinamide (Vitamin B3)

| ID | Citation (Light) | Citation (Full) | DOI |
| --- | --- | --- | --- |
| NIA-01 | Hakozaki et al., Br J Dermatol (2002) | Hakozaki T, Minwalla L, Zhuang J, et al. The effect of niacinamide on reducing cutaneous pigmentation and suppression of melanosome transfer. Br J Dermatol. 2002;147(1):20-31. | 10.1046/j.1365-2133.2002.04834.x |
| NIA-02 | Bissett et al., Dermatol Surg (2005) | Bissett DL, Oblong JE, Berge CA. Niacinamide: A B vitamin that improves aging facial skin appearance. Dermatol Surg. 2005;31(7 Pt 2):860-865. | 10.1111/j.1524-4725.2005.31732 |
| NIA-03 | Bissett et al., J Cosmet Dermatol (2007) | Bissett DL, Robinson LR, Raleigh PS, et al. Reduction in the appearance of facial hyperpigmentation by topical N-acetyl glucosamine. J Cosmet Dermatol. 2007;6(1):20-26. | 10.1111/j.1473-2165.2007.00295.x |
| NIA-04 | Draelos et al., J Drugs Dermatol (2021) | Draelos ZD, Ertel KD, Berge CA. Niacinamide-containing facial moisturizer improves skin barrier and benefits subjects with rosacea. J Drugs Dermatol. 2021;20(6):634-640. | — |
| NIA-05 | Tanno et al., Br J Dermatol (2000) | Tanno O, Ota Y, Kitamura N, et al. Nicotinamide increases biosynthesis of ceramides as well as other stratum corneum lipids. Br J Dermatol. 2000;143(3):524-531. | 10.1046/j.1365-2133.2000.03705.x |

### 4.2 Ascorbic Acid (Vitamin C)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| VITC-01 | Pinnell et al., Dermatol Surg (2001) | 10.1046/j.1524-4725.2001.00264.x |
| VITC-02 | Lin et al., J Invest Dermatol (2003) | — |
| VITC-03 | Lin et al., J Invest Dermatol (2005) | 10.1111/j.0022-202x.2005.23768.x |
| VITC-04 | Farris PK, Dermatol Surg (2005) | 10.1111/j.1524-4725.2005.31725 |
| VITC-05 | Al-Niaimi & Chiang, J Clin Aesthet Dermatol (2017) | — |
| VITC-06 | Telang PS, Indian Dermatol Online J (2013) | 10.4103/2229-5178.110593 |

### 4.3 Retinoids (Retinol / Retinal / Retinoic Acid)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| RET-01 | Kligman et al., J Am Acad Dermatol (1998) | — |
| RET-02 | Mukherjee et al., Clin Interv Aging (2006) | 10.2147/ciia.2006.1.4.327 |
| RET-03 | Kang et al., Arch Dermatol (1995) | — |
| RET-04 | Varani et al., J Invest Dermatol (2000) | 10.1046/j.1523-1747.2000.00902.x |
| RET-05 | Babamiri & Nassab, Aesthet Surg J (2010) | 10.1177/1090820x09360704 |

### 4.4 Bakuchiol

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| BAK-01 | Chaudhuri et al., Br J Dermatol (2019) | — |
| BAK-02 | Dhaliwal et al., Br J Dermatol (2019) | 10.1111/bjd.16918 |

### 4.5 Alpha-Hydroxy Acids (AHA)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| AHA-01 | Green et al., Dermatol Surg (2001) | — |
| AHA-02 | Ditre et al., J Am Acad Dermatol (1996) | 10.1016/s0190-9622(96)80110-1 |
| AHA-03 | Smith WP, J Am Acad Dermatol (1996) | 10.1016/s0190-9622(96)90602-7 |
| AHA-04 | Bernstein et al., Dermatol Surg (2001) | — |
| AHA-05 | Thibault et al., Dermatol Surg (1998) | 10.1111/j.1524-4725.1998.tb04209.x |

### 4.6 Salicylic Acid (BHA)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| BHA-01 | Kligman & Kligman, Dermatol Surg (1998) | 10.1111/j.1524-4725.1998.tb04162.x |
| BHA-02 | Arif T, Clin Cosmet Investig Dermatol (2015) | 10.2147/ccid.s84765 |
| BHA-03 | Draelos ZD, Dermatol Ther (2000) | 10.1046/j.1529-8019.2000.00018.x |

### 4.7 Polyhydroxy Acids (PHA)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| PHA-01 | Green et al., Dermatol Surg (2001) | — |
| PHA-02 | Grimes PE, Dermatol Surg (1999) | 10.1046/j.1524-4725.1999.08145.x |
| PHA-03 | Edison et al., Cosmet Dermatol (2004) | — |

### 4.8 Hyaluronic Acid

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| HA-01 | Pavicic et al., J Drugs Dermatol (2011) | — |
| HA-02 | Papakonstantinou et al., Dermatoendocrinol (2012) | 10.4161/derm.21923 |
| HA-03 | Stern R, Eur J Cell Biol (2004) | 10.1078/0171-9335-00392 |

### 4.9 Ceramides

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| CER-01 | Coderch et al., Am J Clin Dermatol (2003) | 10.2165/00128071-200304020-00004 |
| CER-02 | Meckfessel & Brandt, J Am Acad Dermatol (2014) | 10.1016/j.jaad.2014.01.891 |
| CER-03 | Imokawa G, Exog Dermatol (2004) | 10.1159/000086158 |

### 4.10 Sunscreen Filters

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| SUN-01 | Chatelain & Gabard, Photochem Photobiol (2001) | 10.1562/0031-8655(2001)074<0401:pobmaa>2.0.co;2 |
| SUN-02 | Sayre et al., Photochem Photobiol (2005) | 10.1111/j.1751-1097.2005.tb00207.x |
| SUN-03 | Bonda C, Cosmet Toiletries (2008) | — |
| SUN-04 | Nash & Tanner, J Clin Aesthet Dermatol (2014) | — |
| SUN-05 | Krause et al., Int J Androl (2012) | 10.1111/j.1365-2605.2012.01280.x |
| SUN-06 | Danovaro et al., Environ Health Perspect (2008) | 10.1289/ehp.10966 |

### 4.11 Peptides

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| PEP-01 | Robinson et al., J Cosmet Dermatol (2008) | — |
| PEP-02 | Robinson et al., Int J Cosmet Sci (2005) | 10.1111/j.1467-2494.2005.00261.x |
| PEP-03 | Lupo & Cole, Dermatol Ther (2007) | 10.1111/j.1529-8019.2007.00148.x |
| PEP-04 | Blanes-Mira et al., Int J Cosmet Sci (2002) | 10.1046/j.1467-2494.2002.00153.x |

### 4.12 Barrier & Moisturization

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| BAR-01 | Rawlings & Harding, Dermatol Ther (2004) | 10.1111/j.1396-0296.2004.04s1005.x |
| BAR-02 | Rawlings et al., J Invest Dermatol (1994) | 10.1111/1523-1747.ep12398620 |
| BAR-03 | Loden M, Br J Dermatol (2003) | — |
| BAR-04 | Proksch et al., Int J Dermatol (2014) | — |

### 4.13 Antioxidants (General)

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| AOX-01 | Thiele et al., Skin Pharmacol Physiol (2001) | 10.1159/000056395 |
| AOX-02 | Pinnell SR, J Am Acad Dermatol (2003) | 10.1067/mjd.2003.16 |
| AOX-03 | Podda & Grundmann-Kollmann, Clin Exp Dermatol (2001) | 10.1046/j.1365-2230.2001.00902.x |

### 4.14 Centella Asiatica / Madecassoside

| ID | Citation (Light) | DOI |
| --- | --- | --- |
| CEN-01 | Bylka et al., Postepy Dermatol Alergol (2013) | 10.5114/pdia.2013.33378 |
| CEN-02 | Gohil et al., Indian J Pharm Sci (2010) | 10.4103/0250-474x.78519 |
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

---

## 9. Citation Mode Pipeline (v2.2)

Citation Mode answers efficacy, safety, disease, and myth questions. It is not a product report — it is an evidence answer. Selected in `SKILL.md` Step 0.

### 9.1 Problem Classification

| Class | Example | Primary source tier (§9.3) |
| --- | --- | --- |
| Efficacy | "Does azelaic acid help with post-acne marks?" | 3–4 |
| Safety | "Is salicylic acid safe during pregnancy?" | 1 |
| Disease | "Can niacinamide treat rosacea?" | 2–4 |
| Myth | "Is it true that skin absorbs best at 10pm?" | 3–5 + explicit refutation |
| Product-specific | "Is this product clinically validated?" | usually unanswerable — Rule 1 |

Class is fixed before any claim is written. An unclassifiable question is not answered in Citation Mode — it is returned with a request for narrowing.

### 9.2 Claim Extraction

Decompose the question into atomic claims. One claim = one verifiable proposition.

- "Does A + B help with C?" → C1: A helps C; C2: B helps C; C3: A + B outperforms either alone
- Never merge claims; never extract a claim the user did not make
- Each claim receives an ID (C1, C2, …) reused in §9.6

### 9.3 Evidence Routing

Route every claim to its source tier **before** searching the library. Route by class, not by convenience.

| Tier | Sources | Legitimate use |
| --- | --- | --- |
| 1 — Regulatory | SCCS opinions, CIR reports, FDA, NMPA, EU Annexes | Safety, concentration limits, pregnancy, long-term use |
| 2 — Guidelines | AAD, EADV, JDA, EDF, national dermatology guidelines | Treatment positioning, disease management |
| 3 — Systematic reviews / meta-analyses | Cochrane, PubMed | Efficacy magnitude |
| 4 — Clinical trials | RCTs, in vivo human | Human efficacy claims |
| 5 — In vitro / mechanistic | Cell, ex vivo, model membrane | Mechanism only — never efficacy (Rule 2) |
| 6 — Textbook / expert opinion | Standard references | Background only |
| 7 — Marketing / unsourced | — | Not citable (Rule 5) |

A safety claim load-bearing on tiers 3–5 instead of tier 1 is a routing error (Rule 4).

Cross-references for routing: concentration ceilings → `references/bootstrap-database.md` §5; ingredient identity and class → `references/ingredient-ontology-map.md`; ingredient pairs → `references/interaction-rules.md`; the curated library's entries carry own evidence levels (§4, §5).

### 9.4 Evidence Ranking

Within a tier, rank by study design → sample size → recency → independence from the product's manufacturer. Conflicts of interest are kept but flagged (§6.3). Disagreeing results are both reported, with the contradiction stated — never averaged into a false consensus.

### 9.5 Evidence Card

Every claim is resolved into a card before any prose is written.

| Field | Content |
| --- | --- |
| Claim ID | C1 |
| Claim | the proposition, as the user stated it |
| Verdict | Supported / Partially supported / Not supported / Insufficient evidence |
| Evidence level | A–E (M17) |
| Source tier | 1–7 (§9.3) |
| Key finding | one sentence; quantitative if the source gives a number |
| Caveat | what the evidence does **not** show |
| Citation | `[C1]` with DOI or link (§9.7) |

"Not supported" and "Insufficient evidence" are valid, expected verdicts. A card with no caveat usually means the source was not read carefully.

### 9.6 Five-Section Output

| # | Section | Content |
| --- | --- | --- |
| ① | Summary / Core Answer | Direct answer in ≤3 sentences. No citation markers here, no hedging padding |
| ② | Problem Classification | Class from §9.1, source tier used, and what was **not** asked |
| ③ | Evidence-Supported Claims | One bullet per claim: ID + evidence level + caveat |
| ④ | Inference & Uncertainty | Three-class separation: literature-supported / formulation-inferred / uncertain; states explicitly what the evidence cannot answer |
| ⑤ | References / Sources | One entry per citation: `[Cn] Author, Journal (Year)` + link + tier |

Output-level constraints:

- Every ID used in ③ appears in ⑤; every entry in ⑤ is cited in ③
- Product-specific validation questions land in ④, never in ③ (Rule 1)
- If ③ is empty, say so plainly and let ④ carry the answer
- No numeric score in this mode — scoring belongs to Product Analysis mode

Layout template: `references/output-format-spec.md` §6.

### 9.7 Link Format

| Situation | Link |
| --- | --- |
| DOI known | `https://doi.org/<doi>` |
| DOI unknown, author + year + title known | PubMed search: `https://pubmed.ncbi.nlm.nih.gov/?term=<author>+<year>+<title keywords>` |
| Regulatory document | SCCS / CIR / FDA / NMPA document page or document number |
| No source found | no link — and state "no direct evidence" |

Never construct a DOI, PMID, or document number that was not read. A PubMed **search** link is honest; an invented DOI is not.

### 9.8 Operating Constraints

- Confidence still applies (`references/confidence-engine-spec.md`). If the evidence base is too thin to answer, return conservative mode and say so rather than asserting
- Safety questions are never carried by efficacy evidence as the load-bearing source (Rule 4)
- The curated library (§4) is a starting point, not a ceiling — its 60 entries cover the most common ingredients, not all of them
- Determinism: identical question + identical library → identical card verdicts
