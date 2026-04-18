# 📊 Data Directory: NYC Motor Vehicle Collisions (2021-2026)

This directory contains the dataset used to analyze traffic accidents in New York City. The data is sourced from [NYC Open Data via Kaggle](https://www.kaggle.com/datasets/mlynhafizh/nyc-open-data-motor-vehicle-collisions-2021-2026/data).

## 📂 Folder Structure

- `raw/`: Contains the original, unaltered CSV files. This data is **read-only**.
- `processed/`: Contains cleaned datasets, engineered features, and aggregated tables ready for Python analysis or BI dashboarding.
- `temp/`: Temporary storage for intermediate files during long-running processing scripts.

## 📄 Dataset Overview (Raw)

The primary dataset tracks every collision in NYC where someone was injured/killed or where at least $1,000 in property damage occurred.

**Key Columns include:**
- `CRASH DATE` / `CRASH TIME`: Temporal data for trend analysis.
- `BOROUGH`: Location of the accident (Bronx, Brooklyn, Manhattan, Queens, Staten Island).
- `LATITUDE` / `LONGITUDE`: Geospatial coordinates for mapping.
- `NUMBER OF PERSONS INJURED/KILLED`: Primary metrics for severity.
- `CONTRIBUTING FACTOR`: Reason for the crash (e.g., Distraction, Alcohol, Speeding).
- `VEHICLE TYPE CODE`: Types of vehicles involved (e.g., Sedan, SUV, Bicycle).

## 🛠 Transformation Logic (`raw/` ➡️ `processed/`)

The following cleaning steps are applied via the `notebooks/02_data_cleaning.ipynb` script:

1.  **Date/Time Parsing**: Merging `CRASH DATE` and `CRASH TIME` into a single ISO-8601 `timestamp` column.
2.  **Missing Value Imputation**: 
    * Missing `BOROUGH` information is filled using `LATITUDE` and `LONGITUDE` via reverse geocoding where possible.
    * Nulls in contributing factors are labeled as "Unspecified".
3.  **Data Filtering**: 
    * Restricting records to the date range **January 2021 – December 2026**.
    * Removing records with invalid coordinates (e.g., 0.0, 0.0).
4.  **Feature Engineering**:
    * `IS_FATAL`: Boolean flag indicating if any deaths occurred.
    * `CRASH_HOUR`: Extracted hour of the day for peak-time analysis.
    * `VEHICLE_CATEGORY`: Simplified vehicle types (e.g., grouping "Taxi" and "Livery" into "Commercial").

## ⚖️ Data Usage & Licensing

- **Source**: NYC Open Data.
- **Update Frequency**: Manual download for this project version.
- **Privacy Note**: This dataset is public and does not contain Personally Identifiable Information (PII) of drivers or victims.

## ⚠️ Notes
- The processed files are exported in `.parquet` format for the modeling phase to save space and improve loading speeds in Python, while `.csv` is maintained for Power BI/SQL compatibility.