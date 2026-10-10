# 🏡 Melbourne Housing Market Analysis: Property Pricing, Features, and Regional Trends

## 📌 Introduction
Housing prices are one of the clearest reflections of a city's economic and social fabric — shaped by location, property type, size, and demand patterns that shift across neighborhoods and over time. Understanding what drives these prices matters to buyers deciding where to invest, sellers pricing their properties, and analysts tracking regional market trends.

This project analyzes the **Melbourne Housing Snapshot** dataset, a real record of residential property sales in Melbourne, Australia. Through exploratory data analysis, we examine how price relates to property characteristics (rooms, type, building size), location (suburb, region, distance from the CBD), and time (sale year), with the goal of identifying the strongest drivers of property value in this market.

🛠️ **Tooling:** Python (Jupyter Notebook) — pandas, NumPy, matplotlib, seaborn

## 🎯 Objectives
- Clean and prepare the raw sales data for analysis (handle missing values, duplicates, outliers, and inconsistencies)
- Explore price distribution and relationships with property features through univariate, bivariate, and multivariate analysis
- Identify which factors — property type, room count, location, or distance from the CBD — most strongly influence price
- Summarize key, data-backed insights about what drives Melbourne housing prices

## 📊 About the Dataset
- **Source:** Melbourne Housing Snapshot (`melb_data.csv`), Kaggle
- **Shape:** 13,580 rows × 21 columns

| Column | Description |
|---|---|
| `Suburb` | Suburb where the property is located |
| `Address` | Street address of the property |
| `Rooms` | Number of rooms |
| `Type` | Property type — House, Unit/Duplex, or Townhouse |
| `Price` | Sale price in AUD |
| `Method` | Method of sale (e.g., sold, passed in, vendor bid) |
| `SellerG` | Real estate agent/agency |
| `Date` | Date of sale |
| `Distance` | Distance from Melbourne's CBD, in km |
| `Postcode` | Postal code |
| `Bedroom2` | Number of bedrooms (second data source, may differ slightly from `Rooms`) |
| `Bathroom` | Number of bathrooms |
| `Car` | Number of car spots |
| `Landsize` | Land size in square meters |
| `BuildingArea` | Building size in square meters |
| `YearBuilt` | Year the property was built |
| `CouncilArea` | Governing local council for the area |
| `Lattitude` / `Longtitude` | Geographic coordinates |
| `Regionname` | General region of Melbourne (e.g., Southern Metropolitan) |
| `Propertycount` | Number of properties in the suburb |


### 🧹 Data Pre-processing
- Converted `Date` to datetime
- Handled missing values: `Car` (median), `CouncilArea` ("Unknown"), `YearBuilt`/`BuildingArea` (suburb-group median imputation with "missing flag" columns)
- Standardized the `Type` column — mapped `h`/`u`/`t` codes to House/Unit-Duplex/Townhouse, cast to categorical dtype
- Confirmed no duplicate rows
- Capped outliers in `Price`, `Landsize`, `BuildingArea` using the IQR method (preserving sample size)
- Fixed a data inconsistency: 6 rows with negative `Property_Age` — treated as missing, median-imputed
- Engineered features: `Price_per_sqm`, `Property_Age`, `Sale_Year`, `Sale_Month`

### 📈 Exploratory Data Analysis
10+ visualizations across univariate, bivariate, and multivariate analysis:
- 📊 Distribution of property prices
- 🏘️ Number of properties by type
- 📦 Price by number of rooms
- 🗺️ Price vs. distance from CBD
- 📦 Price distribution by property type
- 📊 Average price by region
- 📦 Price by rooms, split by property type *(multivariate)*
- 🗺️ Price vs. distance from CBD, colored by region *(multivariate)*
- 🔥 Correlation heatmap of numeric features *(multivariate)*
- 📦 Outlier boxplots (Price, Landsize, BuildingArea)

### 💡 Key Insights
1. 🛏️ More rooms generally means a higher price, but the relationship isn't perfectly linear
2. 📍 Properties closer to the CBD tend to command higher prices, though the effect is modest (correlation: -0.171)
3. 🏠 Property type has a major impact on price — houses average nearly double the price of units/duplexes
4. 🌆 Location within Melbourne matters significantly — Southern Metropolitan is the most expensive region
5. 📅 Prices were relatively stable year-over-year across the dataset

**🎯 Conclusion:** Property type and location (region) emerge as the strongest drivers of price in the Melbourne housing market, outweighing distance from the CBD. For buyers and investors, **"where" and "what kind"** of property matter more than simply **"how big."**

## 💡 Recommendations
**For buyers:** Prioritize region and property type over room count when budgeting; consider Units/Duplexes or Townhouses in well-located regions as a lower-cost alternative to Houses; don't assume closer-to-CBD always means better value.

**For sellers:** Highlight property type and regional positioning in listings; price larger properties (7+ rooms) based on comparable sales rather than assuming a linear "more rooms = more value" relationship.

**For investors:** Compare region-level price-per-square-meter rather than raw price for a clearer read on relative value; the dataset's year-over-year price stability (2016–2017) suggests a mature, steady market rather than a fast-appreciating one.

### ⚠️ Limitations & Future Work
- Limited time window (2016–2017) — longer-term trends couldn't be assessed
- `BuildingArea` and `YearBuilt` had substantial missing data (~40–47%), requiring suburb-level imputation
- Future work could incorporate school zones, public transport proximity, or crime data

## 📁 Files
- `Melbourne_Property_Market_Analysis.ipynb` — full analysis notebook
- `melb_data.csv` — source dataset
- `README.md` — this file
