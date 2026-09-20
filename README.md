# Player Retention Analysis

Exploratory analysis of mobile game player behaviour, built around D1, D7, and D14 retention. Uses raw event-level and user-level data to construct player-level features, test whether early engagement predicts retention, and segment players by activity.

## Data

- `events.xlsx` — raw event-level log data (per-player, per-session activity)
- `users.xlsx` — player-level attributes (install date, cohort info)
- `player_retention.ipynb` — the full analysis notebook

## What the notebook covers

**1. Feature engineering**
- Builds a `player_stats` table aggregating raw events into per-player metrics: `total_sessions`, `active_days`, `sessions_per_active_day`
- Computes D1, D7, and D14 retention flags for each player
- Derives early-engagement features — active days in the first few days post-install (D0–D3 and D0–D6 windows) — to test as leading indicators of longer-term retention

**2. Descriptive statistics**
- Mean, median, standard deviation, min/max, and quantile summaries for engagement metrics
- IQR-based outlier detection on session counts and active days
- Skewness checks and a log transform (`active_days_log`) to correct for right-skewed engagement data

**3. Hypothesis testing**
- Compares early-engagement distributions between retained and non-retained players (D7 and D14 cohorts) using box plots
- Mann-Whitney U tests to check whether the difference in early activity between retained and churned players is statistically significant
- Effect size and hypothesis decision at α = 0.05

**4. Correlation analysis**
- Correlation matrix across engagement features
- Checks the relationship between early active days and later retention

**5. Segmentation**
- K-means clustering on scaled behavioural features to group players into activity segments
- Maps clusters to interpretable labels (e.g. low/medium/high engagement) and compares D14 retention rates across segments

## Tools

Python · pandas · numpy · matplotlib · scipy (`mannwhitneyu`) · scikit-learn (`KMeans`)

## Status

Work in progress — part of ongoing prep for analyst/data roles in game analytics.
