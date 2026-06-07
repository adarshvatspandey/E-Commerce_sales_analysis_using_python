# E-Commerce Sales Analysis Using Python

## Project Overview

This project analyzes an E-Commerce Superstore dataset using Python and Pandas to uncover business insights related to sales performance, profitability, customer behavior, product performance, and regional trends.

The objective is to transform raw transactional data into actionable business recommendations through data analysis and visualization.
![image](https://github.com/adarshvatspandey/E-Commerce_sales_analysis_using_python/blob/6ca3fccfa2729dfeade03d0b8ad1753651531000/images.jpg)
---

## Dataset Information

* Total Records: 9,994
* Country: United States
* Categories: Furniture, Office Supplies, Technology
* Customer Segments: Consumer, Corporate, Home Office

---

## Tools & Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook

---

## Project Workflow

### 1. Data Loading

* Imported dataset using Pandas
* Verified structure and data types

### 2. Data Cleaning

* Checked missing values
* Removed duplicates
* Converted date columns
* Validated numerical fields

### 3. Data Transformation

* Created Shipping Days feature
* Extracted Year and Month from Order Date
* Generated business KPIs

### 4. Exploratory Data Analysis (EDA)

* Sales Analysis
* Profit Analysis
* Customer Analysis
* Product Analysis
* Regional Analysis

---

## Business Questions Solved

### Customer Analytics

* Top 10 Customers by Sales
* Top 10 Customers by Profit
* Repeat Customer Analysis
* RFM Customer Segmentation

### Sales Analytics

* Monthly Sales Trend
* Yearly Sales Trend
* Average Order Value
* Segment-wise Revenue Analysis

### Profitability Analytics

* Profit by Category
* Profit by Region
* Profit Margin Analysis
* Discount Impact on Profit

### Product Analytics

* Top Selling Products
* Most Profitable Products
* Sub-Category Analysis

### Regional Analytics

* Top Revenue Cities
* Most Profitable Cities
* Loss-Making Cities

---

## Key Insights

* Technology category generated the highest sales.
* A small percentage of customers contributed a large share of revenue.
* Heavy discounts negatively impacted profitability.
* Several cities generated losses despite strong sales.
* Consumer segment contributed the largest revenue share.
* Regional performance varied significantly across the business.

---

## Results

The analysis helped identify:

* High-value customers
* Profitable products
* Underperforming regions
* Revenue trends
* Discount optimization opportunities

---

## Future Enhancements

* Sales Forecasting
* Customer Churn Prediction
* Market Basket Analysis
* Profit Prediction Model
* Interactive Power BI Dashboard
# 1. Who are the Top 10 Customers by Sales?

```python
top_customers = (
    data.groupby(['Customer ID','Customer Name'])['Sales']
        .sum()
        .reset_index()
        .sort_values(by='Sales', ascending=False)
        .head(10)
)

top_customers
```

### Insight

The top customers contribute a significant portion of total revenue. These customers should be prioritized through loyalty programs, personalized offers, and premium customer service.

---

# 2. Who are the Top 10 Customers by Profit?

```python
top_profit_customers = (
    data.groupby('Customer Name')['Profit']
        .sum()
        .reset_index()
        .sort_values(by='Profit', ascending=False)
        .head(10)
)

top_profit_customers
```

### Insight

High-profit customers are more valuable than high-sales customers because they contribute directly to business growth.

---

# 3. Which Cities Generate the Highest Sales?

```python
top_cities = (
    data.groupby('City')['Sales']
        .sum()
        .reset_index()
        .sort_values(by='Sales', ascending=False)
        .head(10)
)

top_cities
```

### Insight

These cities represent the strongest revenue-generating markets and should be targeted for future expansion.

---

# 4. Which Cities Generate the Highest Profit?

```python
top_profit_cities = (
    data.groupby('City')['Profit']
        .sum()
        .reset_index()
        .sort_values(by='Profit', ascending=False)
        .head(10)
)

top_profit_cities
```

### Insight

High-profit cities indicate healthy operations and strong customer demand.

---

# 5. Which Cities are Causing Losses?

```python
loss_cities = (
    data.groupby('City')['Profit']
        .sum()
        .reset_index()
        .sort_values(by='Profit')
        .head(10)
)

loss_cities
```

### Insight

These cities require a review of pricing strategies, logistics costs, and discount policies.

---

# 6. Which Category Generates the Highest Sales?

```python
category_sales = (
    data.groupby('Category')['Sales']
        .sum()
        .reset_index()
        .sort_values(by='Sales', ascending=False)
)

category_sales
```

### Insight

The top-performing category contributes the largest share of revenue.

---

# 7. Which Category Generates the Highest Profit?

```python
category_profit = (
    data.groupby('Category')['Profit']
        .sum()
        .reset_index()
        .sort_values(by='Profit', ascending=False)
)

category_profit
```

### Insight

A category with high profit is more valuable than one with high sales but low margins.

---

# 8. Which Sub-Categories Generate the Highest Sales?

```python
subcategory_sales = (
    data.groupby('Sub-Category')['Sales']
        .sum()
        .reset_index()
        .sort_values(by='Sales', ascending=False)
)

subcategory_sales
```

### Insight

These sub-categories are the most popular among customers.

---

# 9. Which Sub-Categories Generate the Highest Profit?

```python
subcategory_profit = (
    data.groupby('Sub-Category')['Profit']
        .sum()
        .reset_index()
        .sort_values(by='Profit', ascending=False)
)

subcategory_profit
```

### Insight

These sub-categories offer the highest returns and should receive greater business focus.

---

# 10. What is the Monthly Sales Trend?

```python
data['Order Date'] = pd.to_datetime(data['Order Date'])

monthly_sales = (
    data.groupby(data['Order Date'].dt.to_period('M'))['Sales']
        .sum()
)

monthly_sales
```

### Insight

Monthly trends help identify seasonality and peak demand periods.

---

# 11. What is the Yearly Sales Trend?

```python
yearly_sales = (
    data.groupby(data['Order Date'].dt.year)['Sales']
        .sum()
)

yearly_sales
```

### Insight

Yearly growth indicates the overall business performance over time.

---

# 12. Which Region Generates the Highest Sales?

```python
region_sales = (
    data.groupby('Region')['Sales']
        .sum()
        .reset_index()
        .sort_values(by='Sales', ascending=False)
)

region_sales
```

### Insight

Top-performing regions contribute most to overall company revenue.

---

# 13. Which Region Generates the Highest Profit?

```python
region_profit = (
    data.groupby('Region')['Profit']
        .sum()
        .reset_index()
        .sort_values(by='Profit', ascending=False)
)

region_profit
```

### Insight

Profitability varies significantly across regions, making regional analysis essential.

---

# 14. What is the Average Order Value?

```python
aov = (
    data.groupby('Order ID')['Sales']
        .sum()
        .mean()
)

print(aov)
```

### Insight

Average Order Value (AOV) measures customer spending behavior and purchasing power.

---

# 15. Which Products are Sold Most Frequently?

```python
top_products = (
    data.groupby('Product Name')['Quantity']
        .sum()
        .reset_index()
        .sort_values(by='Quantity', ascending=False)
        .head(10)
)

top_products
```

### Insight

High-demand products require effective inventory management to avoid stock shortages.

---

# 16. Which Products Generate the Highest Profit?

```python
profitable_products = (
    data.groupby('Product Name')['Profit']
        .sum()
        .reset_index()
        .sort_values(by='Profit', ascending=False)
        .head(10)
)

profitable_products
```

### Insight

These products contribute the most profit and should be highlighted in marketing campaigns.

---

# 17. How Do Discounts Impact Profit?

```python
data[['Discount','Profit']].corr()
```

### Insight

A strong negative correlation suggests that excessive discounting reduces profitability.

---

# 18. What is the Average Shipping Time?

```python
data['Ship Date'] = pd.to_datetime(data['Ship Date'])

data['Shipping Days'] = (
    data['Ship Date'] - data['Order Date']
).dt.days

data['Shipping Days'].mean()
```

### Insight

Shipping efficiency is a key driver of customer satisfaction.

---

# 19. Which Customer Segment Generates the Highest Revenue?

```python
segment_sales = (
    data.groupby('Segment')['Sales']
        .sum()
        .reset_index()
        .sort_values(by='Sales', ascending=False)
)

segment_sales
```

### Insight

Understanding customer segments helps allocate marketing budgets effectively.

---

# 20. Which Customer Segment Generates the Highest Profit?

```python
segment_profit = (
    data.groupby('Segment')['Profit']
        .sum()
        .reset_index()
        .sort_values(by='Profit', ascending=False)
)

segment_profit
```

### Insight

The most profitable segment deserves greater business attention and retention efforts.

