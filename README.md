# FIFA World Cup 2026 Player Analytics

A data-driven football analytics project that transforms raw FIFA World Cup 2026 player performance data into actionable insights through advanced statistics, composite scoring, and visual storytelling.

## Overview

This repository analyzes tournament-wide player performance using match-level data and converts it into scouting-style outputs. Instead of relying only on raw totals, the project builds per-90 metrics, compares actual production to expected output, identifies players who improved under knockout pressure, and creates a composite-score Best XI.

The workflow is designed to be simple to run, easy to modify, and strong enough for a portfolio project in sports analytics, data analysis, or performance modeling.

## Features

- Player-level tournament aggregation from match-by-match data
- Per-90 performance metrics for fairer comparisons
- Finishing efficiency analysis using goals vs expected goals (xG)
- Clutch-performance modeling using group-stage vs knockout-stage rating changes
- Position-specific composite scoring for goalkeepers, defenders, midfielders, and forwards
- Data-driven Best XI selection with nationality diversity constraints
- Nationality strength ranking based on squad-wide composite quality
- Plotly visualizations for clearer storytelling and presentation
- CSV exports for downstream analysis or dashboard use

## Dataset

- <a href = "https://github.com/Sharnow/Hypothetical-Data-Analysis/blob/main/data/fifa_world_cup_2026_player_performance.csv"> Dataset </a>

## Project Structure

```bash

├── data/
│   └── fifa_world_cup_2026_player_performance.csv
├── notebooks/
│   ├── 01_cleaning.ipynb
│   ├── 02_eda.ipynb
├── outputs/
│   └── (charts, cleaned CSV, model files)
├── README.md
```

## Core Analysis

### 1. Player Aggregation
The raw dataset contains match-level player records. The notebook aggregates those rows into one tournament summary per player, including minutes, goals, assists, xG, xA, tackles, recoveries, ratings, and other advanced metrics.

### 2. Per-90 Metrics
Per-90 calculations make comparisons fairer across players with different minute totals. This is especially useful when comparing rotation players to full-time starters.

### 3. Finishing Efficiency
The project measures finishing efficiency using:

```python
finishing_delta = goals - xg
```

A positive value suggests a player scored more than expected from their chances, while a negative value suggests underperformance relative to shot quality.

### 4. Clutch Factor
To capture pressure performance, the project compares each player's average rating in the group stage against their average rating in knockout rounds. This helps identify players who stepped up when the stakes increased.

### 5. Composite Best XI
Each position uses a custom weighted scoring model:

| Position | Main Inputs |
|---|---|
| Goalkeeper | Saves, rating, clean sheets |
| Defender | Tackles, interceptions, recoveries, attacking output |
| Midfielder | Creativity, rating, passing, attacking output |
| Forward | Goals+assists per 90, rating, clutch score, finishing delta |

These scores are used to generate a 4-3-3 Best XI with a cap on players from the same nationality to improve variety.

### 6. Nationality Strength Ranking
The project also ranks countries by average composite score across qualifying players, giving a broader picture of squad depth beyond just star performers.

## Visualizations

The notebook generates three main charts:

- **Goals vs xG bar chart** — highlights the biggest overperformers and underperformers in finishing
- **Clutch performer chart** — shows players with the largest knockout-stage rating jump
- **Actual vs expected G+A scatter plot** — compares attacking production to expected attacking output per 90 minutes

## Technologies Used

- Python
- Pandas
- NumPy
- Plotly
- Jupyter Notebook

## How to Run

1. Clone the repository.
2. Place `fifa_world_cup_2026_player_performance.csv` in the project root.
3. Open `02_eda.ipynb` in Jupyter Notebook or JupyterLab.
4. Run the notebook from top to bottom.


## Output Files

Running the notebook/script generates:

- `player_aggregates.csv` — player-level tournament summary table
- `best_xi.csv` — selected Best XI using composite scoring
- `nationality_strength.csv` — nationality depth ranking
- `xg_over_underperformers.csv` — finishing efficiency leaders and laggards
- `clutch_performers.csv` — top knockout risers
- PNG chart files for reporting or portfolio use

## Why This Project Matters

This project is useful as:

- a sports analytics portfolio project,
- a demonstration of feature engineering and metric design,
- an example of turning raw event-style data into decision-ready outputs,
- and a clean case study in combining analysis with presentation.

It can also be extended into a Streamlit dashboard, scouting tool, or interactive web app.

## Future Improvements

- Add team-level tactical summaries
- Build player similarity search
- Add interactive filtering by nationality, stage, and position
- Deploy as a dashboard
- Incorporate radar charts or role-based archetype clustering

## License

This project is open for educational and portfolio use. Update the license section as needed for your preferred repository license.
