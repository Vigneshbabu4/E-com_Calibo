# E-Commerce Customer Data Analysis

## Project Overview

This project explores and cleans an e-commerce customer dataset using Python. It focuses on data quality checks, exploratory data analysis (EDA), sales and profit summaries, customer and order patterns, and visualizations that can support business decisions.

> **Note:** The notebook performs data cleaning and exploratory analysis. It does not train or evaluate a machine-learning model.

## Dataset

The notebook loads a CSV file named `ecommerce_customer.csv`.

The analysis uses fields including (where present in the dataset):

- Customer information: `Customer_Age`, `City`, `Customer_Segment`, `Customer_Rating`, `Customer_Loyalty_Points`
- Order and product information: `Order_ID`, `Customer_ID`, `Product_Name`, `Category`, `Quantity`, `Device`
- Sales and financial information: `Unit_Price`, `Gross_Amount`, `Discount_Pct`, `Discount_Amount`, `Net_Sales`, `Estimated_Cost`, `Profit`, `Profit_Margin_Pct`
- Fulfilment and behaviour: `Shipping_Days`, `Website_Session_Minutes`, `Customer_Satisfaction`, `Return_Status`
- Channel and acquisition information: `Sales_Channel`, `Payment_Method`, `Marketing_Source`

The exact columns available depend on the supplied CSV file.

## Tools and Libraries

- **Python** — analysis and data processing
- **Pandas** — loading, cleaning, grouping, and summarizing data
- **NumPy** — numerical operations
- **Matplotlib** — charts and plots
- **Seaborn** — correlation heatmap

## Workflow

### 1. Load and inspect the data

- Load `ecommerce_customer.csv` into a Pandas DataFrame.
- Inspect the first and last rows, dataset dimensions, column names, data types, and descriptive statistics.
- Check missing values and duplicate records.

### 2. Clean the data

- Remove duplicate rows.
- Standardize text formatting in fields such as `City`, `Category`, and `Payment_Method`.
- Inspect missing values in categorical and numeric columns.
- Fill selected numeric missing values using median values.
- Check for invalid numeric values, including negative ages, quantities, shipping days, and financial amounts, as well as discount percentages outside the 0–100 range and customer ratings above 5.
- Replace selected invalid values with median values.
- Check duplicate order/customer combinations and remove duplicates based on `Order_ID` and `Customer_ID`.

**Data-cleaning note:** Review the notebook's imputation and duplicate-removal steps before using the cleaned data for reporting. In particular, ensure categorical missing values are filled with actual mode values and confirm that `Order_ID` plus `Customer_ID` uniquely identifies a record for this dataset.

### 3. Explore the data

- Summarize sales and profit by quantity and product.
- Compare products by quantity sold, total profit, and profit per quantity.
- Calculate correlations between numeric fields.
- Identify potential outliers using the IQR (interquartile range) rule.
- Explore payment methods, sales channels, customer segments, cities, marketing sources, categories, and return status.

### 4. Visualize findings

The notebook creates visualizations including:

- Top-selling products by quantity
- Top products by total profit
- Quantity sold versus profit by product
- Sales-channel distribution
- Payment-method distribution
- Profit by customer segment
- Customer distribution by city
- Net sales by marketing source
- Customer-age distribution
- Net sales by product category
- Correlation heatmap for financial columns
- Returns by product category
- Product profitability and recommendation chart

### 5. Create product recommendations

The notebook compares each product's total profit with the median of product-level profit. Products below the median receive a low-profit suggestion; other products are marked as recommended. This is a simple rule-based classification, not a trained machine-learning model.

### 6. Export the cleaned data

The notebook saves the processed DataFrame as `cleaned_dataset.csv`. In Google Colab, the final cell initiates a download of that CSV file.

## Setup and Usage

### Requirements

- Python 3
- Jupyter Notebook or Google Colab
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn` (for the correlation heatmap)

Install the libraries if needed:

```bash
pip install pandas numpy matplotlib seaborn
```

### Run locally

1. Place `ecom(1).ipynb` and `ecommerce_customer.csv` in the same working directory.
2. Open the notebook in Jupyter Notebook or JupyterLab.
3. Run the cells from top to bottom.
4. Review the cleaning steps and visualizations.
5. Find the exported `cleaned_dataset.csv` in the notebook's working directory.

If using Google Colab, upload the CSV when prompted or place it in the expected Colab working directory. The last cell uses `google.colab.files`, so that download cell is intended for Colab.

## Output

- Charts for exploratory analysis of customers, products, sales, profit, and returns
- `cleaned_dataset.csv` — the cleaned dataset exported by the notebook

## Limitations and Recommendations

- The README does not report specific numerical findings because the dataset's executed results were not independently verified here.
- Validate whether negative financial values are truly invalid for the business context; refunds and adjustments can sometimes be negative.
- Confirm that deduplicating on `Order_ID` and `Customer_ID` does not remove legitimate multiple product lines from an order.
- Use training/test splits and appropriate evaluation metrics if a predictive machine-learning model is added later.

## Project Structure

```text
project/
├── ecom(1).ipynb
├── ecommerce_customer.csv
├── cleaned_dataset.csv   # generated after running the notebook
└── README.md
```
