# Data sources

## Canonical source

The primary raw data source is [`sdgedfegw/du-lieu-diem-thi`](https://github.com/sdgedfegw/du-lieu-diem-thi).

The repository currently uses commit `1178a012c8af3f07f7d40c614dc61fb342687e46`.

The source covers three exam periods.

- University and college entrance exams from 2013 to 2014.
- National high school exams from 2016 to 2019.
- High school graduation exams from 2020 to 2026.

This repository includes the source as a Git submodule at `sources/du-lieu-diem-thi`.

## Cross-check sources

The repository records reviewed, downloaded, and cross-checked sources in `metadata/source_registry.csv`.

Notable sources include the following.

- `anhdung98/diem_thi_2026` provides 2026 CSV data with a `dm1` through `dm13` schema. The repository maps and compares it with the canonical data.
- The Government News Portal and Government E-Portal published 2025 CT2018 and CT2006 XLSX files. The repository stores the downloaded files under `sources/crosscheck/baochinhphu/2025`.
- The Vietnam Ministry of Education and Training's 2026 lookup portal confirms the lookup channel and provincial links. The project does not crawl it for bulk data.
- VnExpress provides 2026 lookup and summary pages for spot checks and rankings. It is not a canonical source.

## Canonical source policy

- Prefer bulk files with clear structures that support reproducible analysis.
- When a source provides both aggregate and year-specific files, use the year-specific files to avoid double-counting.
- Record crawlers and candidate lookup pages for auditing or spot checks when they are not suitable canonical bulk sources.
