# 🚀 Space Mission Data Analysis & Price Estimation

## 📌 Project Overview

This project presents an end-to-end analysis of historical space mission data, covering missions from 1957 to 2020.

The project focuses on understanding mission trends, success rates, organizations, countries, mission costs, and relationships between different variables. Since a large portion of the mission price data was missing, machine learning was also used to estimate missing prices while maintaining transparency through prediction methods and reliability levels.

The analysis combines **Exploratory Data Analysis (EDA), Data Preprocessing, Data Visualization, and Machine Learning** to generate meaningful insights from historical space mission data.

---

## 🎯 Project Objectives

The main objectives of this project are:

- Understand the historical space mission dataset
- Clean and preprocess the raw data
- Analyze mission activity across organizations and countries
- Study mission trends over time
- Analyze mission success and failure patterns
- Investigate mission cost distributions
- Handle missing mission price values
- Estimate missing prices using Machine Learning
- Evaluate relationships between mission cost and mission success
- Generate business-oriented insights and recommendations

---

## 📊 Dataset Overview

The dataset contains historical space mission records from **1957 to 2020**.

### Dataset Statistics

| Metric | Value |
|---|---:|
| Total Records | 4,323 |
| Original Records | 4,324 |
| Features after preprocessing | 17 |
| Known Mission Prices | 963 |
| Missing Mission Prices | 3,360 |
| Missing Price Percentage | 77.7% |
| Overall Mission Success Rate | 89.7% |

### Original Dataset Fields

- Organisation
- Location
- Date
- Detail
- Rocket_Status
- Price
- Mission_Status

Additional features were created during preprocessing and analysis.

---

# 🔧 Data Preprocessing

The following preprocessing steps were performed:

### 1. Data Cleaning
- Removed unnecessary index-like columns
- Checked and removed duplicate rows
- Identified missing values
- Checked for placeholder and inconsistent values

### 2. Data Type Conversion
- Converted `Date` from string to datetime
- Converted `Price` from text to numeric
- Removed commas and unwanted characters from price values

### 3. Feature Engineering

New features were extracted from the existing data:

- `Year`
- `Month`
- `Decade`
- `Country`
- `Rocket_Name`
- `Mission_Detail`

### 4. Categorical Data Standardization

Organization and location values were standardized to improve consistency during analysis.

---

# 🔍 Exploratory Data Analysis

The project includes **Univariate, Bivariate, and Multivariate Analysis**.

## 📈 Univariate Analysis

The following distributions were analyzed:

- Mission status
- Mission count by organization
- Mission count by country
- Mission count by month
- Mission price distribution
- Prediction method distribution
- Prediction reliability distribution

## 📊 Bivariate Analysis

Relationships between variables were explored, including:

- Year vs Mission Count
- Year vs Mission Success Rate
- Organization vs Success Rate
- Rocket Status vs Success Rate
- Organization vs Mission Price
- Price Range vs Mission Success Rate
- Year vs Completed Mission Price

## 🌐 Multivariate Analysis

Multiple variables were analyzed together to identify deeper patterns, including:

- Organization × Country × Mission Count
- Year × Organization × Mission Activity
- Organization × Mission Cost × Success Rate

---

# 🤖 Machine Learning – Missing Price Estimation

One of the major challenges in the dataset was the large number of missing mission prices.

Out of 4,323 records:

**3,360 mission prices were missing (~77.7%).**

Instead of simply deleting these records, Machine Learning was explored to estimate missing prices.

### Model Evaluated

Several approaches were evaluated, including:

- Linear Regression
- Random Forest
- Extra Trees
- Rocket Family based models
- Organization-based baselines
- Global Median fallback
- TF-IDF + Ridge

### Final Approach

**Extra Trees Regressor** was selected as the primary estimation model for applicable records.

Features included:

- Organization
- Country
- Rocket Name
- Year
- Month

Because many missing-price missions belonged to rocket names that were not present in the known-price data, a **cold-start problem** existed.

Therefore, predictions were combined with a **Global Median fallback** when the model was considered unreliable.

---

# 💰 Price Estimation Results

The 3,360 missing prices were completed using two methods:

| Prediction Method | Records |
|---|---:|
| Extra Trees | 1,585 |
| Global Median Fallback | 1,775 |
| **Total** | **3,360** |

The original observed prices were preserved.

Additional columns were created:

- `Price_Was_Missing`
- `Estimated_Price_M`
- `Price_Completed_M`
- `Prediction_Method`
- `Prediction_Reliability`

This allows users to distinguish between **observed and estimated prices**.

---

# ⚠️ Prediction Reliability

Prediction reliability was categorized based on the availability of relevant historical price information.

| Reliability | Records |
|---|---:|
| Low | 2,258 |
| Moderate | 338 |
| Higher | 764 |

The reliability classification is project-specific and is intended to provide transparency around estimated prices.

Because a large proportion of the missing-price records have limited historical pricing information, estimated prices should be interpreted as **analytical estimates rather than actual historical costs**.

---

# 📌 Key Insights

### 🚀 Mission Activity

- Russia and the USA account for a large share of historical mission activity.
- RVSN USSR is the organization with the highest number of recorded missions.
- Mission activity increased significantly from the late 1950s through the 1970s.
- Activity declined during several periods before increasing again around 2016–2019.

### ✅ Mission Success

- Overall mission success rate is approximately **89.7%**.
- Success rates were considerably lower during the early years of space exploration.
- Mission success improved substantially through the 1970s and remained generally high in later decades.
- Active rockets showed a slightly higher success rate than retired rockets in this dataset.

### 💰 Mission Cost

- Mission prices are highly right-skewed.
- NASA has a substantially higher median recorded mission price than most organizations.
- RVSN USSR has extremely high recorded prices in only a small number of known-price records, which strongly affects its average and median.
- Price and mission success show an association in some price ranges, but this does **not establish causation**.

### 🤖 Price Estimation

- 1,585 missing prices were estimated using Extra Trees.
- 1,775 records required the Global Median fallback.
- Prediction reliability was retained to make the estimated values more transparent.

---

---

# 💡 Business Insights & Recommendations

The analysis provides several potential applications:

### 1. Cost Benchmarking
Historical mission costs can be used as reference points for preliminary cost benchmarking and planning.

### 2. Mission Reliability Analysis
Historical success rates can help identify patterns across organizations, periods, and mission characteristics.

### 3. Organization Benchmarking
Organizations can be compared based on mission volume, success rate, and available cost information.

### 4. Cost Estimation
Machine learning can provide estimated costs when historical price information is unavailable, provided the predictions are interpreted according to their reliability.

### 5. Data Transparency
Maintaining prediction methods and reliability levels makes estimated values easier to interpret and audit.

---

# 🛠️ Technologies Used

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **Jupyter Notebook**
- **Machine Learning**
- **Exploratory Data Analysis**

---

# 📂 Project Structure

```text
Space-Mission-EDA/
│
├── Space_Mission_EDA.ipynb
├── space_mission_data.csv
├── space_mission_final_predictions.csv
├── README.md
│
└── presentation/
    └── Space-Mission-Dataset-EDA.pdf
