# Coverage and data gaps

## Coverage and cross-checks

- High school exam score data from 2016 to 2026 is available locally, with 10,865,001 canonical rows.
- The 2026 data was cross-checked against the independent `anhdung98/diem_thi_2026` release. The candidate-number sets and compared score and language fields match exactly.
- Government portal workbooks for the 2025 CT2018 and CT2006 exams have row counts that match the canonical CSV files. The CT2018 workbook has 1,131,136 rows and the CT2006 workbook has 22,090 rows.

## Identity fields

- The 2013-2014 legacy university and college entrance data contains `HovaTen` and `NgaySinh`.
- The reviewed 2016-2026 high school score data contains candidate numbers, province or exam codes, subjects, and scores. It does not provide names or dates of birth as reusable bulk fields.

## Missing or limited data

- The current canonical source has no raw file for 2015.
- The reviewed bulk datasets from 2016 to 2026 do not contain names or birth dates. Inferring them from candidate numbers or score lookup pages would be speculative unless a source explicitly publishes them.
- Province codes are not stable across all years. The 2026 data uses the post-reorganization list of 34 provinces. Earlier years use older lists with 63 or 64 codes.
- Post-exam regrading scores are not consistently available in the reviewed public raw data. Most releases identify themselves as pre-regrading snapshots or do not include regrading results.
- The official candidate-number lookup portal is useful for spot checks. It is not a clean bulk source and may have CAPTCHA, rate limits, or restrictive terms.

## Causality limits

Name and birth-month analyses show associations. They do not establish causal effects by themselves. A credible causal design would need to account for province, year, school or exam block, cohort effects, family and socioeconomic factors, and a defensible identification strategy. The feature tables support exploratory analysis and hypothesis generation.

## Privacy handling

The raw source retains the 2013-2014 identity fields. The derived row-level feature file splits names and birth dates into components, but it still contains identifying information. Aggregated tables omit row-level birth dates. The name aggregates still contain name parts. Do not publish row-level identity data without a separate legal and ethical review.

## Legacy name cleaning

Some 2013-2014 names use TCVN3-style legacy characters. `scripts/build_legacy_features.py` converts detected names and name tokens to Unicode in derived outputs while leaving the raw source unchanged. The `name_font_fixed` column marks converted rows.
