# Sales Data Cleaning & Preparation Project

## Project Overview

This project focuses on the first and most critical stage of the data analytics lifecycle: **Data Immersion, Data Quality Assessment, Data Cleaning, and Data Transformation**.

The objective was to transform a raw sales dataset into an analysis-ready dataset by identifying and resolving data quality issues such as missing values, inconsistent formatting, and potential outliers.

---

## Dataset Information

**Dataset Name:** ApexPlanet Data Analytics Dataset

**Records:** 1000 Rows

**Domain:** Sales & Customer Transactions

The dataset contains customer demographics, product information, transaction details, and sales data.

---

## Project Objectives

* Understand the structure and contents of the dataset.
* Create a data dictionary for all variables.
* Identify data quality issues.
* Clean and preprocess the data.
* Perform feature engineering.
* Generate a final analysis-ready dataset.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Jupyter Notebook / VS Code

---

## Data Quality Assessment

The following checks were performed:

### Missing Values

| Column | Missing Values |
| ------ | -------------- |
| Age    | 20             |
| City   | 13             |

### Duplicate Records

* No duplicate rows were found.

### Data Type Validation

* Verified numerical, categorical, and date columns.
* Converted `Order_Date` to datetime format.

### Outlier Detection

* Applied the IQR (Interquartile Range) method to identify outliers in:

  * Age
  * Quantity
  * Unit Price
  * Total Sales

---

## Data Cleaning Process

### Handling Missing Values

#### Age

Missing values were replaced using the median age.

```python
df["Age"] = df["Age"].fillna(df["Age"].median())
```

#### City

Missing values were replaced using the most frequent city.

```python
df["City"] = df["City"].fillna(df["City"].mode()[0])
```

### Duplicate Removal

```python
df.drop_duplicates(inplace=True)
```

### Text Standardization

* Removed leading/trailing spaces.
* Converted text values to title case.

Example:

```python
df["City"] = df["City"].str.strip().str.title()
```

### Date Standardization

Converted `Order_Date` into datetime format.

```python
df["Order_Date"] = pd.to_datetime(df["Order_Date"])
```

---

## Feature Engineering

Several new features were created to improve future analysis.

### Date Features

* Order_Year
* Order_Month
* Order_Day
* Month_Name

Example:

```python
df["Order_Year"] = df["Order_Date"].dt.year
```

### Age Group Segmentation

Customers were grouped into age categories:

* 18–25
* 26–35
* 36–50
* 50+

### Sales Category

Transactions were categorized as:

* Low
* Medium
* High
* Very High

based on Total Sales value.

---

## Data Dictionary

| Column         | Description                | Data Type   |
| -------------- | -------------------------- | ----------- |
| Order_ID       | Unique order identifier    | String      |
| Order_Date     | Date of order              | Date        |
| Customer_ID    | Unique customer identifier | String      |
| Customer_Name  | Customer name              | String      |
| Age            | Customer age               | Numeric     |
| Gender         | Customer gender            | Categorical |
| City           | Customer city              | Categorical |
| Product        | Product purchased          | Categorical |
| Category       | Product category           | Categorical |
| Quantity       | Number of units purchased  | Numeric     |
| Unit_Price     | Price per unit             | Numeric     |
| Total_Sales    | Total transaction value    | Numeric     |
| Order_Year     | Extracted order year       | Numeric     |
| Order_Month    | Extracted order month      | Numeric     |
| Order_Day      | Extracted order day        | Numeric     |
| Month_Name     | Month name                 | Categorical |
| Age_Group      | Customer age segment       | Categorical |
| Sales_Category | Sales value segment        | Categorical |

---

## Output

The cleaned dataset was exported as:

```text
Cleaned_Sales_Dataset.csv
```

This dataset is ready for:

* Exploratory Data Analysis (EDA)
* Dashboard Creation
* Business Intelligence Reporting
* Machine Learning Applications

---

## Project Structure

```text
├── ApexPlanet_DataAnalytics_Dataset.xlsx
├── data_cleaning.py
├── Cleaned_Sales_Dataset.csv
├── README.md
```

---

## Key Learnings

* Data profiling and quality assessment
* Handling missing values
* Data transformation using Pandas
* Feature engineering
* Outlier detection using IQR
* Preparing datasets for analytics and machine learning

---

## Author

**Navaneethan S**

Data Analytics Internship Project – ApexPlanet
