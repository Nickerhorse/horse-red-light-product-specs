# Method and limitations

## Scope and counting units

This release documents a frozen compilation of published product information, selected AI answer checks, and source-reading records. It does not describe physical testing of the compared commercial devices.

| File | Data rows, excluding header | Unit |
|---|---:|---|
| `data/T1-published-specs.csv` | 11 | Main-sample product record |
| `data/T1-supplementary-rows.csv` | 3 | Additional product record for contradiction checks |
| `data/T2-ai-answer-audit.csv` | 36 | Audit detail, summary, or scoped answer-count record |
| `data/T3-evidence-register.csv` | 61 | Source record, which can describe research, a review, or guidance |

The tables do not share one denominator. Supplementary products stay outside the main product count. T2 includes overlapping details and summaries. T3 sources can discuss overlapping research or methods unrelated to light therapy.

## Product information

The underlying product compilation reviewed business pages, associated policies, and available structured page information on November 17, 2026. Its source log records URL collection and manual reading of individual fields. The sample was assembled for this comparison and associated AI checks; it was not a random sample or a complete market inventory.

Official business pages were used where accessible. The Horseware record identifies retailer sources because official-site access returned HTTP 403. Ortho Equine policy references returned HTTP 404. The source log also records stopping at access or rate restrictions rather than bypassing them. Source type and missing-information notes remain in the exported records.

The US purchasing context was checked where relevant. PbmEquine stock differed by regional context, so a stock statement must retain its region. Package sizes, retailer alternatives, list prices, and policy conflicts remain qualified text. The supplementary EquiCare row retains pair and kit prices in the original single-price field; neither amount is a per-boot price.

`not stated` describes the material reviewed. It does not establish that a feature is absent, that no policy exists, or that no other page provides the information. Published specifications are not independent measurements. Product categories and measurement conditions differ, so irradiance values do not establish an efficacy ranking.

## AI answer audit

T2 separates observations made on November 16 and 17, 2026 from checks recorded on November 17 and 18, 2026. These are historical observations, not live retests.

Verification detail records use T2-V identifiers. Summary records T2-S1 through T2-S4 classify 18 unique finding IDs: 14 correct, 2 partially correct, 1 incorrect, and 1 not stated. The unit is a finding ID, not every table row or subclaim. A grouped PbmEquine finding remains grouped. The unopened Hock Helper finding is excluded. Use either detail records or their summaries when counting this subset.

Contradiction records use T2-C identifiers. T2-C-SUM reports 1 genuine error among 5 flagged items after restoring price units, package context, and timing conditions. These items are a separate audit subset; they do not extend the verification denominator.

The remaining measures describe specific answer sets. For windpuffs, the scope is the recorded question and its 4 runs. For the abscess questions, the purchase-recommendation measure uses 10 answers, while light-specific evidence and safety measures use 2. Questions without a light-specific prompt remain in the recommendation denominator. A lack of a purchase recommendation is not necessarily an explicit rejection.

Citation measures count an answer once for an exact cited domain, even if that answer cites multiple pages on the domain. Listed-only sources are excluded. Domain counts overlap because one answer can cite several domains. AI statements are observations being audited; they are not clinical evidence.

The export contains selected findings, counts, and provenance references rather than all original prompts, answers, and retrieval logs. The internal references make the compilation traceable within its source archive, but this package alone does not reproduce every run or extraction step. It does not estimate AI accuracy across other questions, models, or dates.

## Evidence register

T3 transcribes the supplied source-reading records. Each record retains source identity, species, body site, intervention, design, result, and limitations. Merged source identifiers are preserved in `source_id`. A record can refer to guidance, a review, or an experimental study, and the register includes care methods other than light therapy.

Reading depth varies. Some records use abstracts, institutional summaries, or selected full-text sections; `limits` identifies these constraints. The source log records use of an open literature API when access to an abstract page was restricted, and a PDF where an institutional page redirected unsuccessfully. These routes do not imply that every source was read in full.

The register is not a systematic review of commercial hoof wraps. It does not provide a pooled effect estimate or a common quality score. Study populations, anatomical sites, interventions, and outcomes differ. Horse counts in reviews can cover several studies. The `hoof_or_sole_tested` field must be read alongside `modality`: the positive record describes cooling, not a light-device experiment.

## Reuse and release boundaries

Use a CSV parser that preserves quoted fields and text qualifications. Do not replace missing-information text with zero or silently convert mixed package amounts into per-item prices. Keep source references and limitation fields with any extracted values. [DATA-DICTIONARY.md](DATA-DICTIONARY.md) supplies the complete column definitions.

This release includes audit corrections made to the supplied CSV values before publication. [CHANGELOG.md](CHANGELOG.md) records version v1.0.0; [CITATION.cff](CITATION.cff) provides attribution metadata. The package includes source references, not copies of all third-party pages or publications. Cite original sources when reusing their findings.

Compiled by Nicker, a horse care brand that offers an LED light wrap for horses. No Nicker product is included in the comparison.

Conflict of interest: The compiler has a commercial interest in the category. The dataset does not constitute independent testing of its own product.
