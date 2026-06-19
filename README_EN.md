# 🧴 Skincare Products Skill

> A dermatology-oriented AI agent framework for cosmetic formulation analysis. Evaluates skincare, body care, and hair care products by mechanism, formula logic, and scientific evidence — never by brand, marketing, or price.

[![Version](https://img.shields.io/badge/version-2.1-blue)](https://github.com)
[![License](https://img.shields.io/badge/license-MIT-green)](https://github.com)
[![Platforms](https://img.shields.io/badge/platforms-8-orange)](https://github.com)
[![Categories](https://img.shields.io/badge/product%20categories-10-purple)](https://github.com)

[![中文](https://img.shields.io/badge/中文-简体-red)](README_CN.md)

---

## 📖 What Is This?

This is a **structured agent skill** that transforms any AI assistant into a dermatology-oriented cosmetic formulation analyst. Instead of evaluating products by brand reputation, marketing claims, or price, it applies:

- **First-principle reasoning** — identify the biological objective before analyzing ingredients
- **Evidence-based evaluation** — every mechanism claim mapped to an A–E evidence level
- **15-category ingredient ontology** — unified classification before any efficacy analysis
- **30 documented ingredient interactions** — synergy, antagonism, and conflict rules
- **Harmonic-mean confidence scoring** — five-factor uncertainty propagation
- **Per-category weight profiles** — 10 product types with optimized scoring dimensions

The framework contains **631 structured data entries** across ingredient databases, interaction rules, and scientific references.

---

## 🎯 What It Analyzes

| Category | Examples | Spec |
| --- | --- | --- |
| 🧼 Facial Cleanser | Foaming cleanser, gel cleanser, cleansing milk | Inline |
| 🚿 Body Wash | Shower gel, body cleanser | `body-wash-spec.md` |
| 💧 Moisturizer | Face cream, gel cream, emulsion | Inline |
| 🧪 Serum | Ampoule, treatment essence | Inline |
| ☀️ Sunscreen | SPF lotion, sunscreen spray, physical/chemical | Inline |
| 🧴 Body Lotion | Body cream, body butter | `body-lotion-spec.md` |
| 🧴 Shampoo | Anti-dandruff, scalp care, daily shampoo | `shampoo-spec.md` |
| 💆 Conditioner | Rinse-off conditioner, hair mask, leave-in | `hair-conditioner-spec.md` |
| 💋 Lip Balm | SPF lip balm, lip butter, lip mask | `lip-balm-spec.md` |
| 👶 Infant Products | Baby cream, baby wash, diaper cream | Inline |

Plus **12 skin type/condition assessments**: Normal, Dry, Oily, Combination, Sensitive, Acne-prone, Seborrheic Dermatitis, Rosacea, Barrier-damaged, Keratosis Pilaris, Body Acne, Infant.

---

## 🧠 How It Works

```
Input (text/OCR) → Validation → Ontology Mapping → Database Query
→ Interaction Analysis → Mechanism Analysis → Architecture Analysis
→ Risk Analysis → Skin Adaptation → Confidence → Scoring → Output
```

### Scoring Formula

```
Final_Score = Σ(PS × EM × IM × Weight) − Marketing_Penalty

PS = Presence Score (0.0–1.0): how well the product fulfills each dimension
EM = Evidence Multiplier: A=1.00  B=0.90  C=0.70  D=0.50  E=0.20
IM = Interaction Modifier: Synergy=1.10  Independent=1.00  Antagonism=0.85  Conflict=0.70
```

### Confidence

Five factors aggregated via **harmonic mean** (worst-factor-aware):

$$C = \frac{5}{\frac{1}{I} + \frac{1}{D} + \frac{1}{M} + \frac{1}{X} + \frac{1}{C}}$$

| Score | Label | Behavior |
| --- | --- | --- |
| ≥ 80% | 🟢 High | Definitive language, numeric score |
| 60–79% | 🟡 Medium | Hedged language, numeric score with caveats |
| 40–59% | 🟠 Low | Qualitative only, no numeric score |
| < 40% | 🔴 Critical | "Insufficient data" — conservative mode |

---

## 🏗️ Architecture

```
skincare-products-skill/
├── SKILL.md                           # Entry point — YAML frontmatter + core pipeline
├── references/                        # Lazy-loaded detailed documentation
│   ├── framework-full.md              #   Complete L0–L12 + M13–M22 specification
│   ├── ingredient-ontology-map.md     #   326 INCI → 15-category ontology
│   ├── bootstrap-database.md          #   140 entries (sunscreen, surfactants, preservatives, humectants, risk)
│   ├── extended-databases.md          #   85 entries (emollients, silicones, polymers, plant extracts)
│   ├── interaction-rules.md           #   30 interaction rules with evidence levels
│   ├── scoring-algorithm.md           #   Full scoring formulas + Niacinamide serum walkthrough
│   ├── confidence-engine-spec.md      #   Harmonic mean formula + fallback linkage
│   ├── input-parsing-spec.md          #   OCR correction + INCI normalization + CJK language tables
│   ├── output-format-spec.md          #   Markdown template + JSON API schema
│   ├── evidence-citation-spec.md      #   50+ curated references with DOIs
│   ├── body-wash-spec.md              #   Rinse-off logic, surfactant evaluation, experience ingredients
│   ├── body-lotion-spec.md            #   Four functional systems, KP evaluation, barrier-friendly ingredients
│   ├── shampoo-spec.md                #   Anti-fungal hierarchy, seborrheic dermatitis pathogenesis
│   ├── hair-conditioner-spec.md       #   Cationic/silicone/fatty alcohol systems, dead keratin constraints
│   └── lip-balm-spec.md               #   Occlusive hierarchy, menthol/camphor danger, semi-mucous membrane
├── assets/
│   └── report-schema.json             #   JSON Schema for machine-consumable reports
└── platforms/
    └── obsidian/                       #   Obsidian-formatted formula cards
```

> **Design principle**: Progressive disclosure. Only `SKILL.md` is always loaded (~380 lines). The 15 reference files are loaded on demand when the agent needs ingredient data, interaction rules, or category-specific evaluation logic.

---

## 🔬 Key Design Decisions

### 15-Category Ingredient Ontology

Every ingredient is classified into exactly ONE primary category before efficacy analysis:

```
Core Active [A] · Formula Support [FS] · Skin Conditioning [SC]
Texture Modifier [TM] · Preservative [P] · Solvent [S] · Chelator [C]
Emulsifier [E] · Stabilizer [ST] · Film Former [FF] · Colorant [CO]
Fragrance [FR] · Botanical [B] · Marketing [M] · Risk [R]
```

Risk `[R]` is additive — an ingredient can be both `[A]` (active) and `[R]` (safety concern).

### 6-Level Priority Hierarchy

When rules conflict:

```
Safety Rules > Scientific Evidence (A/B) > Internal Database
> Ontology Mapping > Mechanism Inference > Heuristic Estimation
```

### Cascading Fallback

```
Database match? → YES: full confidence
               → NO: Ontology match? → YES: infer + reduce confidence
                                     → NO: Mechanism inference? → YES: reduce further
                                                                → NO: "Unknown [name]" — never fabricate
```

### Category-Specific Weight Profiles

No two product types share the same scoring dimensions. Cleansers prioritize safety (30%), sunscreens prioritize UV protection (35%), shampoos prioritize anti-fungal evidence (40% when medicated), body washes prioritize surfactant quality (35%).

---

## 📊 Data Scale

| Resource | Entries |
| --- | --- |
| Ingredient Ontology Map | 326 INCI names |
| Database Entries (Bootstrap + Extended) | 225 |
| Ingredient Interactions | 30 rules |
| Curated Literature References | 50+ (with DOIs) |
| Product Categories | 10 |
| Skin Types / Conditions | 12 |
| Weight Profiles | 10 |
| **Total Structured Data** | **~651** |

---

## ⬇️ Download & Install

### Option 1: Clone via Git (recommended)

```bash
git clone https://github.com/mochenxin2025-png/skincare-products-skill.git
cd skincare-products-skill
```

### Option 2: Download ZIP

[![Download ZIP](https://img.shields.io/badge/Download-ZIP-brightgreen?style=for-the-badge)](https://github.com/mochenxin2025-png/skincare-products-skill/archive/refs/heads/master.zip)

Click the badge above or manually: **Code → Download ZIP** on the GitHub repo page, then extract the archive.

### Option 3: Install as a Hermes Agent Skill

If you're using [Hermes Agent](https://hermes-agent.nousresearch.com), you can install this skill in one command:

```bash
# Make sure the hermes-agent skill is loaded, then:
hermes skills install skincare-products-skill
```

Or install from local directory:

```bash
cp -r /path/to/skincare-products-skill $HERMES_HOME/skills/
# Verify:
hermes skills list | grep skincare
```

### Option 4: Hermes Skill Archive (`.7z`)

Download the portable archive for offline installation:

👉 [**skincare-products-skill.7z**](https://github.com/mochenxin2025-png/skincare-products-skill/releases/download/v2.1/skincare-products-skill.7z)
*(Extract to `$HERMES_HOME/skills/` using 7-Zip)*

---

## 🚀 Usage

### As a Reasonix Code / Claude Code Skill

Place the entire `skincare-products-skill/` directory in your skills folder. The YAML frontmatter in `SKILL.md` provides automatic activation triggers.

### As a ChatGPT Custom GPT

Use the portable single-file version. Paste the contents as the Instructions field.

### As a Cursor Rule

Place the rule content in `.cursorrules` or `.cursor/rules/skincare.md`.

### Trigger Examples

```
"Analyze this ingredient list: Aqua, Niacinamide, Butylene Glycol..."
"Is this sunscreen good?" [attach product photo]
"Compare these two moisturizers"
"Evaluate this anti-dandruff shampoo"
"Review this lip balm — it has menthol in it"
```

---

## 🛡️ Anti-Hallucination Guards

The framework includes explicit anti-hallucination rules to prevent common AI failure modes in cosmetic analysis:

- Never assume concentration without declared evidence
- Never infer efficacy from ingredient count or popularity
- Rinse-off products (body wash, shampoo, conditioner): ingredients in the last third of the ingredient list → trace concentration → reclassify as Marketing `[M]`
- Experience ingredients (menthol, camphor, sea salt) → sensory engineering only → `[M]`
- Collagen, peptides, stem cells, gold in topical products → always `[M]`
- "Used for centuries" ≠ clinical evidence → Evidence D at best
- Database missing → "Insufficient Evidence" — never fabricate
- No interaction rule found → Independent (IM 1.00) — never invent interactions

---

## 📝 Example Output

```markdown
## ⑬ Overall Score: 54 / 100 (🟢 High Confidence)

| Dimension | Weight | PS | EM | IM | Contribution |
| --- | --- | --- | --- | --- | --- |
| Core Effectiveness | 35 | 0.85 | 0.90 | 1.00 | 26.8 |
| Architecture | 20 | 0.70 | 0.50 | 1.00 | 7.0 |
| Safety | 20 | 0.85 | 0.70 | 1.00 | 11.9 |
| Support System | 15 | 0.50 | 0.50 | 1.00 | 3.75 |
| Skin Adaptation | 10 | 0.70 | 0.70 | 1.00 | 4.9 |

## ⑭ Conclusion

**Strengths**: Well-recognized active (Niacinamide 10%) with strong clinical evidence.
**Limitations**: Simple architecture; no antioxidant support system.
**Recommendation**: Recommended for normal to oily skin seeking hyperpigmentation reduction.
```

---

## 🔌 Platform Compatibility

| Platform | Status | Notes |
| --- | --- | --- |
| Reasonix Code | ✅ Native | Full multi-file progressive disclosure |
| Claude Code | ✅ Compatible | YAML frontmatter + file-reading tools |
| Codex CLI | ⚠️ Adapter needed | Different skill manifest format |
| Cursor Rules | ⚠️ Flat file | Multiple references → single `.cursorrules` |
| Windsurf | ⚠️ Flat file | Same as Cursor |
| RooCode | ⚠️ Flat file | Same as Cursor |
| ChatGPT Custom GPT | ⚠️ Truncated | Instructions field ~8K char limit |
| Gemini Gems | ⚠️ Truncated | System instruction length limit |

---

## 🤝 Contributing

New product categories, ingredient database entries, and interaction rules follow a consistent template:

1. **New category**: Define First Principle → Weight Profile → Domain Rules → Anti-Hallucination Rules
2. **New ingredient**: Follow M21 schema (Name / Alias / Category / Ontology / Mechanism / Evidence / Risk / Concentration / Skin Compatibility)
3. **New interaction**: Pair + Type + Mechanism + Evidence Level + IM value

---

*Built with the Reasonix Code Skill Creator format. Evidence levels follow A–E classification. All conclusions should be verified by a dermatologist for medical decisions.*
