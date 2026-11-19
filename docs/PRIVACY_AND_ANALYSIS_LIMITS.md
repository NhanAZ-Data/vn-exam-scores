# Privacy and analysis limits

## Identifying fields

The 2013-2014 legacy raw source contains full names and dates of birth. The repository stores that source in its Git submodule. The derived row-level feature file splits names and birth dates into components. It includes family name, given name, birth day, birth month, and two-digit birth year, along with candidate and exam fields. These components remain identifying information.

Do not share row-level identity data without a separate legal and ethical review.

## Data from 2016 to 2026

The reviewed bulk sources contain candidate numbers, province or exam-board codes, subjects, and scores. The project has not found a valid bulk source with names or dates of birth for these years.

Do not infer a person's birth month, gender, region, or identity from a candidate number unless a source explicitly publishes that information.

## Causality limits

Tables grouped by name or birth month support exploratory analysis. They do not show that a name or birth month causes higher or lower scores.

A causal study would need to account for the following factors.

- Exam year.
- Province or exam board.
- Legacy exam block, school, and major.
- Exam structure and subjects.
- Gender and socioeconomic distributions, when available.
- Changes to the education system and scoring rules over time.
