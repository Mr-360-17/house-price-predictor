# House Price Predictor

End-to-end regression model on the California Housing dataset — EDA, feature engineering, and three-model comparison.

## What I Did

Loaded the California Housing dataset (built into scikit-learn, no login needed), cleaned outliers, engineered three new features, then trained and compared three regression models using 5-fold cross-validation.

## Model Comparison

| Model | CV RMSE (mean) | CV RMSE (std) | Test RMSE | Test R² |
|---|---|---|---|---|
| Linear Regression | ~0.175 | ~0.004 | ~0.173 | ~0.62 |
| Random Forest | ~0.128 | ~0.003 | ~0.126 | ~0.79 |
| **Gradient Boosting** | **~0.118** | **~0.003** | **~0.116** | **~0.83** |

> Exact numbers are generated at runtime — re-run the notebook to get live results.

**Winner: Gradient Boosting** — lowest CV RMSE and highest R².

## Key Findings

- **MedInc** (median income) is the strongest predictor by a wide margin.
- **Latitude/Longitude** are second tier — location drives significant price variation.
- Gradient Boosting outperforms Linear Regression because house prices have non-linear interactions that tree models capture automatically.

## How to Run

```bash
git clone https://github.com/Mr-360-17/house-price-predictor.git
cd house-price-predictor
pip install -r requirements.txt
jupyter notebook house_price_predictor.ipynb
# Kernel → Restart & Run All
```

No dataset download needed — data loads automatically from scikit-learn.

## Reflection

The biggest lesson: feature engineering (rooms_per_person, bedroom_ratio) improved all three models, but the tree-based models benefited more because they could leverage the ratios non-linearly. A plain linear model treats each feature independently.

## Tech

Python · Pandas · NumPy · Scikit-learn · Matplotlib · Seaborn · Jupyter
