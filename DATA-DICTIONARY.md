# Data dictionary

This dictionary covers every column in the four CSV files under `data/`. The files use UTF-8 text, comma separators, and quoted fields where needed. A comma inside a quoted field is part of the value. Column order and identifiers are retained from the supplied exports.

## Shared conventions

- Treat descriptive fields as text. A field can combine values, units, conditions, and qualifications.
- `not stated` means that information was not available in the material reviewed for that record. It does not prove absence. Longer qualifications explain access failures, uncertain units, or other limits.
- A blank or a missing-value phrase is not a measured zero. T2 numerators can contain an actual zero.
- Read dates in their recorded form. T1 retrieval dates, T2 observation dates, T2 check dates, and T3 reading dates describe different events.
- Source fields may combine references with ` + ` or semicolons. Some retain relative paths or abbreviated paths containing `...`; they are provenance text, not necessarily a single directly resolvable URL.
- Record identifiers are local references. Shared publications, overlapping observations, and summary rows mean row counts are not automatically counts of independent observations.

## T1: product tables

The following complete schema applies separately to both `data/T1-published-specs.csv` and `data/T1-supplementary-rows.csv`. The main table has 11 product rows. The supplementary table has 3 rows used for contradiction checks; exclude them from main-sample counts.

| Column | Stored form and meaning | Interpretation limit |
|---|---|---|
| `row` | Text identifier: numeric labels in the main table; labels prefixed with E in the supplementary table. | A reference label, not a rank or a sample weight. |
| `brand` | Brand or business attribution as recorded, sometimes including the distributor relationship. | Does not imply independent authorship of the specification. |
| `product` | Product name, with category or package qualifications where recorded. | Includes products other than hoof boots. |
| `price_single_usd` | USD price text retained in the original single-price field. May include list prices, retailer alternatives, pair or kit amounts, or package ambiguity. | Not consistently a numeric per-item price. Supplementary EquiCare pair and kit prices remain here as labeled. |
| `price_pair_usd` | Pair-price text, alternative package amounts, or an explanation of the available package. | Do not assume the entire field is a numeric price for a pair. |
| `wavelengths_nm` | Published wavelengths in nanometers, or a qualified description of missing or conflicting statements. | A page statement, not an independent spectrum measurement. |
| `irradiance_mw_cm2` | Published irradiance in milliwatts per square centimeter, including approximations or thresholds. | Read with measurement location; values do not establish comparable test conditions. |
| `irradiance_measurement_location` | Stated location, distance, or measurement-context wording. | A surface reference without a documented method does not establish a full measurement protocol. |
| `led_count` | Published LED count; may also describe chips or uncertainty about per-item versus total count. | LEDs and chips are different units. |
| `stated_coverage` | Anatomical coverage described by the source. | Does not demonstrate light reaching tissue or clinical benefit. |
| `timer_auto_off` | Timer or automatic shutoff statement, or session-duration context when no timer is stated. | Suggested session length does not establish an automatic timer. |
| `battery_runtime` | Published runtime, session count, or a qualification of missing information. | Battery capacity is not runtime; a customer comment is identified where relevant. |
| `charge_time` | Published full-charge duration or a missing-information qualification. | A charging connector type does not give a charging duration. |
| `ip_rating` | Published ingress-protection information or related source wording. | Cleaning or immersion instructions are not a numeric IP rating. |
| `returns` | Return-window and condition text, including shipping responsibility, conflicts, or access failures. | Apply the recorded conditions; do not convert an unread policy to a zero-day window. |
| `warranty` | Warranty duration and scope, variable terms, or missing-information wording. | Not a guarantee of device lifespan. |
| `source_url` | Product, policy, retailer, or structured-page references used for the record. | May combine addresses with shortened paths; inspect each component. |
| `source_type` | Recorded provenance category, distinguishing official business material from retailer material. | Describes where the information came from, not its independent validation. |
| `retrieved_date` | Date on which the source information was retrieved. | A historical snapshot, not a current availability check. |
| `note` | Context, conflicts, use restrictions, regional differences, or other qualifications. | Retain with the values it qualifies. |

## T2: AI answer audit

`data/T2-ai-answer-audit.csv` contains 36 records. Its rows use different counting units. Read `measure` and `scope_note` together before selecting a subset.

| Column | Stored form and meaning | Interpretation limit |
|---|---|---|
| `record_id` | Local audit identifier. T2-V identifies verification details; T2-S identifies their summaries; T2-C identifies contradiction checks, including T2-C-SUM. Other identifiers name scoped answer or citation measures. | Details and summaries overlap; an identifier is not necessarily an AI run. |
| `measured_on` | Date of the AI observation or run set being audited. | Distinct from the later source-check date. |
| `measure` | Name of the verdict, count, answer behavior, or citation measure. | Defines what the numerator counts. |
| `numerator` | Integer count for the measure in that row. | A detail row can encode a single finding; do not pool different measures. |
| `denominator` | Integer size of the eligible set for that measure. | Can refer to finding IDs, flagged items, or answer runs. It is not one common sample across the file. |
| `scope_note` | Inclusion rules, exclusions, grouping, run references, prompt scope, and interpretation cautions. | Required for interpreting the count; some finding IDs contain grouped subclaims. |
| `official_value` | Checked source statement or corrected value for a finding; otherwise missing-information wording. | Can include mixed units, conditions, or amounts not found. It is not an AI output column. |
| `official_source_url` | Business-source reference for a checked finding, or `not stated` for a run-derived measure or summary without a separate page reference. | May contain combined or shortened paths. Use `source_id` and `scope_note` for run-derived provenance. |
| `checked_on` | Date of the source or record check. | Does not mean the AI observation occurred on that date. |
| `source_id` | Underlying finding, data-card section, run-record, or report reference. | Not a standardized cross-file join key; local source materials are not all included in this package. |

## T3: evidence register

`data/T3-evidence-register.csv` has 61 source records. A record can summarize a study, review, or guidance page. It is not necessarily an independent experiment, an equine source, or a source about light therapy.

| Column | Stored form and meaning | Interpretation limit |
|---|---|---|
| `record_id` | Local identifier for the exported source record. | A record key, not a study-quality score. |
| `source_id` | Original source-reading identifiers; merged references can be separated by semicolons. | Several internal references may point to one exported record. |
| `authors` | Author names or institutional attribution recorded for the source. | Source authors are distinct from dataset authors. |
| `year` | Recorded publication year or missing-information wording. | Online, issue, and update dates can differ; consult `limits`. |
| `title` | Source title as transcribed. | Identifies the source rather than a conclusion of this dataset. |
| `journal_or_publisher` | Journal, institution, publisher, or source host. | Hosting does not by itself establish a study design. |
| `doi_or_pmid` | DOI, PMID, PMC reference, combined identifiers, or `not stated`. | May contain several identifier formats rather than a single DOI. |
| `url` | Address used to identify the source. | Can point to an abstract, institutional page, manuscript, or full text. |
| `source_type` | Recorded category: randomized controlled trial, experimental study, systematic review, review, or guidance. | Category alone does not establish applicability or quality. |
| `species` | Species or patient group covered by the source. | Not every source concerns horses. |
| `tissue_or_site` | Anatomical site, tissue, or topic represented in the source. | A skin or muscle result does not establish a hoof result. |
| `modality` | Intervention or care method, including explicit non-light methods and `none`. | `none` is distinct from a missing wavelength or setting. |
| `wavelength_nm` | Light wavelengths in nanometers when recorded, or `not stated`. | Does not specify all device settings or validate a product. |
| `dose_or_settings` | Text describing exposure, device settings, timing, or other intervention details. | Not a normalized numeric field; missing settings have not been calculated. |
| `n_horses` | Recorded horse count or missing-information wording. | A review total is not a trial sample. `not stated` is not zero and may occur for non-equine sources. |
| `design` | Study design or guidance description, with population or comparison details where recorded. | Read before interpreting any sample count or result. |
| `main_result` | Extracted finding or guidance summary. | Keep linked to the population, intervention, and limits; it is not a commercial product claim. |
| `limits` | Reading scope, missing methods, bias concerns, date distinctions, and limits on transfer to other uses. | Abstract-only reading is not full-text appraisal. |
| `hoof_or_sole_tested` | Recorded label: `yes`, `no`, or `not stated`. | `yes` does not mean light therapy was tested; the positive record concerns hoof-wall cooling. |
| `read_on` | Date the source was read for the underlying register. | Distinct from publication and update dates. |
