# Outliers — Datathon 2026

Analysis of the Akshara Foundation **GP Contest** maths assessments (Karnataka government schools, grades 4–6, three years), combined with district-level secondary data from **Karnataka At A Glance 2024-25** and **ASER 2024**.

Two notebooks. Everything they produce lands in `outputs/`.

---

## Notebooks

### `01_eda.ipynb` — primary data
Loads the nine Excel files (3 grades × 3 years), builds per-child scores and competency mastery, and works through the exploration.

- File-level checks: which competencies appear on which paper, whether question names and competency labels hold still across years, whether the same GPs were assessed each year
- Scores by grade, year, gender, division, district; below-floor rates (<50% of the paper)
- Variance decomposition across division → district → block → cluster → GP
- Competency-level mastery: weakest areas, mean-vs-spread quadrant (central fix vs local fix), grade 4→6 progression, per-district heatmap
- Question-name analysis: presentation effects (word problem / pictorial / abstract), the carry–borrow cliff, non-attempt runs at the end of papers, item-level reliability
- Blocks that moved between the first and last year, and GPs that beat their own block consistently

### `02_indices_and_cross_dataset.ipynb` — indices + secondary data
Builds two district indices from KAG and compares them against primary mastery and ASER.

- **Infrastructure Access** — all-weather road access, mobile connections per 1,000 enrolled children
- **Education Access** — out-of-school rate (inverted), gender parity in enrolment
- Both min–max scaled with equal weights, so they are relative positions within Karnataka, not absolute levels
- Name-matching audit (no fuzzy matching), leave-one-component-out sensitivity check, quadrant plots, a descriptive regression of mastery on the two indices, and residuals as a way to rank which districts are worth asking about
- Within-district contrast: education districts sharing a parent revenue district share every index value, so any mastery gap between them sits below district level

---

## Reading the numbers

Four things constrain everything here:

1. There is no `Year`, `Grade` or `Score` column — year and grade come from the file path, score is the row sum of Q1–Q20.
2. `Unique Identifier` does not follow a child across years. Year comparisons are cohorts in a place, not the same children growing up.
3. A `0` is either a wrong answer or a question never reached. Every mastery figure is **demonstrated** mastery; section 7.5 sizes the non-attempt problem.
4. Each file has its own competency mapping and question names. The nine papers are nine instruments, so cross-file comparisons are scoped to the shared core, and the item-level trend is the only fully like-for-like comparison across years.

Index weights are a convention, not a finding. Ballari, Raichuru and Vijayanagara report zero out-of-school children, so their Education Access index uses one component instead of two — the notebook rebuilds the ranking without them so it is clear which version is being quoted. Internet Connections and Dropout Ratio are excluded from KAG as data issues (see section C1).

---

## Running it

```bash
pip install pandas numpy matplotlib seaborn scipy openpyxl
```

Expected layout, all paths relative:

```
Primary_Dataset/<year>/GPContest_Grade_<n>_<year>.xlsx
Secondary_Dataset/KAG_2024-25_Secondary_Data_Extract.xlsx
Secondary_Dataset/ASER_2024_Karnataka_Rural_Extract.xlsx
outputs/            # created by the notebooks
```

Run `01` first — `02` reads its district × grade × competency cache. Every chart is saved to `outputs/figures/` as well as shown inline. Seed is fixed at 42.

**The raw primary Excel files are not committed.** The district-level CSVs written to `outputs/` are.

---

## Sources

| Dataset | Publisher | Level |
|---|---|---|
| GP Contest assessments | Akshara Foundation | child (down to Gram Panchayat) |
| Karnataka At A Glance 2024-25 (tables 9.3a, 9.4, 10.3a, 10.4a, 10.5a, 10.8) | Directorate of Economics & Statistics, Govt. of Karnataka | district |
| ASER 2024 Karnataka Rural | ASER Centre / Pratham | district (30 of 31) |

ASER is used only to validate the district ranking, never as an index input.
