# Retail-Sales-Analysis
An end-to-end data cleaning and exploratory analysis pipeline that merges retail sales data, stores metadata, and SKU taxomonies. Implements robust outlier detection and winsorization to treat heavily skewed numeric fields like total values and cost prices.  Produces clean, normalized datasets and comparative visualizations ready for predictive.

# Retail Sales Analysis & Outlier Treatment

This repository features a comprehensive, end-to-end Exploratory Data Analysis (EDA) and data cleaning pipeline conducted on retail sales transactional data. The main objective of this project is to clean, merge, analyze, and optimize a highly skewed retail dataset by applying advanced statistical techniques to identify and treat outliers.

## 📌 Project Overview
In retail, datasets often suffer from highly skewed distributions due to bulk orders, high-value items, promotional periods, or customer ID tracking variances. This project explores transactional sales data from a multi-store retailer named **BlueMart**, focusing on handling missing values, merging multidimensional datasets (Sales, Products, and Stores), and implementing robust outlier detection and capping (winsorization).

## 📊 The Datasets
The analysis utilizes three core relational tables:
1. **`bm_sales.csv`**: Transactional logs including purchase dates, store IDs, item quantities, total transaction values, and customer IDs.
2. **`bm_skus.csv`**: Product taxonomy detailing category, subcategory, base cost price, brand information, and standard unit prices.
3. **`bm_stores.csv`**: Store demographics indicating physical location (cities in UAE), store type (Mall, High Street, Community), and opening dates.

## 🛠️ Key Technical Workflow

### 1. Data Merging & Wrangling
* Merged transactional sales data with store metadata and SKU feature files on relational keys (`store_id`, `sku_id`).
* Handled structural differences and resolved duplicate columns (such as multiple unit price columns).

### 2. Missing Value Imputation
* Identified missing indices (predominantly in the `customer_id` column, representing guest checkouts).
* Safely removed or isolated records with missing values to keep downstream models accurate and reliable.

### 3. Exploratory Data Analysis (EDA)
* Generated distributions and boxplots for transaction characteristics like `quantity`, `discount_pct`, `cost_price`, and `total_value`.
* Conducted correlation analyses using Seaborn heatmaps to observe relationships between margins, discounts, and transaction volume.

### 4. Robust Outlier Treatment via Capping
* Analyzed numerical skewness mathematically.
* Calculated Interquartile Range (IQR) boundaries ($Q1 - 1.5 \times IQR$ and $Q3 + 1.5 \times IQR$) across heavily skewed columns.
* Applied a **Capping/Winsorization technique** using `numpy.where` to handle extreme values for `quantity`, `discount_pct`, `cost_price`, and `total_value` without sacrificing data volume.
* Reduced total value distribution skewness from **3.20** down to a healthier **1.16**.

## 📈 Visualizations Included
* **Distribution of Stores by Type**: High Street, Community, and Mall stores.
* **Distribution Plots (KDE + Histograms)**: Exploring product pricing skewness.
* **Interactive Correlation Heatmap**: Revealing profit margins and pricing trends.
* **Before-and-After Boxplot Panels**: Showcasing original distributions side-by-side with their capped counterparts to highlight outlier reductions.

## 🚀 Getting Started

### Prerequisites
Make sure you have the following libraries installed in your Python environment:
```bash
pip install pandas numpy matplotlib seaborn
