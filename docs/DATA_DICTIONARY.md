# Data dictionary

## High school exam data from 2016 to 2026

| Field | Description |
| --- | --- |
| `SBD` | Candidate number. |
| `Nam` | Two-digit exam year in raw files, such as `24`, `25`, or `26`. |
| `Tinh` | Province or exam-board code. The coding scheme varies by period. |
| `Toan`, `NguVan`, `VatLy`, `HoaHoc`, `SinhHoc`, `LichSu`, `DiaLy`, `NgoaiNgu` | Subject scores. |
| `GDCD` | Civic education score, mainly in the GDPT 2006 schema. |
| `KinhTePhapLuat`, `TinHoc`, `CongNgheCongNghiep`, `CongNgheNongNghiep` | Subjects in the newer 2025 and 2026 schema. |
| `MaMonNgoaiNgu` | Language code. For example, `N1` identifies English where present. |
| `KhoiA`, `KhoiA1`, `KhoiB`, `KhoiC`, `KhoiD`, `KhoiA02`, `KhoiC01`, `KhoiD07` | Precomputed exam-combination scores from the source. |
| `KHTN`, `KHXH`, `TongDiemKHTN`, `TongDiemKHXH` | Composite-test totals or averages for applicable exam periods. |

`metadata/subjects.csv` lists source column identifiers and their original Vietnamese labels. The `label_vi` column remains as source metadata.

## Legacy data from 2013 to 2014

| Field | Description |
| --- | --- |
| `Nam` | `13` or `14`. |
| `Tinh` | Province or city code. It may be blank on some rows. |
| `KyThi` | `DH` or `CD`, for university or college entrance exams. |
| `DH` | School code. |
| `Khoi` | Exam-block code. |
| `SBD` | Candidate number. |
| `HovaTen` | Candidate's full name in the raw source. |
| `NgaySinh` | Date in `ddmmyy` format. `000000` means blank. |
| `Mon1`, `Mon2`, `Mon3`, `TongDiem` | Integer-encoded scores. For example, `775` represents `7.75`. |

The feature output is `data/analysis/legacy_2013_2014_features.csv`. It splits source names and birth dates into these fields:

| Field | Description |
| --- | --- |
| `family_name` | Family name. |
| `given_name` | Given name. |
| `middle_name_token_count` | Number of middle-name tokens. |
| `birth_day`, `birth_month`, `birth_year_yy` | Parsed date-of-birth components. |
| `birth_date_valid` | Whether the date of birth parsed as valid. |
| `name_font_fixed` | Whether a name or name token was converted from TCVN3 to Unicode. |
| `score_mon1`, `score_mon2`, `score_mon3`, `score_total` | Scores converted to the standard decimal scale. |
