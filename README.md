# Melbourne Housing Market Analysis: Property Pricing, Features, and Regional Trends

## Overview
An exploratory data analysis (EDA) of the Melbourne Housing Snapshot dataset, examining what drives residential property prices in Melbourne, Australia, and how they vary by suburb, region, distance from the CBD, and property type.

**Tooling:** Python (Jupyter Notebook) — pandas, NumPy, matplotlib, seaborn

## Dataset
- **Source:** Melbourne Housing Snapshot (`melb_data.csv`), Kaggle
- **Shape:** 13,580 rows × 21 columns
- **Key columns:** Suburb, Address, Rooms, Type, Price, Method, SellerG, Date, Distance, Postcode, Bedroom2, Bathroom, Car, Landsize, BuildingArea, YearBuilt, CouncilArea, Regionname, Propertycount, Lattitude, Longtitude

## Project Status: Complete ✅

### Data Loading & Initial Overview
- Loaded dataset, reviewed structure, data types, and summary statistics

### Data Pre-processing
- Converted `Date` to datetime
- Handled missing values:
  - `Car`: median imputation
  - `CouncilArea`: filled with "Unknown"
  - `YearBuilt` and `BuildingArea` (high missingness): suburb-group median imputation, with "missing flag" indicator columns to preserve the information that these were originally missing
- Standardized the `Type` column — mapped single-letter codes (`h`, `u`, `t`) to readable labels (House, Unit/Duplex, Townhouse) and cast to a categorical dtype
- Checked and confirmed no duplicate rows
- Handled outliers in `Price`, `Landsize`, and `BuildingArea` using IQR-based capping (rather than removal, to preserve sample size)
- Fixed a data inconsistency: 6 rows had a negative `Property_Age` (sale date before build year) — treated as missing and median-imputed
- Engineered new features: `Price_per_sqm`, `Property_Age`, `Sale_Year`, `Sale_Month`

### Exploratory Data Analysis
10+ visualizations across univariate, bivariate, and multivariate analysis, including:
- Distribution of property prices
- Number of properties by type
- Price by number of rooms
- Price vs. distance from CBD
- Price distribution by property type
- Average price by region
- Price by rooms, split by property type (multivariate)
- Price vs. distance from CBD, colored by region (multivariate)
- Correlation heatmap of numeric features (multivariate)
- Outlier boxplots (Price, Landsize, BuildingArea)

### Key Insights
Five key findings, each backed by supporting statistics:
1. More rooms generally means a higher price, but the relationship isn't perfectly linear
2. Properties closer to the CBD tend to command higher prices, though the effect is modest (correlation: -0.171)
3. Property type has a major impact on price — houses average nearly double the price of units/duplexes
4. Location within Melbourne matters significantly — Southern Metropolitan is the most expensive region
5. Prices were relatively stable year-over-year across the dataset

**Conclusion:** Property type and location (region) emerge as the strongest drivers of price in the Melbourne housing market, outweighing distance from the CBD. Room count matters but shows diminishing and inconsistent returns at the high end. For buyers and investors, "where" and "what kind" of property matter more than simply "how big."

## Files
- `Melbourne_Property_Market_Analysis.ipynb` — full analysis notebook
- `melb_data.csv` — source dataset
- `README.md` — this file
