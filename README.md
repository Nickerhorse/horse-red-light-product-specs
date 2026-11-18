# horse-red-light-product-specs

Compiled by Nicker, a horse care brand that offers an LED light wrap for horses. No Nicker product is included in the comparison.

Conflict of interest: The compiling brand participates commercially in this product category.

## Where should a reader start?

Use this repository to inspect the CSV records and follow their source references. Start with the [column dictionary](DATA-DICTIONARY.md), then read the [method and limitations](METHOD.md) before filtering or counting rows. The repository separates product observations, AI answer checks, and evidence summaries so that a source record is not mistaken for a product test.

## How are the files arranged?

```text
data/
  T1-published-specs.csv
  T1-supplementary-rows.csv
  T2-ai-answer-audit.csv
  T3-evidence-register.csv
DATA-DICTIONARY.md
METHOD.md
CHANGELOG.md
CITATION.cff
LICENSE.md
```

T1 holds 11 main product rows and a separate file of 3 supplementary rows. T2 has 36 audit records with explicit counting scopes. T3 has 61 source records, including guidance and reviews as well as experimental research. Row counts omit headers. The supplementary products do not enlarge the main comparison sample.

All CSV files use comma delimiters and a header row. Import the files with a CSV reader that respects quoted fields: commas inside a description are not new columns. Keep mixed price descriptions and qualification text as strings rather than forcing an entire column into numeric values.

## How should records be compared?

Retain `row` for product references and `record_id` for audit and evidence references. T2 `source_id` identifies the underlying audit provenance; it is not a universal foreign key into T1 or T3. Source fields can contain combined references or shortened page paths, so preserve the original text when following a record.

For AI verification, count the individual finding records or use their summary rows. Combining both counts the same findings again. For answer-level measures, read `scope_note` before using `numerator` and `denominator`. The files describe selected observations; they do not estimate accuracy across all AI answers.

T3 includes sources on other care methods and species. Read `modality`, `species`, `design`, and `limits` together before treating a result as relevant to a horse light device.

## How should this repository be cited?

Authors: Nicker and Muhammed Veysel Erin (https://orcid.org/0009-0004-2368-3622). The release citation is:

Nicker; Muhammed Veysel Erin. Horse red-light hoof and leg products: published specifications, AI answer audit and evidence register, November 2026 (Nicker). Version v1.0.0. Zenodo. DOI: https://doi.org/10.5281/zenodo.24352070.

[CITATION.cff](CITATION.cff) supplies citation metadata. [CHANGELOG.md](CHANGELOG.md) identifies the release contents. The archive description is at the DOI above. Reuse is under CC BY 4.0, linked in [LICENSE.md](LICENSE.md).
