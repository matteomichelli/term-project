# Data Directory

This folder contains all raw and processed datasets used in the BSAD 482 Term Project.

---

## Raw Data Files

### Natural Stat Trick (5 files)

| File | Season | Teams |
|------|--------|-------|
| `games_2021.csv` | 2020–21 | 32 |
| `games_2022.csv` | 2021–22 | 32 |
| `games_2023.csv` | 2022–23 | 32 |
| `games_2024.csv` | 2023–24 | 32 |
| `games_2025.csv` | 2024–25 | 32 |

**Source:** Natural Stat Trick — https://www.naturalstattrick.com/  
**Filter applied:** 5v5, Regular Season  
**Date Accessed:** February 2026  
**APA Citation:**  
Natural Stat Trick. (2026). *NHL team statistics 2021–2025, 5v5 regular season* [Data set]. https://www.naturalstattrick.com/

---

### MoneyPuck (5 files)

| File | Season | Teams |
|------|--------|-------|
| `teams_2021.csv` | 2020–21 | 32 |
| `teams_2022.csv` | 2021–22 | 32 |
| `teams_2023.csv` | 2022–23 | 32 |
| `teams_2024.csv` | 2023–24 | 32 |
| `teams_2025.csv` | 2024–25 | 32 |

**Source:** MoneyPuck — https://moneypuck.com/data.htm  
**Filter applied:** 5on5 situation only  
**Date Accessed:** February 2026  
**APA Citation:**  
MoneyPuck. (2026). *NHL team statistics 2021–2025* [Data set]. https://moneypuck.com/data.htm

---

## Processed Data Files

| File | Rows | Source | Produced By |
|------|------|--------|-------------|
| `games_2021-25.csv` | 160 | Natural Stat Trick | Tableau Prep |
| `teams_2021-25.csv` | 160 | MoneyPuck | Tableau Prep |

---

## Key Variables

| Variable | Description | Source |
|----------|-------------|--------|
| `xGF%` | Expected Goals For % — primary performance metric | NST / MoneyPuck |
| `HDCF` | High-Danger Chances For — offensive generation proxy | NST / MoneyPuck |
| `HDCA` | High-Danger Chances Against — defensive suppression proxy | NST / MoneyPuck |
| `HDCF%` | High-Danger Chance share | NST / MoneyPuck |
| `Points` | Regular season standings points | NST |
| `W`, `L` | Wins and losses | NST |
| `xGF`, `xGA` | Expected goals for and against (raw counts) | NST / MoneyPuck |
| `CF%` | Corsi For % — shot attempt possession metric | NST / MoneyPuck |
