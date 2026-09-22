# Melbourne Housing Market Analysis

Final project for Data Analytics coursework — a Python-based exploratory data analysis (EDA) of the Melbourne Housing Snapshot dataset.

## Objective
Analyze what drives property prices in Melbourne, Australia, and how they vary by suburb, region, distance from the CBD, and property type.

## Dataset
- Source: Kaggle — Melbourne Housing Snapshot (`melb_data.csv`)
- 13,580 rows, 21 columns of real residential property sales data

## Progress So Far

### Step 1: Data Loading and Initial Overview ✅
- Imported the dataset with Pandas
- Reviewed shape, data types, and summary statistics (`.info()`, `.describe()`)
- Identified missing values in `Car`, `CouncilArea`, `YearBuilt`, and `BuildingArea`

### Step 2: Data Pre-processing ✅
- Converted `Date` to datetime format
- Handled missing values:
  - `Car` and `CouncilArea` imputed (median / 'Unknown') due to minimal missingness
  - `YearBuilt` and `BuildingArea` imputed using suburb-level medians, with flag columns added for transparency
- Checked for and confirmed no duplicate rows
- Identified and capped extreme outliers in `Price`, `Landsize`, and `BuildingArea` using the IQR method
- Fixed a data inconsistency (negative `Property_Age`) caused by mismatched sale/build dates
- Engineered new columns: `Price_per_sqm`, `Property_Age`, `Sale_Year`, `Sale_Month`

## Tools
Python, Pandas, NumPy, Matplotlib, Seaborn — Jupyter Notebook
