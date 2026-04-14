# 🧹  Data Cleaning & Pipeline

This repository contains a comprehensive Data Cleaning pipeline implemented in Python using a Jupyter Notebook. The project focuses on transforming "dirty" Customer data into a structured, analysis-ready format by addressing missing values, inconsistent formatting, outliers, and duplicates.

## 📊 Dataset Overview
The initial dataset consisted of **10,200 rows** with the following columns:
* **Identifiers**: `Customer_ID`, `Name`, `Email`, `Phone_Number`
* **Demographics**: `Gender`, `Age`, `City`, `Country`
* **Engagement**: `Signup_Date`, `Last_Purchase_Date`, `Purchase_Amount`, `Feedback_Score`

## 🛠️ Cleaning Operations Performed

### 1. Handling Missing Values & Nulls
- [cite_start]**Critical Identifiers**: Removed rows where `Customer_ID` was null[cite: 12].
- [cite_start]**Categorical Imputation**: Filled missing `Gender`, `City`, and `Country` values using the **Mode** (most frequent value)[cite: 25].
- **Numerical Imputation**: 
    - [cite_start]Filled `Purchase_Amount` using the **Median** to avoid outlier bias[cite: 22].
    - [cite_start]Filled `Feedback_Score` using the **Median** score[cite: 75, 76].
- [cite_start]**Temporal Data**: Applied **Forward Fill (ffill)** for `Last_Purchase_Date` to maintain chronological consistency[cite: 26].

### 2. Data Standardization & Regex
- [cite_start]**Age Extraction**: Used **Regular Expressions (Regex)** to extract numeric digits from strings like "51.0 years" or "40 years"[cite: 15].
- **Text Normalization**: 
    - [cite_start]Standardized `Gender` into two clean categories: `male` and `female`[cite: 28, 29].
    - [cite_start]Normalized `City` and `Country` to lowercase and removed leading/trailing whitespaces[cite: 31, 32, 33].
- [cite_start]**Data Typing**: Converted date columns to `datetime64` objects and age to `int64`[cite: 41, 44, 45].

### 3. Duplicate Management
- [cite_start]Identified and removed global duplicates[cite: 35].
- [cite_start]Handled business-logic duplicates by keeping the first occurrence of unique `Customer_ID` entries[cite: 38].

### 4. Outlier Detection
- [cite_start]Utilized **Z-Score** analysis to identify and filter out statistical outliers in `Age` and `Purchase_Amount` (e.g., removing entries with age 250 or negative purchase amounts)[cite: 51, 54].
- [cite_start]Verified data distribution using **Boxplots** generated via `Seaborn`[cite: 54].

## 💻 Technologies Used
- **Python**
- **Pandas**: Data manipulation and cleaning.
- **NumPy**: Mathematical operations.
- **Regex (`re`)**: Pattern matching for string cleaning.
- **Matplotlib/Seaborn**: Data visualization and outlier detection.
- **Scipy**: Statistical Z-score calculation.

## 🚀 How to Use
1. Clone this repository.
2. Ensure you have the required libraries installed:
   ```bash
   pip install pandas matplotlib seaborn scipy numpy
