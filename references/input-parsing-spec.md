# Input Parsing & Normalization Specification v1.0

## Overview

Cosmetic ingredient analysis begins with raw, unstructured input — typically a photo of the ingredient label or pasted text. This specification defines how to parse, clean, and normalize ingredient lists before they enter the M18 Runtime Pipeline.

---

## 1. Input Sources & Preprocessing

| Source | Format | Strategy |
| --- | --- | --- |
| **Product photo** | Image (JPEG/PNG) | OCR → text extraction → normalization |
| **Pasted text** | Plain text / markdown | Direct parsing → normalization |
| **Product URL** | HTML | Scrape ingredient section → text extraction → normalization |
| **PDF / Manual** | Document | Text extraction → normalization |

### 1.1 OCR Strategy (Image Input)

When input is an image, apply OCR with the following guidelines:

```
1. Preprocess image:
   - Convert to grayscale
   - Increase contrast (CLAHE recommended)
   - Binarize (Otsu threshold)
   - Deskew if text is rotated

2. OCR engine preference:
   - Primary: Text with clear contrast → standard OCR
   - Curved surface (bottle/tube): Perspective correction first
   - Low resolution (<150dpi): Upscale 2×, denoise, re-OCR

3. If OCR confidence <80% per character:
   - Flag input quality as "Partial" (M14)
   - Attempt dictionary-based correction (see §3)
   - If still unintelligible → "Unreadable" (M14)
```

### 1.2 Common OCR Error Patterns

| OCR Output | Likely Intended | Reason |
| --- | --- | --- |
| `Aqva` | `Aqua` | `u` misread as `v` |
| `AQUA/WATER` | `Aqua` | All-caps rendering |
| `Giycerin` | `Glycerin` | `l` misread as `i` |
| `Niacinam1de` | `Niacinamide` | `i` misread as `1` |
| `Tocopher0l` | `Tocopherol` | `o` misread as `0` |
| `Sodi um Hyalur0nate` | `Sodium Hyaluronate` | Spurious spaces; `o`→`0` |
| `Dimethic0ne` | `Dimethicone` | `o` misread as `0` |
| `Parf um` | `Parfum` | Spurious space |
| `Benzyl Alcoho1` | `Benzyl Alcohol` | `l` misread as `1` |
| `Cl 77891` | `CI 77891` | `I` misread as `l` |

**Correction algorithm**: For each OCR output word, compute edit distance to all known INCI names. If distance ≤ 2 and the ratio is unique in context, auto-correct. Flag all corrections for transparency.

---

## 2. Ingredient List Parsing

### 2.1 Delimiter Normalization

Raw ingredient lists use various delimiters. Normalize to a standard format:

```
Step 1: Remove all header/footer text
  - Strip "INGREDIENTS:", "Ingredients:", "成分:", "全成分:", etc.
  - Strip trailing punctuation like "。", ".", "."
  - Remove "(FIL CODE: ...)" and similar codes

Step 2: Normalize delimiters
  - ", " → comma-delimited
  - "，" (full-width comma) → ", "
  - Line breaks → ", "
  - "·" (middle dot) → ", "
  - "、"(Chinese/Japanese enumeration comma) → ", "
  - "；" / "；" (semicolons) → ", "

Step 3: Normalize whitespace
  - Collapse multiple spaces → single space
  - Trim leading/trailing whitespace per ingredient

Step 4: Split into individual ingredient names
  - Split on ", "
  - Each item = one ingredient
```

### 2.2 Special Pattern Handling

| Pattern | Example | Handling |
| --- | --- | --- |
| **May Contain** | `[+/- May Contain: CI 77891, CI 77491]` | Flag as optional; include in analysis but mark uncertainty |
| **Parenthetical INCI** | `Water (Aqua)` | Extract INCI name (`Aqua`); store alias `Water` |
| **Percentage declarations** | `Niacinamide (10%)` | Extract percentage; store as concentration data point |
| **Bracketed sub-components** | `Fragrance (Parfum) [contains: Linalool, Limonene]` | Expand: `Parfum, Linalool, Limonene` |
| **Color Index codes** | `CI 77891`, `CI 77491` | Validate against CI registry; flag if non-standard |
| **Trade names** | `Tinosorb® S` | Normalize to INCI: `Bis-Ethylhexyloxyphenol Methoxyphenyl Triazine` |
| **Numeric-only codes** | `Glycerin (and) Aqua (and) Sodium PCA` | Split `(and)` into separate ingredients |

### 2.3 Position Tracking

The position of each ingredient in the list is significant (INCI lists are ordered by descending concentration above 1%). Preserve position index (1-based) for:

- Concentration inference (ingredients before fragrance are typically ≥1%)
- Presence Score position bonuses/penalties (§2.1 of scoring algorithm)

---

## 3. INCI Normalization

### 3.1 Case Normalization

All INCI names are Title Case (capitalize first letter of each major word):

```
"NIACINAMIDE" → "Niacinamide"
"sodium hyaluronate" → "Sodium Hyaluronate"
"dimethicone crosspolymer" → "Dimethicone Crosspolymer"
```

### 3.2 Common Name → INCI Mapping

Non-INCI common names must be mapped to INCI before entering the pipeline:

| Common Name | INCI |
| --- | --- |
| Water | Aqua |
| Vitamin C | Ascorbic Acid |
| Vitamin E | Tocopherol |
| Vitamin B3 | Niacinamide |
| Vitamin B5 | Panthenol |
| Vitamin A | Retinol |
| Shea Butter | Butyrospermum Parkii Butter |
| Cocoa Butter | Theobroma Cacao Seed Butter |
| Jojoba Oil | Simmondsia Chinensis Seed Oil |
| Argan Oil | Argania Spinosa Kernel Oil |
| Rosehip Oil | Rosa Canina Fruit Oil |
| Tea Tree Oil | Melaleuca Alternifolia Leaf Oil |
| Aloe Vera | Aloe Barbadensis Leaf Juice / Extract |
| Green Tea Extract | Camellia Sinensis Leaf Extract |
| Licorice Extract | Glycyrrhiza Glabra Root Extract |
| Snail Mucin | Snail Secretion Filtrate |
| Bee Venom | Bee Venom |
| Propolis | Propolis Extract |
| Honey | Honey / Mel |
| Centella / Cica / Tiger Grass | Centella Asiatica Extract |
| Madecassoside (standalone) | Madecassoside |
| Mugwort | Artemisia Princeps Extract / Artemisia Vulgaris Extract |
| Heartleaf | Houttuynia Cordata Extract |
| Rice Bran Oil | Oryza Sativa Bran Oil |
| Sake / Rice Ferment | Saccharomyces/Rice Ferment Filtrate |
| Galactomyces / Pitera™ | Galactomyces Ferment Filtrate |
| Bifida / Estée Lauder ANR | Bifida Ferment Lysate |
| Retinal / Retinaldehyde | Retinal |
| Bakuchiol | Bakuchiol |
| Argireline | Acetyl Hexapeptide-8 |
| Matrixyl | Palmitoyl Pentapeptide-4 / Palmitoyl Tripeptide-1 |
| Copper Peptide | Copper Tripeptide-1 |
| Ceramides (generic) | Ceramide NP / AP / EOP (check specific) |
| AHA (generic) | Check: Glycolic Acid / Lactic Acid / Mandelic Acid etc. |
| BHA | Salicylic Acid |
| PHA | Gluconolactone / Lactobionic Acid |
| Vitamin C derivative | Check: Ascorbyl Glucoside / SAP / MAP / Ethyl Ascorbic Acid etc. |
| Chemical sunscreen (generic) | Check specific filter |
| Physical / Mineral sunscreen | Zinc Oxide / Titanium Dioxide |
| Fragrance | Parfum |
| Essential Oil | Check specific: Lavandula Angustifolia Oil etc. |
| PEG | Find specific: PEG-40 Hydrogenated Castor Oil etc. |
| Silicone | Find specific: Dimethicone / Cyclopentasiloxane etc. |
| Paraben | Find specific: Methylparaben / Propylparaben etc. |

### 3.3 Trade Name → INCI Mapping

| Trade Name | INCI |
| --- | --- |
| Tinosorb S | Bis-Ethylhexyloxyphenol Methoxyphenyl Triazine |
| Tinosorb M | Methylene Bis-Benzotriazolyl Tetramethylbutylphenol |
| Tinosorb A2B | Tris-Biphenyl Triazine |
| Uvinul A Plus | Diethylamino Hydroxybenzoyl Hexyl Benzoate |
| Uvinul T150 | Ethylhexyl Triazone |
| Mexoryl SX | Terephthalylidene Dicamphor Sulfonic Acid |
| Mexoryl XL | Drometrizole Trisiloxane |
| Mexoryl 400 | Methoxypropylamino Cyclohexenylidene Ethoxyethylcyanoacetate |
| Parsol 1789 | Butyl Methoxydibenzoylmethane (Avobenzone) |
| Parsol SLX | Polysilicone-15 |
| Neo Heliopan AP | Disodium Phenyl Dibenzimidazole Tetrasulfonate |
| Neo Heliopan E1000 | Isoamyl p-Methoxycinnamate |
| Kathon CG | Methylchloroisothiazolinone / Methylisothiazolinone |
| Euxyl PE 9010 | Phenoxyethanol + Ethylhexylglycerin |
| SymSave H | Hydroxyacetophenone |
| Aristoflex AVC | Ammonium Acryloyldimethyltaurate/VP Copolymer |
| Sepigel 305 | Polyacrylamide + C13-14 Isoparaffin + Laureth-7 |
| Carbopol | Carbomer |
| Pemulen | Acrylates/C10-30 Alkyl Acrylate Crosspolymer |

---

## 4. Multi-Language Normalization

### 4.1 Chinese → INCI

| 中文 | INCI |
| --- | --- |
| 水 | Aqua |
| 甘油 | Glycerin |
| 烟酰胺 | Niacinamide |
| 透明质酸钠 | Sodium Hyaluronate |
| 丁二醇 | Butylene Glycol |
| 聚二甲基硅氧烷 | Dimethicone |
| 苯氧乙醇 | Phenoxyethanol |
| 香精 | Parfum |
| 生育酚 | Tocopherol |
| 视黄醇 | Retinol |
| 抗坏血酸 | Ascorbic Acid |
| 水杨酸 | Salicylic Acid |
| 神经酰胺 | Ceramide (check specific NP/AP/EOP) |
| 泛醇 | Panthenol |
| 角鲨烷 | Squalane |
| 乙醇 | Alcohol / Alcohol Denat. |
| 黄原胶 | Xanthan Gum |
| 卡波姆 | Carbomer |
| 氢氧化钠 | Sodium Hydroxide |
| 柠檬酸 | Citric Acid |
| 二氧化钛 | Titanium Dioxide |
| 氧化锌 | Zinc Oxide |

### 4.2 Japanese → INCI

| 日本語 | INCI |
| --- | --- |
| 水 | Aqua |
| グリセリン | Glycerin |
| ナイアシンアミド | Niacinamide |
| ヒアルロン酸Na | Sodium Hyaluronate |
| BG | Butylene Glycol |
| ジメチコン | Dimethicone |
| フェノキシエタノール | Phenoxyethanol |
| 香料 | Parfum |
| トコフェロール | Tocopherol |
| レチノール | Retinol |

### 4.3 Korean → INCI

| 한국어 | INCI |
| --- | --- |
| 정제수 | Aqua |
| 글리세린 | Glycerin |
| 나이아신아마이드 | Niacinamide |
| 히알루론산나트륨 | Sodium Hyaluronate |
| 부틸렌글라이콜 | Butylene Glycol |
| 디메티콘 | Dimethicone |
| 페녹시에탄올 | Phenoxyethanol |
| 향료 | Parfum |
| 토코페롤 | Tocopherol |

### 4.4 Language Detection

```
1. Check for CJK characters (U+4E00–U+9FFF, U+3040–U+30FF, U+AC00–U+D7AF)
2. If >30% CJK characters → apply CJK normalization
3. Distinguish Chinese/Japanese/Korean by:
   - Hangul (U+AC00–U+D7AF) → Korean
   - Hiragana/Katakana (U+3040–U+30FF) → Japanese
   - Otherwise → Chinese (most common for cosmetic labels)
4. Hybrid labels (e.g., Japanese with INCI parentheticals) → extract INCI, discard Japanese duplicates
```

---

## 5. Ingredient List Quality Assessment

After parsing, evaluate the input quality to determine M14 Validation Status:

### 5.1 Quality Factors

| Factor | Weight | Assessment Method |
| --- | --- | --- |
| Readability | 30% | OCR confidence or text format quality |
| Completeness | 30% | Does the list end naturally? Any truncation? Missing water? |
| INCI Match Rate | 25% | % of parsed ingredients that match known INCI patterns |
| Order Plausibility | 15% | Does the list order make sense (water/solvent first, fragrance near end)? |

### 5.2 Quality Scoring

```
Quality_Score = (Readability × 0.30) + (Completeness × 0.30) + (INCI_Match_Rate × 0.25) + (Order_Plausibility × 0.15)
```

| Quality Score | M14 Validation Status | Confidence Init |
| --- | --- | --- |
| ≥ 90% | Complete | 100% |
| 75–89% | Complete | 95% |
| 60–74% | Partial | 80% |
| 40–59% | Partial | 65% |
| 20–39% | Unreadable | 50% |
| < 20% | Unknown | 20% |

### 5.3 Completeness Heuristics

| Indicator | Implication |
| --- | --- |
| List ends with preservative or fragrance | Likely complete |
| List ends mid-word / truncated | Incomplete |
| No "Aqua" or "Water" in first 3 ingredients | Suspicious — may be truncated or non-aqueous product |
| Total ingredients < 5 | Suspicious for most cosmetic products (avg: 15–40) |
| No preservative in leave-on product with water | Suspicious — may be incomplete |
| Ends with "..." or "etc." or "等" | Explicitly truncated |

---

## 6. Output of Parsing Stage

The parsed output entering the M18 pipeline should be:

```json
{
  "source_type": "image_ocr | pasted_text | url",
  "validation_status": "Complete | Partial | Unreadable | Unknown",
  "validation_confidence": 0.0–1.0,
  "ingredients": [
    {
      "position": 1,
      "raw_text": "Aqva",
      "normalized_inci": "Aqua",
      "was_corrected": true,
      "correction_reason": "OCR: v→u",
      "ontology": null,
      "concentration_known": false,
      "concentration_value": null,
      "language_source": "en"
    }
  ],
  "warnings": [
    "OCR correction applied: 'Aqva' → 'Aqua'",
    "Ingredient list may be incomplete: ends mid-word"
  ],
  "estimated_total_ingredients": 35,
  "truncation_suspected": false
}
```

---

## 7. Boundary Cases

| Case | Handling |
| --- | --- |
| Empty input | Validation → Unknown; return "No ingredient data provided" |
| Non-cosmetic product | Detect non-INCI text (e.g., food ingredients); return "Input does not appear to be a cosmetic ingredient list" |
| Single ingredient | Flag as likely incomplete; proceed with available data |
| Mixed languages | Extract INCI names where available; use translation table for remainder |
| Handwritten label | OCR likely very low quality → flag as Unreadable; request better image |
| Video screenshot | Frame quality assessment; if <40% → request still photo |
| Ingredient list in image caption / social media post | Strip non-ingredient text; parse only the ingredient portion |
| "Clean beauty" / non-standard naming | Map "clean" aliases to INCI (e.g., "fragrance-free preservative" → specific preservative) |

---

## 8. Integration with M18 Runtime Pipeline

```
Input (raw)
  │
  ▼
[OCR / Text Extraction]  ← this spec §1
  │
  ▼
[Delimiter Normalization] ← this spec §2
  │
  ▼
[INCI Normalization]      ← this spec §3
  │
  ▼
[Language Translation]    ← this spec §4
  │
  ▼
[Quality Assessment]      ← this spec §5 → M14 Validation Status
  │
  ▼
[Structured Output]       ← this spec §6
  │
  ▼
M18 Pipeline: Ontology Mapping → Database Query → ... → Scoring → Report
```
