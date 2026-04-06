# Final Project Draft — DTSProject

Project draft for the Unit 9 final project. This repository contains a Jupyter notebook (`final_project_draft.ipynb`) that loads and explores a dataset, engineers features, trains two ML models (Random Forest and Logistic Regression), and compares their performance.

Dataset
- Place your dataset as `data/dataset.csv`. If this file is missing or empty the notebook will generate a synthetic demo dataset so you can run the pipeline end-to-end.

How to run
1. Create a Python environment (recommended) and install dependencies:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1   # PowerShell
pip install --upgrade pip
pip install pandas numpy scikit-learn matplotlib seaborn
```

2. Open the repository in VS Code and launch Jupyter, or run the notebook:

```powershell
code .
# In VS Code: open final_project_draft.ipynb and run cells
# Or run jupyter notebook / jupyter lab and open the notebook
```

Current results summary
- Notebook implements: data loading + EDA, 3 engineered features (interaction, ratio, binned), preprocessing, `RandomForestClassifier` and `LogisticRegression` implementations, performance comparison table, and a learning curve for Random Forest.
- Replace `data/dataset.csv` with your chosen dataset to evaluate real results for your project.

Next steps
- Add more engineered features (target: 5+ for final submission), perform hyperparameter tuning, and consider advanced models (XGBoost/LightGBM) depending on results.

Contact / Notes
- This draft is intended to be iterated on before the final submission. See `final_project_draft.ipynb` for details and inline discussion.