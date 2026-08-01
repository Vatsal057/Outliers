# Team Name: Replace_Your_Team_Name

Replace this README with a short description of your team and solution.

## Team

- Team name:
- Members:
- Track(s) addressed: Data Insights & Visualization / Predictive Analytics / Policy & Intervention Design
- Contact email:
- Language used: Python / R

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
| `report.pdf` | Main findings report (replace the placeholder) |
| `slides.pptx` | Your filled-in 12-slide solution deck |
| `docs/policy_note.pdf` | Recommendations note |
| `src/run_all.py` or `src/run_all.R` | Single entry point. Running this reproduces everything in `outputs/` |
| `requirements.txt` or `renv.lock` | Packages needed to run your entry point (Python / R) |
| `data/` | Where the organizer dataset goes. Git-ignored, never commit data |
| `manifest.yml` | Lists every file your submission produces |
| `claims.json` | Every factual or numeric claim in your report, with how it can be checked |
| `outputs/` | Generated tables, figures, dashboard, and predictions |
| `Dockerfile` | Optional. Containerizes your entry point for a reproducibility bonus |

## How to run this

**Python teams:**

```bash
pip install -r requirements.txt
python src/run_all.py
```

**R teams:** delete `src/run_all.py`, add `src/run_all.R`, and pin your packages
with `renv.lock` (`renv::snapshot()`) or an `install.R` script. Judges run:

```bash
Rscript -e "renv::restore(prompt = FALSE)"   # or: Rscript install.R
Rscript src/run_all.R
```

Either way, this must rebuild everything under `outputs/` from scratch, reading the dataset from `./data/`.

## Rules (please read)

- **Language:** Python or R. Provide exactly one entry point (`src/run_all.py` or `src/run_all.R`) with packages pinned.
- **Data:** use only the dataset the organizers give you, plus any external data you list in `manifest.yml`. External data must be public and must not contain personal records. Read the data from `./data/`. Never commit the dataset, because the repo is public.
- **Reproducibility:** use relative paths, not absolute machine paths. Fix a random seed for any model that uses randomness. Do not download data or models while your code runs, because the judging run is offline.
- **Runtime:** your entry point should finish in about 3 minutes. If you train a heavy model, save the result and commit it instead of training again during the run.

## Dashboard rules (read before you build)

- **Code-based dashboards only.** Build with Plotly/Dash, Streamlit, Bokeh, Altair/Vega, Observable, or plain HTML/JS, so `src/run_all.py` rebuilds it and it exports to `outputs/figures/dashboard.html`.
- **Tableau and Power BI are not accepted** for the dashboard. The pipeline cannot run or check `.twbx`/`.pbix` files, so they will not count toward the Visualisation and presentation score.
- **Never upload the dataset to any public service** (Tableau Public, Power BI "publish to web", public Google Sheets, and so on). The data contains student assessment records, and publishing it risks re-identifying real children. Doing so disqualifies that data product.

## Notes for reviewers

Add anything a judge should know before reading further (data caveats, known limitations, how to read a specific output file, and so on).
