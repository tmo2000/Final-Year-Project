# Yoruba Proverbs Dataset — Data Dictionary (UNL Yoruba Proverbs Archive)

## Source
This dataset is derived from the University of Nebraska–Lincoln Yoruba Proverbs Archive:
- https://yoruba.unl.edu/yoruba1.html

The archive provides Yoruba proverb entries grouped by website sections ("Parts") and includes Yoruba text, literal translations, and interpretive explanations.

---

## Dataset Files

### 1) `yoruba_proverbs_clean.csv`
**Purpose:** Full cleaned archive of all scraped entries from the website, preserving ordering, metadata, notes/variants, and completeness.

**Use cases:**
- Dataset transparency and reproducibility
- Exploratory analysis of the full archive
- Tracking provenance back to the source URL

---

### 2) `yoruba_proverbs_eval_final.csv`
**Purpose:** Evaluation-ready subset used for benchmarking LLM outputs.

**Filtering rules (evaluation subset):**
- Includes only rows where all of the following are present:
  - Yoruba proverb text
  - English literal translation
  - Gold interpretation
- Removes duplicates (so one proverb is not double-counted in evaluation)

**Use cases:**
- LLM translation and interpretation experiments
- BLEU/BERTScore for literal translation fidelity
- Semantic similarity for interpretation alignment
- Cultural alignment/bias scoring (e.g., Hofstede dimensions)

---

## Key Concepts (Annotation Layers)

### Layer 1 — Yoruba Proverb (Original)
The proverb in Yoruba orthography, including diacritics where available (ẹ, ọ, ṣ, ń, etc.).

### Layer 2 — Literal Translation (Gold Reference)
A surface-level, direct English translation of Yoruba words/phrases.
- Faithful to the wording
- Not a moral explanation

**Used for:** literal translation fidelity metrics (e.g., BLEU, BERTScore).

### Layer 3 — Gold Interpretation (Gold Reference)
A culturally grounded explanation of the proverb’s meaning and lesson.
- Explains implied moral or wisdom
- Often expands beyond literal wording for cultural clarity

**Used for:** semantic evaluation and bias/cultural alignment analysis.

---

## Data Dictionary (Column Definitions)

### Identifier & Ordering Fields

| Column | Type | Meaning |
|-------|------|---------|
| `entry_id` | int/string | Unique ID for each scraped entry. Useful for joining datasets and preserving website order. |
| `part_id` | int | Numeric “Part” identifier corresponding to website section grouping. |
| `part_code` | string | Website part code (e.g., "1A", "2B"). Mirrors the archive’s internal structure. |
| `part_theme` | string | Theme label for the section (curated by the archive). Enables per-theme evaluation and analysis. |
| `letter` | string | Alphabetical grouping tag (if present). Helps preserve website order. |

---

### Linguistic Content Fields

| Column | Type | Meaning |
|-------|------|---------|
| `yoruba` / `proverb_yoruba` | string | Yoruba proverb text (with diacritics preserved where available). |
| `english_literal` / `translation_english` | string | Gold literal English translation (surface meaning). |
| `interpretation_gold` / `interpretation_english` | string | Gold interpretation/explanation of meaning. |

---

### Metadata Fields

| Column | Type | Meaning |
|-------|------|---------|
| `notes` | string | Additional notes from the archive, e.g., “variant of …”, commentary, or editorial remarks. |
| `source_url` | string | URL pointing to the proverb’s page on the UNL archive, providing traceability and provenance. |

---

## Label Semantics

### `part_theme`
The archive groups proverbs by sections that reflect broad cultural themes (e.g., social behavior, wisdom, community).
- Not machine-generated
- Curated by the source
- Useful for stratified evaluation (model performance by theme)

### `notes`
The notes field often contains:
- “Variant of …” (the proverb appears as a variant)
- Editorial clarifications
- Cross-references to similar entries

**Important:** rows that are purely notes/variants may be excluded from evaluation if translation/interpretation is missing.

---

## Cleaning & Preprocessing Decisions

### Encoding
- Yoruba diacritics are preserved using UTF-8.
- Excel-friendly outputs should use UTF-8 with BOM (`utf-8-sig`) or `.xlsx`.

### Evaluation filtering
The evaluation dataset excludes entries with missing:
- Yoruba proverb text
- Gold literal translation
- Gold interpretation

### Deduplication
Duplicate Yoruba proverbs may occur due to variants or repeated listings.
For evaluation, duplicates should be removed so that each proverb is counted once.

---

## Relationship Between Clean and Eval Datasets

| Feature | Clean Dataset | Eval Dataset |
|--------|---------------|-------------|
| Includes all scraped rows | ✅ | ❌ |
| Preserves variants/notes-only rows | ✅ | ❌ (if missing gold refs) |
| May contain duplicates | ✅ | ❌ |
| Guaranteed gold translation + interpretation | ❌ | ✅ |
| Intended for LLM benchmarking | No | Yes |

---

## Intended Evaluation Usage
For each proverb, an AI model produces:
- `model_translation` (literal English translation)
- `model_interpretation` (meaning/lesson)

These are compared against:
- Gold literal translation (`translation_english`)
- Gold interpretation (`interpretation_english`)

This enables:
- Literal fidelity scoring (BLEU/BERTScore)
- Interpretation alignment scoring (semantic similarity)
- Cultural alignment/bias analysis (e.g., Hofstede dimension scoring)

---