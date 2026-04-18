# 📓 Notebooks Directory

This folder contains Jupyter Notebooks used for data exploration, cleaning, prototyping, and visualization. These notebooks serve as the "lab journal" for the project.

## 🔢 Execution Order

To ensure reproducibility, please run the notebooks in the following numerical order:

1.  **`01_data_exploration.ipynb`**: Initial Exploratory Data Analysis (EDA) to understand distributions, correlations, and data quality issues.
2.  **`02_data_cleaning.ipynb`**: Handling missing values, outliers, and formatting data for analysis.
3.  **`03_eda.ipynb`**
4.  **`04_feature_engineering.ipynb`**: Creating new variables and preparing the final dataset for modeling.
5.  **`05_modeling_prototyping.ipynb`**: Testing different algorithms and fine-tuning parameters.
6.  **`06_final_analysis_viz.ipynb`**: Generating the final charts and insights for the stakeholder report.

## 📂 Sub-directories

- `experimental/`: Scratchpad notebooks for quick tests or ideas that didn't make it into the final pipeline.
- `archive/`: Deprecated notebooks from previous versions of the project.

## 🛠 Best Practices

- **Kernel**: Use the project-specific virtual environment (`venv`) as your Jupyter kernel.
- **Clean Slate**: Before committing a notebook, "Restart & Run All" to ensure the logic is linear and works from start to finish.
- **Clear Outputs**: Large outputs (like huge tables or interactive maps) can bloat the file size. Consider clearing outputs or using `Plotly` static renders if file size becomes an issue.
- **Modularize**: If you find yourself copying a function between notebooks, move that code into `src/processing.py` and import it instead.

## 📊 Key Findings Summary

*Briefly list any major "Aha!" moments discovered during the EDA process here.*

* *Finding 1: Sales peak significantly on Tuesday mornings.*
* *Finding 2: 15% of the 'Age' column contained null values, addressed via median imputation.*