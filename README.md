# Breaking the Bubble: Optimizing Salary Cap Allocation for Stanley Cup Contention
## BSAD482 Term Project
**Term:** Winter 2026 | **Path:** Advanced

---

## Decision Framing
> **The Decision:** Determining the optimal allocation of the team's projected $13M Salary Cap space for the 2026-2027 season: Should the team prioritize acquiring **High-Danger Chance Generation (Elite Offence)** or **High-Danger Chance Suppression (Elite Defence)** to maximize the statistical probability of a Stanley Cup victory? This analysis culminates in an interactive simulation dashboard that allows the decision-maker to model different cap allocation splits and observe their projected impact on win probability in real time.

---

## Executive Summary
In the modern NHL, the salary cap is the ultimate equalizer; championship teams are formed not by just acquiring skill, but by optimizing "wins per dollar" more effectively than their competition. The Detroit Red Wings are currently at a critical strategic turning point: following a seven-year rebuild, the franchise remains stuck in the statistical "bubble", too competitive to secure top lottery draft picks, but lacking the elite roster efficiency required to contend for the Stanley Cup. With the 2025-26 NHL salary cap set at $95.5 million and Detroit carrying a projected cap hit of $82.7 million, the franchise has approximately $12.8 million in projected cap space remaining (PuckPedia, 2026). General Manager Steve Yzerman faces a high-stakes resource allocation challenge that will determine the franchise's trajectory for the next decade.

This project addresses the core tension of roster construction: the trade-off between purchasing scarce, high-premium offensive production versus investing in cost-effective defensive suppression. While traditional hockey wisdom often favours defensive depth, modern analytics suggest that elite high-danger chance generation may offer a higher Return on Investment (ROI) in terms of pure win probability. However, due to the salary cap, investing heavily in one area mathematically necessitates weakness in the other.

Using a Decision Intelligence framework, this analysis utilizes historical player data and predictive modelling to assess the impact of these opposing strategies on playoff success. Demonstrating the feedback loops among roster investment, on-ice performance, and cap flexibility provides the General Manager with data-backed advice on how to utilize the team's remaining financial assets to maximize the likelihood of winning the Stanley Cup in 2027.

[Read more](Background.md)
---
## Causal Loop Diagram
The model visualizes the systemic tension between the pressure to win and financial reality:

**R1: The Success Cycle (Reinforcing Loop):** This loop illustrates the cost of success. As Win Probability increases, it drives up Playoff Revenue and Fan/Owner Pressure. This pressure compels management to double down on Allocation to Elite Offense to maintain dominance, creating a snowball effect of rising expectations and spending.

**B1: The Salary Cap Squeeze (Balancing Loop):** This loop acts as the system's hard constraint. Increasing the Allocation to Elite Offense directly reduces the Cap Space for Defense/Depth. This depletion harms Defensive Stability, which drags down Win Probability. This balancing mechanism limits the effectiveness of purely offensive investment, as the team eventually becomes too "top-heavy" and vulnerable defensively.

**B2: The Franchise Revenue Loop (Balancing Loop):** This loop captures the broader financial feedback. As Win Probability increases, Franchise Revenue grows through ticket sales, merchandise, and media value. This revenue supports investment in Roster Depth, which in turn supports Win Probability, but remains constrained by the hard salary cap ceiling.

![Causal Loop Diagram](img/refined_CLD.png)

### CLD Evidence Links

The following causal links are supported by data and research:

**Link 1: High Danger Chance Generation (HDCF) → Win Probability**
The positive link between HDCF% and Win Probability is supported by Viz 3, which shows a strong positive relationship between high-danger chance generation share and regular season points across all 32 NHL teams over five seasons. Teams generating more high-danger chances consistently accumulate more points.

**Link 2: Cap Allocation to Elite Offence → High Danger Chance Generation (HDCF)**
Macdonald (2012) demonstrated that shot-based metrics, particularly high-danger chances, are stronger predictors of future goals than raw goal totals, with OLS and Ridge regression models achieving correlations of r = 0.67-0.69 between predicted and actual goals. This supports the link between investing cap space in elite offensive players and increased high-danger chance generation, as skilled forwards are the primary drivers of slot-area shot attempts. The study restricted analysis to 5-on-5 situations, the same filter applied to both datasets in this project.

**Link 3: xGF% → Win Probability**
The positive link between expected goals percentage and Win Probability is supported by Viz 1, which shows a strong upward league-wide trend between xGF% and regular season points across 160 team-seasons (2021–2025). This confirms that xGF% is a reliable predictor of standings success, consistent with the foundational methodology established by Macdonald (2012).

---

## Milestone 2: Data Exploration & System Mapping

### Data Sources
Two data sources were used for this analysis, covering all 32 NHL teams across five regular seasons (2020-21 through 2024-25) at 5-on-5 strength:

- **Natural Stat Trick**: Team-level stats including wins, points, xGF%, HDCF%, and Corsi. Downloaded as annual CSVs and combined into `games_2021-25.csv`. (Natural Stat Trick, 2026)
- **MoneyPuck**: Team-level advanced metrics filtered to 5on5 situations only, combined into `teams_2021-25.csv`. (MoneyPuck, 2026)

All wrangling was performed in Tableau Prep. See [Wrangling.md](Wrangling.md) for full documentation.

---

### Visualizations

#### Viz 1: Expected Goals % vs. Points
![xGF% vs Points](img/viz1_xgf_points_scatter.png)

This scatter plot shows the relationship between xGF% and regular season points for all 32 NHL teams across five seasons. The strong upward trend line confirms that expected goals percentage is a reliable predictor of standings success. Detroit's data points (red circles) consistently appear in the bottom-left cluster, below 50% xGF and below league average in points, visually confirming the gap Yzerman must close. This supports the decision framing: improving xGF% through targeted cap investment should translate directly into more points and playoff qualification.

---

#### Viz 2: Detroit vs. League Average xGF%
![Detroit vs League xGF%](img/viz2_det_vs_league_xgf.png)

This line chart tracks Detroit's average xGF% at 5v5 against the league average from 2021 to 2025. The league average holds steady near 50% while Detroit bottomed out at 45.75% in 2023 before climbing sharply to 49.98% in 2025, nearly reaching the break-even line. This trend validates the Yzerplan's trajectory but also highlights the urgency: Detroit is approaching but has not yet crossed the 50% threshold that separates contenders from bubble teams.

---

#### Viz 3: High-Danger Chance Generation vs. Points
![HDCF% vs Points](img/viz3_hdcf_points_scatter.png)

This scatter plot examines the relationship between HDCF% and regular season points. The positive trend confirms that teams generating more high-danger chances tend to accumulate more points. Detroit's data points cluster in the lower-left, indicating below-average offensive high-danger generation across all five seasons. This directly informs the cap allocation decision: investing in forwards who generate high-danger chances has a measurable impact on standings outcomes league-wide.

---

#### Viz 4: Detroit Points vs. League Average
![Detroit Points Bar](img/viz4_det_points_bar.png)

This bar chart compares Detroit's regular season points to the league average for each season from 2021 to 2025. Detroit fell below the league average in every season except 2023, where it nearly matched it with 91 points before regressing to 86 in 2024 and 72 in 2025 (partial season at time of download). This chart reinforces the "bubble team" framing from the decision brief — Detroit is consistently close to average but has never broken through into true contention.

---

### References

PuckPedia. (2026, March 2). *Detroit Red Wings salary cap and contracts*. https://puckpedia.com/team/detroit-red-wings

Macdonald, B. (2012). *An expected goals model for evaluating NHL teams and players*. Proceedings of the MIT Sloan Sports Analytics Conference, March 2-3, 2012, Boston, MA, USA. https://www.hockeyanalytics.com/Research_files/NHL-Expected-Goals-Brian-Macdonald.pdf

MoneyPuck. (2026). *NHL team statistics 2021–2025* [Data set]. https://moneypuck.com/data.htm

Natural Stat Trick. (2026). *NHL team statistics 2021–2025, 5v5 regular season* [Data set]. https://www.naturalstattrick.com/

Pro Hockey Rumors. (2025, October 22). *Salary cap deep dive: Detroit Red Wings*. https://www.prohockeyrumors.com/2025/10/salary-cap-deep-dive-detroit-red-wings-9.html

Octopus Thrower. (2025, June 16). *How the looming salary cap boost can reshape the Red Wings plans*. https://octopusthrower.com/how-the-looming-salary-cap-boost-can-reshape-the-red-wings-plans
