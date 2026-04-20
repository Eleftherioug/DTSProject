# Tottenham Hotspur Recruitment Fit Model

This project is a machine learning scouting prototype designed to identify football players who fit Tottenham Hotspur's tactical profile, recruitment style, and cost-conscious decision-making process. The final solution combines player archetype discovery with K-Means clustering, fit-score prediction with an optimized Random Forest regressor, ethical analysis of model risks, and business recommendations for responsible deployment.

While the original proposal aimed to combine FBref and Transfermarkt across multiple leagues, this final class submission uses a reproducible four-season Premier League dataset from the public Fantasy Premier League repository. That narrower scope allows the entire workflow to run cleanly while still demonstrating feature engineering, model optimization, evaluation, and responsible decision-making.

## Dataset Source and Description

Primary source:
- Vaastav Anand, `Fantasy-Premier-League` GitHub repository
- Repository: https://github.com/vaastav/Fantasy-Premier-League
- Data dictionary: https://github.com/vaastav/Fantasy-Premier-League/blob/master/DATA_DICTIONARY.md

Local data files:
- [data/fpl_raw/2021-22/players_raw.csv](/c:/Users/George/DTSProject/data/fpl_raw/2021-22/players_raw.csv)
- [data/fpl_raw/2022-23/players_raw.csv](/c:/Users/George/DTSProject/data/fpl_raw/2022-23/players_raw.csv)
- [data/fpl_raw/2023-24/players_raw.csv](/c:/Users/George/DTSProject/data/fpl_raw/2023-24/players_raw.csv)
- [data/fpl_raw/2024-25/players_raw.csv](/c:/Users/George/DTSProject/data/fpl_raw/2024-25/players_raw.csv)
- Matching `teams.csv` files for each season are included in `data/fpl_raw/`

Final modeling scope:
- 4 Premier League seasons: `2021-22` through `2024-25`
- 1,625 outfield player-season observations after filtering for meaningful minutes
- 6 engineered features
- Continuous `tottenham_fit_score` target built from style similarity, affordability proxy, availability, and impact

## Project Files

- [final_project_draft.ipynb](/c:/Users/George/DTSProject/final_project_draft.ipynb): final notebook submission
- `data/fpl_raw/`: raw multi-season player and team data

## Setup Instructions

1. Create and activate a Python virtual environment.

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install dependencies.

```powershell
pip install --upgrade pip
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

3. Launch Jupyter.

```powershell
jupyter notebook
```

4. Open `final_project_draft.ipynb` and run all cells from top to bottom.

## Engineered Features

The final notebook includes these engineered features:
- `goal_involvement_per90`
- `creativity_threat_balance`
- `bps_per90`
- `availability_value_index`
- `ict_per_90`
- `team_strength_contribution`

These features capture attacking efficiency, stylistic balance, broader contribution, affordability or availability, impact rate, and team-context-adjusted performance.

## Final Results Summary

The final submission compares two optimized models:
- Optimized K-Means clustering baseline for player archetypes
- Optimized Random Forest regressor for direct Tottenham fit-score prediction

Final test-set results:
- Optimized K-Means baseline: `RMSE = 12.6355`, `MAE = 9.8723`, `R2 = 0.5895`, `MAPE ≈ 23.33%`
- Optimized Random Forest: `RMSE = 4.5541`, `MAE = 3.3331`, `R2 = 0.9467`, `MAPE ≈ 7.26%`

Model takeaway:
- Random Forest is the stronger predictive model by a large margin.
- K-Means remains useful because it provides interpretable player archetypes that support tactical profiling and stakeholder communication.

## Key Insights

- Feature importance shows that influence, overall contribution (`bps` and `bps_per90`), and efficiency-style features matter more than raw goal totals alone.
- The model supports a system-based scouting approach by rewarding players who combine tactical fit, contribution quality, and manageable cost signals.
- Example predictions show that K-Means is useful at a broad archetype level, but Random Forest is much better at distinguishing between players who look similar stylistically yet have meaningfully different fit scores.

## Recommendation

The recommended deployment choice is the optimized Random Forest model, with K-Means retained as a supporting profiling tool. In practice, Tottenham should use the model as a shortlist generator for analyst and scout review rather than as a fully automated decision-maker.

## Ethical and Deployment Notes

- The dataset is limited to Premier League players, so the model may underrepresent talent from smaller leagues.
- The affordability signal uses `now_cost` as a proxy rather than real transfer-market value.
- The system should be used with human review, position-specific monitoring, and periodic retraining rather than deployed as a fully automated recruitment filter.
