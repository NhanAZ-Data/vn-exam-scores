# Vietnam Exam Scores

This repository contains public exam score data from Vietnam and scripts for reproducible analysis. It covers national high school exams from 2016 to 2019, high school graduation exams from 2020 to 2026, and legacy university and college entrance exams from 2013 to 2014.

The repository aims to meet these goals.

- Keep raw sources traceable with provenance.
- Produce compact analysis tables.
- Avoid double-counting aggregate files.
- Document whether sources include identifying fields such as names and dates of birth.
- Validate outputs with reproducible scripts.

## Dataset status

- The 2013-2014 legacy university and college entrance data contains 2,412,155 rows.
- The canonical high school exam data from 2016 to 2026 contains 10,865,001 rows.
- The legacy and high school datasets contain 13,277,156 canonical rows in total.
- The 2026 data was cross-checked against the independent `anhdung98/diem_thi_2026` source. Candidate number sets and mapped score fields match exactly.
- Government portal workbooks for the 2025 CT2018 and CT2006 exams were downloaded and checked against canonical row counts.

## Repository structure

```text
.
├── data/
│   ├── analysis/   # Analysis tables generated from raw data
│   └── summary/    # Compact score distributions and subject statistics
├── docs/           # Project documentation
├── metadata/       # Source registry, manifests, coverage reports, and code lists
├── scripts/        # Build and validation scripts
└── sources/
    ├── du-lieu-diem-thi/   # Canonical raw data Git submodule
    └── crosscheck/         # Downloaded data used for cross-checking
```

The `sources/du-lieu-diem-thi` submodule points to `https://github.com/sdgedfegw/du-lieu-diem-thi` at commit `1178a012c8af3f07f7d40c614dc61fb342687e46`.

## Clone the repository

```powershell
git clone --recurse-submodules https://github.com/NhanAZ-Data/vn-exam-scores.git
cd vn-exam-scores
git lfs pull
```

If you already cloned the repository but do not have the submodule:

```powershell
git submodule update --init --recursive
git lfs pull
```

## Install dependencies

```powershell
python -m pip install -r requirements.txt
```

## Rebuild the analysis tables

Run these scripts in order.

```powershell
python scripts/build_subject_summaries.py
python scripts/build_legacy_features.py
python scripts/validate_repo.py
```

The main outputs include the following files.

- `data/summary/subject_score_distribution.csv` maps each year, subject, and score combination to a count.
- `data/summary/year_subject_stats.csv` contains counts, means, standard deviations, and percentiles by year and subject.
- `data/analysis/legacy_2013_2014_features.csv` contains derived fields for the legacy dataset, including name parts and date-of-birth components.
- `data/analysis/legacy_name_score_stats.csv` contains score summaries by family name or given name for groups with at least 30 records.
- `data/analysis/legacy_birth_month_score_stats.csv` contains score summaries by birth month.

## Documentation

- [Data sources](docs/DATA_SOURCES.md)
- [Data dictionary](docs/DATA_DICTIONARY.md)
- [Privacy and analysis limits](docs/PRIVACY_AND_ANALYSIS_LIMITS.md)
- [Coverage gap report](metadata/gap_report.md)

## Important notes

- The raw source file `du_lieu_diem_thi_2016-2025.csv` is an aggregate convenience file. The summary scripts exclude it to avoid double-counting.
- The 2013-2014 source contains `HovaTen` and `NgaySinh`. The derived feature output splits names and date-of-birth values into components, so it still contains identifying information. Review the privacy guidance before sharing it.
- Some legacy names use the TCVN3 font encoding. `scripts/build_legacy_features.py` converts detected names and name tokens to Unicode in derived outputs. The `name_font_fixed` column identifies converted rows.
- The reviewed bulk datasets from 2016 to 2026 do not contain names or dates of birth. Do not infer either from candidate numbers.
- Name and birth-month analyses can show associations. They do not establish causation without a study design that controls for relevant factors.
