Deliverable 1: Data Collection, Cleaning, and Exploration

Dataset Summary

Source: [Kaggle - Online Retail Dataset](https://www.kaggle.com/datasets/vijayuv/onlineretail)
Size: 541,909 rows × 8 columns (before cleaning)
Attributes:
  - `InvoiceNo`: Unique identifier for each transaction
  - `StockCode`: Product/item code
  - `Description`: Product name/description
  - `Quantity`: Number of units purchased (can be negative for returns)
  - `InvoiceDate`: Timestamp of the transaction
  - `UnitPrice`: Price per unit
  - `CustomerID`: Unique identifier for the customer
  - `Country`: Customer’s location

Objective: Prepare the dataset for modeling tasks such as customer segmentation, sales forecasting, and product recommendation through preprocessing and exploration.


Data Cleaning & Preparation Steps

1. Removed Missing Values: 
   - Dropped rows with missing `CustomerID`, as customer-level analysis requires this field.
   - Reduced the dataset size by ~25%.

2. Removed Duplicate Records:
   - Used `.drop_duplicates()` to eliminate repeated entries.

3. Filtered Out Cancelled Transactions:
   - Identified by `InvoiceNo` starting with "C" (credit notes).
   - These were excluded to retain only successful purchases.

4. Removed Invalid Quantities and Prices:
   - Excluded rows where `Quantity` or `UnitPrice` ≤ 0.
   - Ensured only valid sales are analyzed.

5. Feature Engineering:
   - Created a new `Sales` column = `Quantity * UnitPrice` to analyze revenue trends.

6. Data Type Fixes:
   - Converted `InvoiceDate` to datetime for time-based grouping.
   - Converted `Country` and `CustomerID` to categorical types.


Exploratory Data Analysis (EDA) Highlights

Top Countries: The UK dominates the transaction data, followed by the Netherlands and Germany.
Outliers: Detected in both `Quantity` and `UnitPrice`. Distributions are highly skewed.
Sales Trend: Monthly revenue shows seasonality, with spikes in November and December (holiday effect).
Correlations: Minimal linear correlation between `Quantity`, `UnitPrice`, and `Sales`, but useful patterns found visually.

Key Visualizations:
- Bar chart: Top 10 countries by transaction volume
- Histogram: Quantity and price distributions
- Correlation heatmap: `Quantity`, `UnitPrice`, and `Sales`
- Time series plot: Monthly revenue trend


Challenges Encountered & Solutions

| Challenge | Solution |
|----------|----------|
| High volume of missing `CustomerID` | Dropped missing values; noted impact on customer-level analysis |
| Returns and canceled orders | Removed using `InvoiceNo` filters (those starting with "C") |
| Skewed data distributions | Used log scaling in visualizations to analyze outliers |
| Data format issues | Used encoding `ISO-8859-1` and corrected datetime columns |


Summary

This deliverable successfully prepared the Online Retail dataset for advanced analysis by:
- Cleaning the raw transactional data
- Removing noise and inconsistencies
- Gaining business insights through visualization

The cleaned dataset is now ready for regression, classification, clustering, and association rule mining in future deliverables.

