# 🌾 PMFBY District-Level Crop Insurance Performance Analysis Using Python (2018–2022)

> A data-driven analysis of Pradhan Mantri Fasal Bima Yojana (PMFBY) district-level crop insurance data to understand farmer participation, seasonal trends, insurance coverage, demographic participation, district performance, and financial contributions.

---

## 📌 Project Overview

This project analyses **PMFBY district-level crop insurance data from 2018 to 2022** using Python.

The analysis focuses on:

- Farmer participation
- Loanee and Non-Loanee participation
- Seasonal participation
- State-wise participation
- District performance
- Gender-wise participation
- Farmer-type participation
- Insurance Unit coverage
- Area Insured
- Sum Insured
- Premium contribution
- Government contribution

The project applies **data cleaning, data transformation, feature engineering, statistical analysis, exploratory data analysis (EDA), visualization and insight generation**.

---

## 🎯 Objectives

## 1. Participation & Seasonal Analysis

- Analyze PMFBY participation across states and districts from 2018–2022.
- Compare PMFBY participation between Kharif and Rabi seasons.

## 2. Farmer Participation Analysis

- Analyze the participation pattern of Loanee and Non-Loanee farmers.
- Examine gender and farmer-type participation patterns.

## 3. Insurance & Financial Analysis

- Evaluate crop insurance coverage across districts using insured area, insurance units, and sum insured.
- Analyze gross premium and the financial contributions of farmers, State Governments, and the Government of India.

## 4. District Performance Assessment

- Identify high- and low-performing districts based on PMFBY participation, insurance coverage, and financial indicators.

---

## ❓ Problem Statement

The raw PMFBY dataset contains information about farmer participation, seasons, states, districts, insurance coverage and financial contributions.

However, the raw data does not directly reveal how participation changes over time, which season has higher participation, differences between farmer groups, state and district variations, insurance relationships, or changes in financial contributions.

This project uses Python-based analysis and visualization to identify these patterns and convert the raw PMFBY data into meaningful insights.

---

## 📂 Dataset Information

| Attribute | Details |
|---|---|
| Dataset | PMFBY District-Level Crop Insurance Data |
| Period | 2018–2022 |
| Records | 6,161 |
| Original Variables | 28 |
| Geography | State and District |
| Seasons | Kharif and Rabi |
| Domain | Agriculture / Crop Insurance |
| Platform | Google Colab |
| Language | Python |

---

## 🛠️ Tools & Technologies

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Google Colab**

---

## 🔄 Project Workflow

```text
Raw Dataset
     ↓
Data Inspection
     ↓
Data Cleaning
     ↓
Missing Value Analysis
     ↓
Duplicate Detection
     ↓
Data Transformation
     ↓
Feature Engineering
     ↓
Statistical Analysis
     ↓
Univariate Analysis
     ↓
Bivariate Analysis
     ↓
Multivariate Analysis
     ↓
Insights & Interpretation
     ↓
Key Findings
     ↓
Recommendations
     ↓
Conclusion
```

---

## 🧹 Data Cleaning

The raw PMFBY dataset was cleaned and prepared before analysis to improve data quality and consistency. The cleaning process followed the steps implemented in the Python notebook.

### Cleaning Steps

1. **Remove unnecessary columns**
   - Removed columns that were not required for the analysis.

2. **Handle duplicate records**
   - Checked the dataset for duplicate records and handled them during data preparation.

3. **Handle missing values**
   - Checked missing values across relevant columns.
   - Missing values were handled using appropriate imputation or removal where required.
   - Derived `Insurance_Per_Application` missing values were filled with `0`.

4. **Clean text and category fields**
   - Checked state and district names for inconsistent formatting.
   - Checked and handled leading/trailing spaces.
   - Checked capitalization and title-case consistency.

5. **Check numerical fields**
   - Reviewed farmer counts, participation, insurance and financial variables for invalid or unusual values.

6. **Check data types**
   - Verified and converted data types where required for analysis.

7. **Outlier review**
   - Extreme observations were reviewed where necessary before statistical analysis.

8. **Final data validation**
   - Performed final null-value checks and verified the cleaned dataset structure before EDA and statistical analysis.

The notebook explicitly defines the Stage 2 workflow as duplicate handling, missing-value handling, unnecessary-column removal, optional outlier treatment, data-type conversion, transformation/wrangling and final EDA. fileciteturn16file0L15-L31

---

## ⚙️ Feature Engineering

### Total Applications

```python
df["Total_Applications"] = (
    df["Loanee"] + df["Non_Loanee"]
)
```

### Total Government Share

```python
df["Total_Government_Share"] = (
    df["GOI_Share"] + df["State_Share"]
)
```

### Total Premium Contribution

```python
df["Total_Premium_Contribution"] = (
    df["Farmer_Share"]
    + df["GOI_Share"]
    + df["State_Share"]
)
```

### Insurance Value per Application

```python
df["Insurance_Per_Application"] = (
    df["Sum_Insured"] /
    df["Total_Applications"]
)
```

---

# 📊 Statistical Analysis

The project uses:

- Mean
- Median
- Mode
- Variance
- Standard Deviation
- Skewness
- Kurtosis

These measures are used to understand the central tendency, variability, distribution and extreme observations in the PMFBY dataset.

---

# 📊 Statistical Analysis Results

The statistical analysis was performed on four key numerical variables: **Total Applications, Area Insured, Sum Insured, and Gross Premium**.

## 1. Measures of Central Tendency

Mean, Median and Mode were calculated to understand the typical values and distribution of the major PMFBY variables. The results show a considerable difference between mean and median for all four variables, indicating right-skewed distributions. fileciteturn10file0L97-L104

| Variable | Mean | Median | Mode |
|---|---:|---:|---:|
| Total Applications | 59,967.75 | 7,723.00 | 0.00 |
| Area Insured | 41.40 | 4.30 | 0.00 |
| Sum Insured | 15,993.39 | 2,554.02 | 0.00 |
| Gross Premium | 2,255.69 | 202.15 | 0.00 |

### Interpretation

- **Total Applications:** The large difference between mean and median indicates that a few districts have very high application counts.
- **Area Insured:** The mean is much higher than the median, indicating that some districts have considerably larger insured areas.
- **Sum Insured:** The difference between mean and median indicates the presence of high-value insurance observations.
- **Gross Premium:** The mean is considerably higher than the median, indicating a right-skewed premium distribution.
- **Overall:** All four variables are right-skewed, and the mode is **0.00** for each variable. fileciteturn9file1L10-L18

![Central Tendency Analysis](images/central_tendency.png)

---

## 2. Variance

Variance measures how widely the observations are spread around the mean. The PMFBY results show substantial variation across all four variables.

| Variable | Variance |
|---|---:|
| Total Applications | 2.607710 × 10¹⁰ |
| Area Insured | 1.560372 × 10⁴ |
| Sum Insured | 1.088210 × 10⁹ |
| Gross Premium | 3.828380 × 10⁷ |

### Interpretation

- **Total Applications** shows very high dispersion in farmer participation across districts.
- **Area Insured** shows considerable variation in crop insurance coverage.
- **Sum Insured** shows substantial variation in insured amounts.
- **Gross Premium** also shows considerable variation between districts.
- **Overall:** The high variance values indicate that PMFBY observations are not evenly distributed across districts.

![Variance Analysis](images/variance.png)

---

## 3. Standard Deviation

Standard deviation indicates the average spread of observations around the mean in the original units.

| Variable | Standard Deviation |
|---|---:|
| Total Applications | 161,484.05 |
| Area Insured | 124.91 |
| Sum Insured | 32,988.04 |
| Gross Premium | 6,187.39 |

### Interpretation

- **Total Applications:** The standard deviation of **161,484.05** indicates a very high spread in farmer participation.
- **Area Insured:** The standard deviation of **124.91** indicates considerable variation in insured area.
- **Sum Insured:** The standard deviation of **32,988.04** indicates substantial variation in insured amounts.
- **Gross Premium:** The standard deviation of **6,187.39** indicates considerable variation in premium values.
- **Overall:** PMFBY participation, insurance coverage and financial values vary considerably across districts.

![Standard Deviation Analysis](images/standard_deviation.png)

---

## 4. Skewness

Skewness measures the direction and degree of asymmetry in a distribution.

| Variable | Skewness |
|---|---:|
| Total Applications | 6.442054 |
| Area Insured | 11.736275 |
| Sum Insured | 4.106434 |
| Gross Premium | 5.459718 |

### Interpretation

- **Total Applications:** A skewness of **6.442054** indicates a highly right-skewed distribution.
- **Area Insured:** A skewness of **11.736275** indicates a very highly right-skewed distribution.
- **Sum Insured:** A skewness of **4.106434** indicates strong right skewness.
- **Gross Premium:** A skewness of **5.459718** indicates a highly right-skewed distribution.
- **Overall:** All four variables are positively skewed, meaning most observations are at relatively lower values while a smaller number have very high values.

![Skewness Analysis](images/skewness.png)

---

## 5. Kurtosis

Kurtosis helps identify heavy-tailed distributions and the presence of extreme observations.

| Variable | Kurtosis |
|---|---:|
| Total Applications | 61.225004 |
| Area Insured | 249.886077 |
| Sum Insured | 27.332569 |
| Gross Premium | 38.954620 |

### Interpretation

- **Total Applications:** A kurtosis of **61.225004** indicates a highly leptokurtic distribution with extreme observations.
- **Area Insured:** A kurtosis of **249.886077** indicates an extremely leptokurtic distribution with very heavy tails.
- **Sum Insured:** A kurtosis of **27.332569** indicates a highly leptokurtic distribution.
- **Gross Premium:** A kurtosis of **38.954620** indicates a highly leptokurtic distribution with extreme premium values.
- **Overall:** All four variables have high positive kurtosis, indicating heavy tails and the presence of extreme observations.

![Kurtosis Analysis](images/kurtosis.png)

---

# 📈 Exploratory Data Analysis

# 1. Univariate Analysis

## 1.1 Distribution of Loanee Farmer Participation

### Objective
To analyse the distribution of Loanee farmer participation across observations.

![Loanee Farmer Distribution](images/loanee_distribution.png)

### Interpretation

- **Key Insight:** Loanee farmer participation shows considerable variation across observations.
- **Pattern:** Most observations have comparatively lower participation, while a smaller number record higher participation.
- **Observation:** The distribution contains high-value observations.
- **Overall:** Loanee participation is unevenly distributed across the dataset.

---

## 1.2 Distribution of Non-Loanee Farmer Participation

### Objective
To analyse the distribution of Non-Loanee farmer participation across observations.

![Non-Loanee Farmer Distribution](images/non_loanee_distribution.png)

### Interpretation

- **Key Insight:** Non-Loanee participation varies considerably across observations.
- **Pattern:** Most observations are concentrated at comparatively lower participation levels.
- **Observation:** A smaller number record considerably higher participation.
- **Overall:** The distribution indicates substantial variation in Non-Loanee participation.

---

## 1.3 Distribution of Insurance Units

### Objective
To analyse the distribution of Insurance Units across observations.

![Insurance Unit Distribution](images/insurance_unit_distribution.png)

### Interpretation

- **Key Insight:** Insurance Unit values show considerable variation across observations.
- **Pattern:** Most observations have comparatively lower Insurance Unit values.
- **Observation:** A smaller number of observations record exceptionally high values.
- **Overall:** The distribution indicates substantial variation and a positively skewed pattern.

---

# 2. Bivariate Analysis

## 2.1 Year-wise Trend of Total Applications

### Objective
To analyse the yearly trend of PMFBY Total Applications from 2018 to 2022.

![Year-wise Total Applications](images/yearly_total_applications.png)

### Interpretation

- **Key Insight:** Total Applications show a **continuous increasing trend** from 2018 to 2022.
- **Pattern:** Applications increased gradually from **2018 to 2020**, followed by a stronger increase in **2021 and 2022**.
- **Observation:** The highest Total Applications were recorded in **2022**, while the lowest were recorded in **2018**.
- **Trend:** The chart indicates a **strong upward trend in PMFBY participation**.
- **Overall:** PMFBY participation increased substantially between **2018 and 2022**.

---

## 2.2 Season-wise Comparison of PMFBY Total Applications

### Objective
To compare PMFBY participation between Kharif and Rabi seasons.

![Season-wise Applications](images/season_wise_applications.png)

### Interpretation

- **Key Insight:** **Kharif participation remained higher than Rabi participation** throughout the study period.
- **Pattern:** Both Kharif and Rabi applications show an overall increasing trend.
- **Observation:** Kharif applications increased from approximately **3.43 Cr in 2018 to 6.75 Cr in 2022**.
- **Observation:** Rabi applications increased from approximately **2.33 Cr in 2018 to 3.76 Cr in 2022**.
- **Overall:** Kharif remained the **dominant season** for PMFBY participation.

---

## 2.3 Loanee vs Non-Loanee Farmer Participation

### Objective
To compare the overall participation of Loanee and Non-Loanee farmers.

![Loanee vs Non-Loanee](images/loanee_vs_non_loanee.png)

### Interpretation

- **Key Insight:** **Loanee farmers have substantially higher participation than Non-Loanee farmers**.
- **Pattern:** A clear participation difference exists between the two groups.
- **Observation:** Loanee farmers account for the major share of farmer participation.
- **Comparison:** Non-Loanee participation remains considerably lower.
- **Overall:** The analysis indicates a significant participation gap between Loanee and Non-Loanee farmers.

---

## 2.4 Relationship Between Area Insured and Sum Insured

### Objective
To analyse the relationship between Area Insured and Sum Insured.

![Area Insured vs Sum Insured](images/area_vs_sum_insured.png)

### Interpretation

- **Key Insight:** Area Insured and Sum Insured show a generally **positive relationship**.
- **Pattern:** Larger insured areas generally tend to have higher Sum Insured values.
- **Observation:** Some variation exists across individual observations.
- **Overall:** Higher insured area is generally associated with higher insurance value.

---

# 3. Multivariate Analysis

## 3.1 Year-wise and Season-wise Trend of PMFBY Applications

### Objective
To analyse PMFBY applications simultaneously across different years and seasons.

![Year Season Applications](images/year_season_applications.png)

### Interpretation

- **Key Insight:** **Kharif participation remained higher than Rabi participation** in every analysed year.
- **Pattern:** Both seasons show an overall increasing trend.
- **Observation:** Kharif increased from **3.43 Cr in 2018 to 6.75 Cr in 2022**.
- **Observation:** Rabi increased from **2.33 Cr in 2018 to 3.76 Cr in 2022**.
- **Overall:** Kharif remained the **dominant season** for PMFBY participation.

---

## 3.2 State-wise PMFBY Participation Across Years

### Objective
To analyse state-wise PMFBY participation and identify variations across years.

![State-wise Applications Heatmap](images/state_wise_applications_heatmap.png)

### Interpretation

- **Key Insight:** PMFBY participation varies considerably across states and years.
- **Pattern:** Some states consistently record higher participation than others.
- **Observation:** Participation levels are not uniform across geographical regions.
- **Comparison:** State-level differences are visible across multiple years.
- **Overall:** The heatmap highlights significant **state-wise and year-wise variation** in PMFBY participation.

---

## 3.3 Top 10 Districts by Insurance Value per Application

### Objective
To identify the top districts based on Insurance Value per Application.

![Top 10 Districts](images/top10_district_insurance_per_application.png)

### Interpretation

- **Key Insight:** **Nuh** recorded the highest Insurance Value per Application at approximately **1.55 Lakhs**.
- **Comparison:** **Sirsa** recorded approximately **1.12 Lakhs**, while **Karnal** recorded approximately **1.06 Lakhs**.
- **Pattern:** Insurance Value per Application gradually decreases across the selected top 10 districts.
- **Observation:** A district with a high number of applications does not necessarily have the highest Insurance Value per Application.
- **Overall:** **Nuh** recorded the highest Insurance Value per Application among the selected top 10 districts.

---

## 3.4 Overall Gender-wise Farmer Participation

### Objective
To analyse the overall distribution of farmer participation by gender.

![Gender Participation](images/overall_gender_participation.png)

### Interpretation

- **Key Insight:** **Male farmers account for 85.9%** of overall participation.
- **Observation:** **Female farmers account for 14.1%** of overall participation.
- **Observation:** **Transgender farmers account for 0.1%** of overall participation.
- **Pattern:** Male participation is substantially higher than Female and Transgender participation.
- **Overall:** The chart indicates a significant **gender participation gap** in PMFBY participation.

---

## 3.5 Year-wise Total Premium and Government Contribution

### Objective
To compare Total Premium Contribution and Government Share across years.

![Financial Contribution](images/yearly_financial_contribution.png)

### Interpretation

- **Key Insight:** **Total Premium Contribution remained higher than Total Government Share** in every analysed year.
- **Pattern:** Total Premium Contribution increased up to around **2020**.
- **Observation:** Total Government Share also increased up to around **2020**.
- **Trend:** Both financial measures declined after 2020.
- **Overall:** The chart shows that financial contributions reached their highest levels around **2020** and declined thereafter.

---

## 3.6 Farmer-Type Participation Across Years

### Objective
To analyse participation trends across Small, Marginal and Other farmer categories.

![Farmer Type Participation](images/farmer_type_participation.png)

### Interpretation

- **Key Insight:** **Small farmers have the highest participation** across the analysed years.
- **Pattern:** Marginal farmers record the next highest participation, followed by Other farmers.
- **Observation:** Small farmer participation decreased from approximately **88,036 in 2018 to 69,161 in 2022**, with a partial recovery after 2021.
- **Observation:** Marginal farmer participation decreased from approximately **30,458 in 2018 to 22,007 in 2022**.
- **Observation:** Other farmer participation decreased from approximately **31,289 in 2018 to 16,632 in 2022**.
- **Overall:** Small farmers remain the **dominant participating group**, while Marginal and Other farmer participation generally declined.

---

# 🔑 Key Findings

- PMFBY Total Applications show a **strong overall increase from 2018 to 2022**.
- **Kharif** remained the dominant season throughout the study period.
- **Loanee** participation is substantially higher than Non-Loanee participation.
- PMFBY participation varies considerably across states and districts.
- Area Insured and Sum Insured show a generally positive relationship.
- **Male farmers represent 85.9%** of overall participation.
- **Female farmers represent 14.1%** of overall participation.
- **Transgender farmers represent 0.1%** of overall participation.
- **Small farmers** form the largest participating farmer category.
- **Nuh** recorded the highest Insurance Value per Application among the selected top 10 districts.
- Total Premium Contribution remained higher than Total Government Share.
- Several numerical variables show considerable variation, skewness and extreme observations.

---

# 💡 Business Insights

### 👨‍🌾 Farmer Participation
The increasing trend in Total Applications indicates growing PMFBY participation between 2018 and 2022.

### 🌱 Seasonal Participation
Kharif participation is consistently higher than Rabi participation, showing a clear seasonal difference.

### 👥 Farmer Groups
The large difference between Loanee and Non-Loanee participation highlights an important area for further investigation.

### 👩 Gender Participation
The Male–Female participation gap indicates an opportunity for further analysis and targeted awareness initiatives.

### 🗺️ Regional Performance
State and district-level differences show that PMFBY participation is not uniform across regions.

### 💰 Financial Performance
The comparison between Total Premium Contribution and Government Share provides insight into the financial contribution structure.

### 📊 District Performance
Insurance Value per Application varies across districts, showing that application volume alone does not fully represent insurance performance.

---

# 🧠 Analytical Framework

## Descriptive Analysis — What Happened?

The analysis summarizes PMFBY participation, seasonal trends, insurance coverage, farmer demographics, district performance and financial contributions using descriptive statistics and visualizations.

## Diagnostic Analysis — Why Did It Happen?

The analysis identifies differences across seasons, regions and farmer groups.

Loanee, gender and farmer-type participation show clear differences, while Insurance Value per Application also varies across districts.

High skewness and kurtosis indicate substantial variation and extreme observations.

These are observed patterns and should not be treated as confirmed causal relationships without additional external data.

## Predictive Analysis — What May Happen?

Historical PMFBY trends can support future estimation of:

- Year-wise applications
- Seasonal participation
- State-level participation
- District-level participation
- Insurance coverage
- Financial contributions

Reliable prediction would require a suitable predictive model, sufficient historical data and proper validation.

## Prescriptive Analysis — What Should Be Done?

- Monitor low-participation regions and farmer groups.
- Strengthen outreach to Non-Loanee farmers.
- Improve awareness and accessibility for Female farmers.
- Study high-performing districts such as **Nuh, Sirsa and Karnal**.
- Monitor seasonal participation trends.
- Monitor farmer-type participation trends.
- Monitor financial contribution trends.
- Validate extreme values and data completeness before advanced modelling.

---

# 💡 Recommendations

### 1. Improve Data Quality
Validate missing values, duplicate records, inconsistent district names and extreme observations before advanced modelling.

### 2. Strengthen Non-Loanee Participation
Investigate the participation gap between Loanee and Non-Loanee farmers and identify opportunities to improve Non-Loanee participation.

### 3. Improve Female Farmer Participation
The significant Male–Female participation gap indicates an opportunity for targeted awareness and accessibility initiatives.

### 4. Monitor Seasonal Participation
Track Kharif and Rabi separately because participation levels differ considerably between the two seasons.

### 5. Study High-Performing Districts
Further analyse districts such as **Nuh, Sirsa and Karnal** to understand factors associated with higher Insurance Value per Application.

### 6. Monitor Farmer-Type Trends
Track changes in Small, Marginal and Other farmer participation over time.

### 7. Monitor Financial Contributions
Regularly analyse Farmer Share, GOI Share, State Share, Total Premium Contribution and Total Government Share.

---

# 🚀 Future Scope

- Automate the PMFBY analysis workflow.
- Add new years when updated PMFBY data becomes available.
- Build predictive models for future participation.
- Forecast seasonal participation.
- Forecast state-level and district-level participation.
- Add crop-level analysis.
- Analyse crop-wise insurance performance.
- Integrate rainfall and weather information.
- Analyse relationships between crop type, insured area, premium and claims.
- Develop an interactive dashboard in the future if required.

---

# 📁 Project Structure

```text
PMFBY-District-Crop-Insurance-Analysis/
│
├── PMFBY_Analysis.ipynb
├── agri_db.csv
├── README.md
│
└── images/
    ├── loanee_distribution.png
    ├── non_loanee_distribution.png
    ├── insurance_unit_distribution.png
    ├── yearly_total_applications.png
    ├── season_wise_applications.png
    ├── loanee_vs_non_loanee.png
    ├── area_vs_sum_insured.png
    ├── year_season_applications.png
    ├── state_wise_applications_heatmap.png
    ├── top10_district_insurance_per_application.png
    ├── overall_gender_participation.png
    ├── yearly_financial_contribution.png
    └── farmer_type_participation.png
```

---

# ▶️ How to Run

### Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn
```

### Run the Notebook

Open:

```text
PMFBY_Analysis.ipynb
```

Run the cells sequentially to reproduce the data cleaning, feature engineering, statistical analysis, charts and insights.

---

# 📚 Analysis Techniques Used

```text
✔ Data Inspection
✔ Data Cleaning
✔ Missing Value Analysis
✔ Duplicate Detection
✔ Data Validation
✔ Data Transformation
✔ Feature Engineering
✔ Descriptive Statistics
✔ Mean
✔ Median
✔ Mode
✔ Variance
✔ Standard Deviation
✔ Skewness
✔ Kurtosis
✔ Univariate Analysis
✔ Bivariate Analysis
✔ Multivariate Analysis
✔ Trend Analysis
✔ Relationship Analysis
✔ State-wise Analysis
✔ District-wise Analysis
✔ Seasonal Analysis
✔ Demographic Analysis
✔ Financial Analysis
✔ Business Insight Generation
```

---

# 📓 Google Colab

[Open PMFBY Analysis Notebook](https://colab.research.google.com/drive/1bsqRNcTacpBGAmpWrrPChfqWM5xrXRW8)

---

# 📌 Project Summary

| Category | Details |
|---|---|
| Project | PMFBY District-Level Crop Insurance Performance Analysis |
| Domain | Agriculture / Crop Insurance |
| Period | 2018–2022 |
| Records | 6,161 |
| Original Variables | 28 |
| Language | Python |
| Analysis | Statistical Analysis + EDA |
| Visualization | Matplotlib + Seaborn |
| Platform | Google Colab |

---

# 🏁 Conclusion

This project demonstrates how Python can be used to analyse real-world **PMFBY district-level crop insurance data** and transform raw agricultural insurance records into meaningful insights.

The analysis identifies important patterns in:

- Farmer participation
- Seasonal participation
- Loanee and Non-Loanee participation
- Gender participation
- Farmer-type participation
- Insurance coverage
- State-wise participation
- District performance
- Financial contributions

Overall, PMFBY participation increased between **2018 and 2022**, with **Kharif remaining the dominant season and Loanee farmers forming the major participation group**.

The project also highlights significant differences in gender participation, farmer-type participation, state-level participation, district-level Insurance Value per Application and financial contributions.

This project demonstrates practical skills in **data preprocessing, feature engineering, statistical analysis, exploratory data analysis, data visualization and business-oriented insight generation using Python**.

---

# 👩‍💻 Author

**SOWMIYA M**

### Skills Demonstrated

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `EDA` · `Data Cleaning` · `Feature Engineering` · `Statistical Analysis` · `Data Visualization` · `Business Analysis`
