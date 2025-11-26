
Amazon Sales Data 2025 – Exploratory Data Analysis (EDA)

This repository contains an Exploratory Data Analysis (EDA) of Amazon Sales Data 2025. The goal is to understand the dataset, identify patterns, detect anomalies, and summarize key insights.

##Dataset Overview : 
- Rows: 250
- Columns: 11
- Mix of numerical and categorical variables, typical of sales datasets: products, customers, prices, quantities, revenue.
- No column is heavily missing, although some object columns may need conversion (dates, prices).
--
EDA Steps


#1. Load the Dataset
import pandas as pd
df = pd.read_csv("amazon_sales_data 2025.csv")

#2. Preview the Dataset
df.head()
df.tail(

#3. General Information
df.info()

#4. Descriptive Statistics
df.describe(include='all')


Includes:
Mean, median
Min / Max
Standard deviation
Unique values for categorical columns

#5. Missing Values
df.isna().sum()
df.isna().mean() * 100  # percentage

#6. Unique Values
df.nunique()

#7. Categorical Column Analysis
df['Quantity'].value_counts()
df['Quantity'].value_counts(normalize=True) * 100

#8. Numerical Column Analysis

Distribution:

import matplotlib.pyplot as plt
plt.hist(df["Total Sales"])
plt.title("Total Sales")
plt.show()

Outliers Detection:
df["Quantity"].quantile([0.01, 0.25, 0.5, 0.75, 0.99])

#9. Correlation Analysis
corr = df.corr(numeric_only=True)
plt.matshow(corr)
plt.title("Correlation Heatmap")
plt.show()

#10. Time Series Analysis (if Date exists)
df['Date'] = pd.to_datetime(df['Date'])
df.groupby(df['Date'].dt.to_period('M')).sum()

Key Insights

Dataset is well structured, with no major missing values.

Typical sales data: numeric (Unit Sold, Total Revenue) + categorical (Product Type, Invoice ID).

Some object columns can be converted to dates or numeric types.

Temporal trends can be analyzed monthly.

Correlation analysis reveals relationships between numeric variables (exemple: Units Sold <-> Revenue).
