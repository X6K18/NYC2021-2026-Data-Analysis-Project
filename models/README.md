# 📂 Models Directory

This directory contains all machine learning models, trained weights (serialized objects), and scripts related to model training, validation, and inference.

## 📌 Directory Structure

- `production/`: Contains the latest stable versions of models used for deployment or BI integration.
- `development/`: Experimental models, early-stage drafts, and research prototypes.
- `archived/`: Older versions of models kept for reproducibility and benchmarking.
- `encoders/`: Saved scalers (StandardScaler, MinMaxScaler) and label encoders used during preprocessing.

## 🛠 Model Inventory

| File Name | Algorithm | Objective | Key Metric (Accuracy/R2) | Status |
| :--- | :--- | :--- | :--- | :--- |
| `churn_v1.pkl` | Random Forest | Predict customer churn | 85% F1-Score | Production |
| `demand_fc_v2.joblib` | XGBoost | Forecasting weekly sales | 0.92 R² | Testing |

## 🚀 Training Pipeline

The models in this project are developed following these standardized steps:
1. **Feature Engineering**: Input data is sourced from `data/processed/`.
2. **Model Selection**: Comparative analysis of various algorithms (e.g., Logistic Regression, LightGBM).
3. **Hyperparameter Tuning**: Optimization performed using `GridSearchCV` or `Optuna`.
4. **Validation**: Evaluation using K-fold Cross-Validation and hold-out test sets.

## 📝 Usage

To load and use a trained model for inference in your Python scripts:

```python
import joblib

# Load the production model
model = joblib.load('models/production/churn_v1.pkl')

# Generate predictions
predictions = model.predict(X_new)