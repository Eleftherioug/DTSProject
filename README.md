# Tottenham Hotspur Recruitment Fit Model

This project is a draft machine learning prototype for identifying football players who fit Tottenham Hotspur's tactical and recruitment profile. The long-term proposal uses FBref and Transfermarkt data across multiple leagues, but this draft narrows the scope to a reproducible multi-season Premier League dataset so the full workflow can be validated before the final submission.

The notebook builds a continuous `tottenham_fit_score`, profiles player archetypes with K-Means clustering, predicts fit with Random Forest regression, and ranks external players who look like strong Tottenham-style targets.

## Dataset Source and Description

Draft dataset source:
- Vaastav Anand, `Fantasy-Premier-League` GitHub repository
- Repository: https://github.com/vaastav/Fantasy-Premier-League
- Data dictionary: https://github.com/vaastav/Fantasy-Premier-League/blob/master/DATA_DICTIONARY.md

Local data files used in this repo:
- [data/fpl_raw/2021-22/players_raw.csv](/c:/Users/George/DTSProject/data/fpl_raw/2021-22/players_raw.csv)
- [data/fpl_raw/2022-23/players_raw.csv](/c:/Users/George/DTSProject/data/fpl_raw/2022-23/players_raw.csv)
- [data/fpl_raw/2023-24/players_raw.csv](/c:/Users/George/DTSProject/data/fpl_raw/2023-24/players_raw.csv)
- [data/fpl_raw/2024-25/players_raw.csv](/c:/Users/George/DTSProject/data/fpl_raw/2024-25/players_raw.csv)
- Matching `teams.csv` files for each season are also included in `data/fpl_raw/`

Draft dataset scope:
- 4 Premier League seasons: `2021-22` through `2024-25`
- 1,625 outfield player-season observations after filtering for meaningful minutes
- 20+ raw and engineered modeling features
- Real-world player, team, performance, and price-proxy information

Important draft note:
- This version uses `now_cost` from FPL as an affordability proxy.
- The final project is intended to expand back toward the original proposal by integrating FBref performance data and Transfermarkt market values across more leagues.

## Project Files

- [final_project_draft.ipynb](/c:/Users/George/DTSProject/final_project_draft.ipynb): main notebook with EDA, feature engineering, K-Means, Random Forest, comparison, and reflection
- `data/fpl_raw/`: raw multi-season Premier League player and team data

## How to Run

1. Create and activate a Python virtual environment.

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install the dependencies.

```powershell
pip install --upgrade pip
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

3. Launch Jupyter and open the notebook.

```powershell
jupyter notebook
```

4. Open `final_project_draft.ipynb` and run the cells from top to bottom.

## Current Results Summary

The draft compares two proposal-aligned techniques:
- K-Means clustering for player archetypes and cluster-based fit-score baseline predictions
- Random Forest regression for direct Tottenham fit-score prediction

Preliminary test-set results:
- K-Means baseline: `RMSE = 14.7960`, `MAE = 11.9429`, `R2 = 0.5224`
- Random Forest Regressor: `RMSE = 4.9568`, `MAE = 3.5753`, `R2 = 0.9464`

Current takeaway:
- Random Forest is the stronger predictive model for the draft.
- K-Means is still valuable because it provides interpretable player archetypes and supports the tactical identity part of the proposal.

## Engineered Features in the Draft

- `goal_involvement_per90`
- `creativity_threat_balance`
- `bps_per90`
- `availability_value_index`

These features were designed to capture efficiency, player style balance, contribution quality, and affordability or availability trade-offs relevant to Spurs-style recruitment.

## Next Steps for the Final Version

- Add real market values from Transfermarkt instead of relying on the FPL cost proxy
- Add FBref-style tactical features such as progression, defensive actions, and passing quality
- Expand beyond the Premier League to better match the original multi-league recruitment proposal
- Tune the Random Forest model and test more advanced supervised models
