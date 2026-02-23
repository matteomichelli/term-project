# Data Wrangling Documentation

## Overview
All data wrangling was performed using **Tableau Prep**. Two cleaned output files were produced from ten raw input files. The goal was to produce clean, analysis-ready datasets for use in Tableau Desktop visualizations.

---

## Source 1: Natural Stat Trick (NST)

### Raw Files
`games_2021.csv`, `games_2022.csv`, `games_2023.csv`, `games_2024.csv`, `games_2025.csv`

### Steps Performed

**Step 1 — Added Season column**
Each file does not include a season identifier. A calculated field named `Season` was added to each input step with a fixed value matching the year (e.g. `2021`, `2022`, etc.) so that rows could be identified by season after combining.

**Step 2 — Removed unnecessary columns**
The following columns were dropped as they are not relevant to the decision analysis:
`TOI`, `FF`, `FA`, `FF%`, `SF`, `SA`, `SF%`, `ROW`, `OTL`, `Point %`, `HDGF`, `HDGA`, `HDGF%`, `HDSH%`, `HDSV%`

**Step 3 — Unioned all 5 seasons**
All five files were unioned into a single table using Tableau Prep's Union step, producing 160 rows (32 teams × 5 seasons).

**Step 4 — Output**
Saved as `games_2021-25.csv` — 160 rows, 19 columns.

### Issues Encountered
- No missing values found across any season
- 2025 season contains only 58 games per team as the season was not complete at time of download

---

## Source 2: MoneyPuck

### Raw Files
`teams_2021.csv`, `teams_2022.csv`, `teams_2023.csv`, `teams_2024.csv`, `teams_2025.csv`

### Steps Performed

**Step 1 — Filtered to 5-on-5 situations only**
MoneyPuck tracks five game states: `all`, `5on5`, `4on5`, `5on4`, and `other`. Only `5on5` rows were kept. This isolates structural team quality independent of power play talent, which is driven by individual player skill rather than roster construction strategy (Macdonald, 2012).

**Step 2 — Removed unnecessary columns**
Over 100 columns were dropped. Only the following were kept:
`Team`, `Season`, `Situation`, `GP`, `xGF%`, `CF%`, `xGF`, `xGA`, `GF`, `GA`, `HDCF`, `HDCA`

**Step 3 — Created HDCF% calculated field**
MoneyPuck does not include a pre-calculated `HDCF%` column. It was derived as:
`HDCF% = HDCF / (HDCF + HDCA)`

**Step 4 — Renamed columns**
Columns were renamed to match NST naming conventions for consistency.

**Step 5 — Unioned all 5 seasons**
All five files were unioned into a single table producing 160 rows (32 teams × 5 seasons).

**Step 6 — Output**
Saved as `teams_2021-25.csv` — 160 rows, 13 columns.

### Issues Encountered
- No missing values found across any season
- `xGF%` is stored as a decimal (e.g. 0.46) in MoneyPuck vs percentage form (e.g. 46.37) in NST — NST format used for all Tableau visualizations for consistency

---

## Output Files

| File | Rows | Source | Description |
|------|------|--------|-------------|
| `games_2021-25.csv` | 160 | Natural Stat Trick | Team stats by season, all situations |
| `teams_2021-25.csv` | 160 | MoneyPuck | Team stats by season, 5on5 only |

---

## Key Decisions

| Decision | Rationale |
|----------|-----------|
| Filter MoneyPuck to 5on5 only | Removes special teams noise, isolates structural roster quality |
| Use NST for Tableau visualizations | xGF% in percentage form is more readable in charts |
| Keep both sources | NST includes wins/points/standings; MoneyPuck provides deeper shot quality metrics |
