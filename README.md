# Team Name: Replace_Your_Team_Name

Replace this README with a short description of your team and solution.

## Team

- Team name:
- Members:
- Track(s) addressed: Data Insights & Visualization / Predictive Analytics / Policy & Intervention Design
- Contact email:
- Language used: Python

## AI and LLM use is restricted

AI or LLM tools (ChatGPT, Claude, Copilot, Gemini, and so on) must not be used
to generate your analysis, findings, report, slides, or policy recommendations.
The analytical and written work must be your team's own.

The only tolerated use is basic coding assistance, such as editor autocomplete
or looking up syntax and error messages. It must not extend to producing the
analysis or the written deliverables.

Reports and notes are checked for signs of AI generation, and all numbers are
independently fact-checked. Submissions that appear substantially AI-generated
may be disqualified.

## What's in this repo

| File / folder | Purpose |
|---|---|
| `01_eda.ipynb` | First entry point. Exploratory Data Analysis. |
| `02 indices and cross dataset.ipynb` | Second entry point. Indices and cross dataset analysis. |
| `requirements.txt` | Packages needed to run the notebooks |
| `data/` | Where the organizer dataset goes. Git-ignored, never commit data |
| `outputs/` | Generated tables, figures, dashboard, and predictions |

## How to run this

**Python teams:**

```bash
pip install -r requirements.txt
jupyter notebook
```

Open and run `01_eda.ipynb` and `02 indices and cross dataset.ipynb`.

This will rebuild everything under `outputs/` from scratch, reading the dataset from `./data/`.

## Rules (please read)

- **Language:** Python or R. Provide exactly one entry point (`src/run_all.py` or `src/run_all.R`) with packages pinned.
- **Data:** use only the dataset the organizers give you, plus any external data you list in `manifest.yml`. External data must be public and must not contain personal records. Read the data from `./data/`. Never commit the dataset, because the repo is public.
- **Reproducibility:** use relative paths, not absolute machine paths. Fix a random seed for any model that uses randomness. Do not download data or models while your code runs, because the judging run is offline.
- **Runtime:** your entry point should finish in about 3 minutes. If you train a heavy model, save the result and commit it instead of training again during the run.

## Notes for reviewers

Add anything a judge should know before reading further (data caveats, known limitations, how to read a specific output file, and so on).
