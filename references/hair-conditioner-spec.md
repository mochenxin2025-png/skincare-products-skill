# Hair Conditioner Specification v1.0

Supplement to the main framework. Covers hair conditioner, hair mask, and leave-in conditioner. Load when product is identified as "Hair Conditioner", "Conditioner", "Hair Mask", "Hair Treatment", or "Leave-In Conditioner".

---

## 1. First Principle

Hair conditioner is **not a hair repair product**. Its fundamental function is **physical surface modification of hair fibers**, not biological repair.

Human hair is composed of dead keratin fibers with **no metabolic activity**. Therefore:
- Hair cannot regenerate
- Hair cuticles cannot biologically heal
- Hair shafts cannot rebuild themselves
- Permanent repair is biologically impossible

**Primary functions of conditioner**:
1. Adsorption of cationic conditioning agents → charge neutralization
2. Formation of silicone protective films → friction reduction
3. Reduction of fiber-to-fiber friction → less mechanical damage

**Observable effects**: Smoothness, anti-static, reduced frizz, reduced breakage, increased shine, improved combability.

**Conditioners improve surface properties — not biological hair health.**

---

## 2. Formula Architecture

Conditioners follow a fundamentally different architecture from skincare emulsions:

```
Water
  ↓
Fatty Alcohol Base (Cetyl/Stearyl/Cetearyl Alcohol) → thickens, lubricates
  ↓
Cationic Conditioner (BTMS, Behentrimonium Chloride) → anti-static, smoothing
  ↓
Silicone Film System (Amodimethicone, Dimethicone) → protective film
  ↓
Auxiliary System (Panthenol, humectants, oils)
```

Most high-quality conditioners follow this architecture. The fatty alcohol + cationic surfactant forms a **lamellar gel network** that is the structural backbone of the product.

---

## 3. Core Conditioning Ingredients (★★★★★)

### 3.1 Cationic Conditioning Agents — THE most important ingredients

| Ingredient | Alias | Function |
| --- | --- | --- |
| Behentrimonium Methosulfate | BTMS | Anti-static, surface smoothing, charge neutralization, friction reduction, combability |
| Behentrimonium Chloride | — | Excellent detangling, conditioning |
| Cetrimonium Chloride | — | Lighter conditioning; good for fine hair |
| Stearamidopropyl Dimethylamine | — | pH-dependent conditioning; excellent at pH 4–6 |
| Distearyldimonium Chloride | — | Heavy conditioning; for very damaged hair |

**Mechanism**: Positively charged (cationic) molecules adsorb to negatively charged damaged hair sites → charge neutralization → reduced static → smoother cuticle alignment.

**Assessment**: Does the conditioner contain at least one of these in the first 5 ingredients? If not → architecture penalty.

### 3.2 Amino-Functional Silicones — Premium conditioning technology

| Ingredient | Function | Ranking |
| --- | --- | --- |
| Bis-Aminopropyl Dimethicone | Selective deposition on damaged sites; film formation; shine; frizz reduction | Best |
| Amodimethicone | Selective deposition; film formation; breakage reduction | Excellent |

**Mechanism**: Amino groups give silicones a positive charge → selective deposition on negatively charged damaged hair → targeted repair of damaged areas → less buildup on healthy hair.

### 3.3 Standard Silicones

| Ingredient | Function |
| --- | --- |
| Dimethicone | Protective film, smoothness, shine, friction reduction |
| Dimethiconol | Heavier film; more conditioning |

**Anti-marketing-myth rule**: Silicones are safe and effective. They should NOT be negatively judged based on "silicone-free" marketing narratives. There is no scientific evidence that silicones harm hair.

---

## 4. Supporting Ingredients

### Fatty Alcohols (★★★★☆ — Beneficial)

| Ingredient | Function |
| --- | --- |
| Cetyl Alcohol | Lubrication, thickening, emulsion stabilization, softness |
| Stearyl Alcohol | Same; slightly heavier feel |
| Cetearyl Alcohol | Blend of both |

**Note**: These are NOT "drying alcohols" (ethanol/denat.). They are beneficial conditioning ingredients and form the structural backbone of conditioner.

### Cationic Polymers (★★★★☆)

| Ingredient | Function |
| --- | --- |
| Polyquaternium-7 | Film formation, smoothness, anti-static |
| Polyquaternium-10 | Film formation, deposition aid |
| Guar Hydroxypropyltrimonium Chloride | Deposition aid, conditioning |

### Panthenol (★★★★☆)

Moisturization + softness + reduced dryness. Limited but real effectiveness even in rinse-off. The most evidence-supported auxiliary ingredient in conditioners.

---

## 5. Marketing Ingredients in Conditioner

These ingredients have **theoretical benefit** but **limited real-world efficacy** in rinse-off conditioner (1–5 minute contact on dead keratin). Score conservatively.

| Ingredient | Claim | Realistic Assessment | Classification |
| --- | --- | --- | --- |
| Ceramides (NP/AP/EOP) | Hair repair | Theoretical; rinse-off contact too short; hair is dead | [M] — Low evidence |
| Hyaluronic Acid / Sodium Hyaluronate | Hydration | Minimal retention after rinsing | [M] — Low evidence |
| Amino Acid Complexes (>3 AAs listed) | Hair reconstruction | Large complexes often marketing-driven | [M] — Marketing signal |
| Hydrolyzed Proteins (Wheat, Keratin, Soy, Silk) | Hair strengthening | Temporary filling effect; cannot permanently repair | [M] — Limited efficacy |
| Collagen | Hair structure | Hair is NOT composed of collagen; no mechanism | [M] — Marketing |
| Botanical Extracts (general) | Various | Near end of list → trace levels → negligible | [M] — Trace |
| Biotin | Hair health | Deficiency-related only; no topical evidence on dead keratin | [M] — No mechanism |

**Rule**: Large numbers of ceramides, HA, amino acids, and botanical extracts in the ingredient list should NOT significantly increase the formulation score. Core conditioning systems determine product performance, not these additives.

---

## 6. Ingredient Evaluation Priority

```
Cationic Conditioning System         ← Most important
        ↓
Silicone System (amino > standard)   ← Second most important
        ↓
Fatty Alcohol System                 ← Structural backbone
        ↓
Polymer System                       ← Film formation support
        ↓
Panthenol                            ← Best auxiliary
        ↓
Humectants (glycerin, PCA, lactate)  ← Limited rinse-off benefit
        ↓
Plant Oils                           ← Sensory only
        ↓
Ceramides / HA / Amino Acids         ← Marketing weight
        ↓
Botanical Extracts                   ← Trace; negligible
```

---

## 7. Hair Conditioner Weight Profile

| Dimension | Weight | Rationale |
| --- | --- | --- |
| Core Effectiveness | 50 | Cationic conditioning + anti-static + film formation combined |
| Architecture | 25 | Fatty alcohol base + silicone film quality + gel network integrity |
| Safety | 15 | Fragrance allergens, preservatives, scalp irritation |
| Support System | 5 | Panthenol, humectants — limited rinse-off relevance |
| Skin/Scalp Adaptation | 5 | Sensitive scalp considerations |

### Core Effectiveness Scoring

```
CE_PS = (Cationic_PS × 0.40) + (Silicone_PS × 0.35) + (Film_PS × 0.25)

Cationic_PS:
  1.00 = BTMS or Behentrimonium Chloride + secondary cationic
  0.70 = One recognized cationic conditioning agent
  0.40 = Only basic cationic (Cetrimonium Chloride alone)
  0.10 = No cationic conditioning agent

Silicone_PS:
  1.00 = Amino silicone + standard silicone
  0.80 = Amodimethicone or Bis-Aminopropyl Dimethicone present
  0.60 = Standard silicone (dimethicone/dimethiconol)
  0.20 = No silicone system

Film_PS:
  1.00 = Silicone + polymer film system (polyquaternium)
  0.70 = Silicone film only
  0.30 = No dedicated film former
```

---

## 8. Risk Ingredients (Conditioner-Specific)

| Risk | Assessment |
| --- | --- |
| Fragrance/Parfum | Odor only; no conditioning benefit. Sensitive scalp → caution. |
| Fragrance allergens (Linalool, Limonene, Citronellol, Hexyl Cinnamal) | EU-listed allergens; cumulative sensitization risk |
| MIT/MCI (Methylisothiazolinone / Methylchloroisothiazolinone) | High sensitization; permitted in rinse-off but should reduce Safety score (−0.15) |
| Alcohol Denat. (high position) | Drying to hair; may increase irritation |
| Essential oils (high concentration) | Can irritate scalp; "natural" ≠ safe |

---

## 9. Conditioner Anti-Hallucination Rules

- Hair is dead keratin — no ingredient can "repair" or "regenerate" it in the biological sense
- "Hair repair" = surface modification + cuticle smoothing; do not claim biological repair
- Silicones are safe and effective — do not penalize based on "silicone-free" marketing narratives
- Ceramides/HA/Amino Acids/Collagen in rinse-off conditioner → [M] regardless of marketing
- Hydrolyzed proteins → temporary filling only; cannot permanently repair; evidence C at best
- Large amino acid complexes (>3 listed) → marketing signal; do not enhance score
- Botanical extracts at end of list → trace concentrations → [M]
- "Anti-hair-loss conditioner" → no mechanism (dead keratin); flag as unsupported
- Biotin in conditioner → no topical evidence on dead keratin; [M]

---

## 10. Scoring Scale

| Score | Interpretation |
| --- | --- |
| 95–100 | Excellent engineering formulation (all three core systems optimal) |
| 90–94 | Excellent commercial formulation |
| 80–89 | Mature standard formulation |
| 70–79 | Basic conditioning formulation |
| < 70 | Marketing-heavy or low-cost formulation |

---

## 11. Leave-In Conditioner Variant

Leave-in conditioners use the same ingredient analysis framework BUT:
- Panthenol, humectants, and amino acids are slightly more effective (not rinsed off)
- Film-forming ingredients have extended action time → +0.05 to Film_PS
- Fragrance/allergen risk is higher (prolonged scalp contact) → −0.05 to Safety PS
- Architecture evaluation shifts: fluid, non-greasy finish matters more
