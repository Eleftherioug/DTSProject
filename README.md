# Final Project Draft: Breast Cancer Diagnosis Classification

This project is a draft machine learning analysis for classifying breast tumors as malignant or benign. The notebook includes data loading, exploratory data analysis, three engineered features, preprocessing, two classification models, a model comparison table, visualizations, and reflection on next steps.

## Dataset Source

- Dataset: Breast Cancer Wisconsin Diagnostic Dataset
- Source: UCI Machine Learning Repository via `scikit-learn`
- Local file in this repo: [data/breast_cancer_wisconsin.csv](/c:/Users/George/DTSProject/data/breast_cancer_wisconsin.csv)
- Observations: 569
- Predictors: 30 numeric feature columns
- Target: `target` where `0 = malignant` and `1 = benign`

Reference links:
- UCI dataset page: https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic
- scikit-learn dataset docs: https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html

## Repository Contents

- [final_project_draft.ipynb](/c:/Users/George/DTSProject/final_project_draft.ipynb): main notebook for the draft submission
- [data/breast_cancer_wisconsin.csv](/c:/Users/George/DTSProject/data/breast_cancer_wisconsin.csv): dataset used in the notebook
- `data/dataset.csv`: original file already present in the repo; it is not used by the notebook

## How to Run

1. Create and activate a Python environment.
2. Install the required packages:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install --upgrade pip
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

3. Open the notebook:

```powershell
jupyter notebook
```

4. Open `final_project_draft.ipynb` and run the cells from top to bottom.

## Current Results Summary

The current draft compares two classification models:

- Random Forest Classifier
- Logistic Regression

Preliminary test-set results from the draft workflow:

- Random Forest: accuracy `0.9474`, F1 `0.9583`, ROC AUC `0.9924`
- Logistic Regression: accuracy `0.9825`, F1 `0.9861`, ROC AUC `0.9947`

At the moment, Logistic Regression is the stronger draft model because it performs slightly better while also training faster. The notebook also includes a confusion matrix for each model and a learning curve for Random Forest to visualize training versus validation performance.

## Engineered Features in the Draft

- `area_perimeter_ratio`
- `radius_texture_interaction`
- `smoothness_symmetry_product`

These features were added to capture tumor shape compactness, interactions between size and texture, and combined surface-pattern behavior.

## Next Steps

- Add at least two more engineered features for the final submission
- Tune model hyperparameters with cross-validation
- Review whether recall or F1 should be emphasized most strongly for final evaluation
