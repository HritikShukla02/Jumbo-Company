## Objective

This analysis evaluates insurance attachment rates for 163 different sellers  across six branch regions to identify performance patterns, understand regional variations, and provide actionable insights for strategic decision-making.
**Key Objectives:**
- Benchmark and compare regional performance to identify top-performing branches
- Analyze statistical significance of performance differences across regions
- Segment stores into performance clusters for targeted interventions
- Identify trends and forecast future attachment rates to support proactive planning

Through comprehensive data analysis and visualization, this report delivers evidence-based recommendations to optimize insurance sales effectiveness across all regions.

> In order to get executive level insights without going through all the details, reffer to the ppt or pdf provided. External link to ppt: [link to google slides](https://docs.google.com/presentation/d/10vYMt8oZ3lPKdbfivYSIboKXHsOyk4U6sfzC5HtpN4s/edit?usp=sharing)


## Dataset Deccriptives

| Statistic | Dec      | Nov      | Oct      | Sep      | Aug      | Average  | Average_Rate |
|----------|----------|----------|----------|----------|----------|----------|---------------|
| count    | 163.0000 | 163.0000 | 163.0000 | 163.0000 | 163.0000 | 163.0000 | 163.0000 |
| mean     | 0.217239 | 0.217117 | 0.170920 | 0.167301 | 0.128589 | 0.180233 | 0.180233 |
| std      | 0.173270 | 0.131246 | 0.116125 | 0.134518 | 0.116640 | 0.103524 | 0.103524 |
| min      | 0.000000 | 0.000000 | 0.000000 | 0.000000 | 0.000000 | 0.000000 | 0.000000 |
| 25%      | 0.095000 | 0.130000 | 0.100000 | 0.080000 | 0.035000 | 0.117000 | 0.117000 |
| 50%      | 0.200000 | 0.200000 | 0.160000 | 0.150000 | 0.110000 | 0.164000 | 0.164000 |
| 75%      | 0.300000 | 0.295000 | 0.240000 | 0.245000 | 0.190000 | 0.235000 | 0.235000 |
| max      | 1.000000 | 0.700000 | 0.710000 | 0.800000 | 0.600000 | 0.622000 | 0.622000 |

- **Scope:** 163 stores across 6 branch regions, tracking insurance attachment rates over 5 months
- **Overall Trend:** Moderate improvement observed in early months, followed by stabilization, indicating improving sales effectiveness
- **Recent Performance:** Growth has plateaued in the last 2 months, coinciding with reduced transaction volumes and increased performance variability (higher standard deviation)
- **Outlier Presence:** Significant outliers detected with maximum attachment rates substantially exceeding the third quartile across regions
- **Data Quality Note:** Some entries show 80-100% attachment rates but correspond to very low customer counts, requiring careful interpretation during analysis


## Branch Level Performance Benchmarking

<img src="./images/Branch Level Performance Benchmarking.png">

#### Summary Statistics

**Overall Average:** 0.18%

#### Branch Performance

| Branch       | Performance |
|-------------|-------------|
| Pune        | 0.276500    |
| Delhi_Ncr   | 0.243682    |
| Mumbai      | 0.173474    |
| Thane       | 0.148600    |
| Gujarat     | 0.134583    |
| Telangana   | 0.118350    |

**Branches Above Average:** 2  
**Branches Below Average:** 4

- **Top tier:** Pune (27.7%) and Delhi_NCR (24.4%) form the high-performance cluster, converting approximately 1 in 4 customers
- **Bottom tier:** Four branches (Mumbai, Thane, Gujarat, Telangana) range from 11.8% to 17.3%, converting only 1 in 7-8 customers
- **Performance gap:** 12 percentage point difference between high and low performers represents an 81% effectiveness gap
- **Overall benchmark:** Only 2 out of 6 branches (33%) exceed the company average of 18%, indicating significant improvement potential


## Understanding Monthly Branch level performances

<img src="./images/Understanding Monthly Branch level performances.png">

### Branch Rankings by Month

| Branch       | Aug | Sep | Oct | Nov | Dec |
|-------------|-----|-----|-----|-----|-----|
| Delhi_Ncr   | 2   | 2   | 2   | 2   | 2   |
| Gujarat     | 5   | 5   | 5   | 6   | 3   |
| Mumbai      | 3   | 3   | 3   | 3   | 4   |
| Pune        | 1   | 1   | 1   | 1   | 1   |
| Telangana   | 6   | 6   | 6   | 4   | 5   |
| Thane       | 4   | 4   | 4   | 5   | 6   |

---

### Biggest Ranking Changes (Aug to Dec)

#### Biggest Improvements (moved up)
- **Gujarat:** moved up 2 positions  
- **Telangana:** moved up 1 position  

#### Biggest Declines (moved down)
- **Mumbai:** moved down 1 position  
- **Thane:** moved down 2 positions  


## Monthly Outliers Analysis

<img src="./images/Monthly Outliers Analysis.png">

### Outlier Analysis by Branch

> **Note:** Each store is analyzed 5 times, one for each month.

#### Branches Ranked by Number of Outliers

| Branch       | Outliers | Percentage | IQR  | Range              |
|-------------|----------|------------|------|--------------------|
| Pune        | 8        | 10.0%      | 0.15 | [0.00, 0.71]       |
| Delhi_Ncr   | 4        | 1.8%       | 0.18 | [0.00, 1.00]       |
| Telangana   | 4        | 2.0%       | 0.13 | [0.00, 0.83]       |
| Gujarat     | 1        | 0.8%       | 0.12 | [0.00, 0.46]       |
| Mumbai      | 1        | 1.1%       | 0.14 | [0.00, 0.60]       |
| Thane       | 0        | 0.0%       | 0.16 | [0.00, 0.44]       |

---

### Summary

- **Branch with most outliers:** Pune (8 outliers)  
- **Branch with least outliers:** Thane (0 outliers)  

**Average outliers per branch:** 3.0  
**Total outliers across all branches:** 18  



## Branch Level Outlier Analysis with ANOVA and Tukey HSD tests

<img src="./images/Branch Level Outlier Analysis with ANOVA and Tukey HSD tests.png">

### Store-Level Outlier Analysis by Branch

> **Note:** Each store is analyzed once using its 5-month average.

#### Branches Ranked by Number of Outlier Stores

| Branch       | Total Stores | Outlier Stores | Outlier % | IQR   | Range            |
|-------------|--------------|----------------|-----------|-------|------------------|
| Telangana   | 40           | 2              | 5.0%      | 5.90  | [0.00, 29.00]    |
| Delhi_Ncr   | 44           | 1              | 2.3%      | 14.95 | [6.40, 62.20]    |
| Pune        | 16           | 1              | 6.2%      | 10.30 | [10.60, 58.60]   |
| Gujarat     | 24           | 1              | 4.2%      | 5.70  | [0.00, 22.40]    |
| Thane       | 20           | 1              | 5.0%      | 9.00  | [0.00, 36.20]    |
| Mumbai      | 19           | 0              | 0.0%      | 10.50 | [0.00, 33.60]    |

---

### ANOVA Analysis (Store-Level)

- **F-statistic:** 14.5393  
- **P-value:** 0.000000  

#### Effect Size
- **η² (Eta-squared):** 0.3165  
- **Interpretation:** Branch explains **31.65%** of variance.

#### Pairwise Significant Differences (p < 0.05)

- **Delhi_Ncr vs Gujarat:** p = 0.0000, diff = 10.91%  
- **Delhi_Ncr vs Thane:** p = 0.0011, diff = 9.51%  
- **Delhi_Ncr vs Telangana:** p = 0.0000, diff = 12.53%  
- **Delhi_Ncr vs Mumbai:** p = 0.0429, diff = 7.02%  
- **Pune vs Gujarat:** p = 0.0000, diff = 14.19%  
- **Pune vs Thane:** p = 0.0003, diff = 12.79%  
- **Pune vs Telangana:** p = 0.0000, diff = 15.82%  
- **Pune vs Mumbai:** p = 0.0080, diff = 10.30%  


## Branch level Statistics

<img src="./images/Branch level Statistics.png">

### Performance Cluster Analysis

#### Cluster Overview
- **High Performers (2):** Pune, Delhi_Ncr  
- **Lower Performers (4):** Mumbai, Thane, Gujarat, Telangana  

---

#### High Performers

| Branch     | Mean Performance | Std Dev |
|------------|------------------|---------|
| Pune       | 27.65%           | 0.1605  |
| Delhi_Ncr  | 24.37%           | 0.1507  |

---

#### Lower Performers

| Branch     | Mean Performance | Std Dev |
|------------|------------------|---------|
| Mumbai     | 17.35%           | 0.1218  |
| Thane      | 14.86%           | 0.1123  |
| Gujarat    | 13.46%           | 0.0894  |
| Telangana  | 11.83%           | 0.1109  |

---

#### Cluster-Level Summary

- **High Performers Average:** 26.01%  
- **Lower Performers Average:** 14.38%  
- **Performance Gap:** 11.63%  
- **Relative Difference:** 80.93%  



## Classifying Stores Based on Performance

<img src="./images/Classifying Stores Based on Performance.png">

#### Store Performance Classification Report

---

### Classification Criteria

- **Lower Fence (Q1 − 1.5×IQR):** −0.0600%  
- **Q1 (25th Percentile):** 0.1170%  
- **Median (50th Percentile):** 0.1640%  
- **Q3 (75th Percentile):** 0.2350%  
- **Upper Fence (Q3 + 1.5×IQR):** 0.4120%  
- **IQR (Interquartile Range):** 0.1180%  

---

### Overall Classification Summary

| Category                              | Count | Percentage | Avg Rate |
|--------------------------------------|-------|------------|----------|
| Average Performer (Above Median)     | 43    | 26.4%      | 0.1945%  |
| Average Performer (Below Median)     | 38    | 23.3%      | 0.1346%  |
| High Performer                       | 38    | 23.3%      | 0.3017%  |
| Low Performer                        | 41    | 25.2%      | 0.0686%  |
| Outlier (High)                       | 3     | 1.8%       | 0.5407%  |

---

### Classification by Branch

#### Delhi_Ncr
- Average Performer (Above Median): **11 stores (25.0%)**
- Average Performer (Below Median): **5 stores (11.4%)**
- High Performer: **22 stores (50.0%)**
- Low Performer: **5 stores (11.4%)**
- Outlier (High): **1 store (2.3%)**

#### Gujarat
- Average Performer (Above Median): **8 stores (33.3%)**
- Average Performer (Below Median): **10 stores (41.7%)**
- Low Performer: **6 stores (25.0%)**

#### Mumbai
- Average Performer (Above Median): **5 stores (26.3%)**
- Average Performer (Below Median): **5 stores (26.3%)**
- High Performer: **4 stores (21.1%)**
- Low Performer: **5 stores (26.3%)**

#### Pune
- Average Performer (Above Median): **5 stores (31.2%)**
- High Performer: **8 stores (50.0%)**
- Low Performer: **1 store (6.2%)**
- Outlier (High): **2 stores (12.5%)**

#### Telangana
- Average Performer (Above Median): **6 stores (15.0%)**
- Average Performer (Below Median): **14 stores (35.0%)**
- High Performer: **2 stores (5.0%)**
- Low Performer: **18 stores (45.0%)**

#### Thane
- Average Performer (Above Median): **8 stores (40.0%)**
- Average Performer (Below Median): **4 stores (20.0%)**
- High Performer: **2 stores (10.0%)**
- Low Performer: **6 stores (30.0%)**

---

### Actionable Insights

#### High-Performing Outliers Identified (3)
> Study best practices for replication

- **Delhi (Hauz Khas)** – Delhi_Ncr: **0.622%**
- **Pune (Kondhawa)** – Pune: **0.414%**
- **Pune (Hadapsar)** – Pune: **0.586%**

#### Stores Needing Immediate Attention (41)
> Require intervention, training, or support

- MAHIM (VS Next) – Mumbai: **0.000%**
- Ts (Jubilee Hills) – Telangana: **0.080%**
- Ts (Warangal) – Telangana: **0.040%**
- Nallasopara Br – Thane: **0.086%**
- Currey Road – Thane: **0.000%**
- Chembur Br – Mumbai: **0.114%**
- Ts (Attapur) – Telangana: **0.116%**
- Gandhinagar (Sargasan) – Gujarat: **0.052%**
- Ahmedabad (Chandkheda Rd) Br – Gujarat: **0.106%**
- Ts (Nagole) – Telangana: **0.116%**

---

### Branch-Level Insights

#### Delhi_Ncr
- High Performers: **23 / 44 (52.3%)**
- Low Performers: **5 / 44 (11.4%)**
- **→ Strong branch overall**

#### Gujarat
- High Performers: **0 / 24 (0.0%)**
- Low Performers: **6 / 24 (25.0%)**

#### Mumbai
- High Performers: **4 / 19 (21.1%)**
- Low Performers: **5 / 19 (26.3%)**

#### Pune
- High Performers: **10 / 16 (62.5%)**
- Low Performers: **1 / 16 (6.2%)**
- **→ Strong branch overall**

#### Telangana
- High Performers: **2 / 40 (5.0%)**
- Low Performers: **18 / 40 (45.0%)**

#### Thane
- High Performers: **2 / 20 (10.0%)**
- Low Performers: **6 / 20 (30.0%)**

---

### Exporting Results

✅ Classification results exported to: **`store_classification_results.csv`**


## Forecasts for the month of January

<img src="./images/Forecasts for the month of January.png">

### Hierarchical Forecast Model — January 2025

**Model:** Store Trend (60%) + Branch Trend (40%) with adaptive weighting  
*Branch information leveraged to improve forecast accuracy*

---

#### Branch-Level Forecast Summary

| Branch      | Dec   | Jan (F) | Change | R² (Store) | R² (Branch) | R² (Avg) | # High |
|-------------|-------|---------|--------|------------|-------------|----------|--------|
| Delhi_Ncr   | 28.3% | 32.5% ↑ | 4.16%  | 0.408      | 0.935       | 0.672    | 0 / 44 |
| Gujarat     | 19.1% | 20.7% ↑ | 1.61%  | 0.342      | 0.747       | 0.544    | 0 / 24 |
| Mumbai      | 18.3% | 24.6% ↑ | 6.29%  | 0.354      | 0.508       | 0.431    | 0 / 19 |
| Pune        | 28.8% | 38.0% ↑ | 9.19%  | 0.419      | 0.607       | 0.513    | 0 / 16 |
| Telangana   | 18.1% | 23.3% ↑ | 5.18%  | 0.433      | 0.840       | 0.636    | 0 / 40 |
| Thane       | 15.2% | 18.0% ↑ | 2.78%  | 0.377      | 0.236       | 0.307    | 0 / 20 |

---

#### Forecast Confidence Summary

| Confidence Level | Stores | Percentage | Avg Combined R² |
|------------------|--------|------------|------------------|
| Low              | 160    | 98.2%      | 0.555            |
| Medium           | 3      | 1.8%       | 0.745            |

---

#### Trend Direction Summary

| Trend        | Stores | Percentage | Avg Jan Forecast |
|--------------|--------|------------|------------------|
| Increasing   | 118    | 72.4%      | 24.06%           |
| Decreasing   | 38     | 23.3%      | 31.71%           |
| Stable       | 7      | 4.3%       | 35.45%           |

---

### Action Priorities

##### ⚠️ High-Risk Stores (3 total)
*Declining trend + Below-median performance*

- **Vadodara (Alkapuri) Br** — Gujarat: **Dec 18.0% → Jan 17.5%**
- **Panvel Br** — Thane: **Dec 18.0% → Jan 17.6%**
- **Ahmedabad (Maninagar) Br** — Gujarat: **Dec 19.0% → Jan 17.9%**

##### ✓ Momentum Builders
- **None identified** (Increasing trend + High confidence forecast)

---

### Export

✅ Detailed forecast exported to: **`hierarchical_forecast_jan2025.csv`**

## The Core Problem & Opportunity


### Core Problem
- **Untapped upside:** A 12 pp gap means lower performers operate at only ~55% of top-branch effectiveness
- **Systematic, not random:** Branch location explains ~32% of performance variance (p < 0.000001)
- **Gap is widening:** Performance spread increased ~20% over 5 months, favoring current leaders


### The Opportunity
- **Proven, repeatable success:** Pune & Delhi_NCR consistently achieve 26–28% attachment
- **High ROI lever:** Closing 50% of the gap (14% → 20%) implies 40%+ revenue uplift in lagging regions
- **Execution is feasible:** Limited set of high-risk stores and underperforming branches enables focused action


>  **Key takeaway:** *The issue is structural, measurable, and solvable—not a market limitation.*



## Strategic Imperatives (90-Day Plan)

What Must Be Done
- **Immediate (0–30 days):** Deep-dive Pune & Delhi_NCR playbooks
 (training, incentives, scripts, store ops, team management)


- **Near-term (30–60 days):** Pilot best practices in one underperforming branch with weekly tracking


- **Medium-term (60–90 days):** Scale validated interventions to remaining low performers with central support


- **Ongoing:** Monthly branch reviews with early-warning signals using forecast models


> **Objective:** *Reduce variance, replicate success, and prevent future divergence.*



## Statistical Validation: Why We Can Trust These Findings

- **Sample size:** 163 stores × 5 months = 815 data points analyzed, providing statistically robust conclusions
- **ANOVA results:** F-statistic = 14.54, p-value < 0.000001 confirms branch differences are real, not chance variation
- **Effect size:** Branch location explains 31.65% of all performance variance—the single largest controllable factor identified
- **Confidence:** 8 out of 8 cross-tier pairwise comparisons statistically significant (p < 0.05), confirming distinct performance clusters
