## Dataset Deccriptives
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Dec</th>
      <th>Nov</th>
      <th>Oct</th>
      <th>Sep</th>
      <th>Aug</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>163.000000</td>
      <td>163.000000</td>
      <td>163.000000</td>
      <td>163.000000</td>
      <td>163.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.217239</td>
      <td>0.217117</td>
      <td>0.170920</td>
      <td>0.167301</td>
      <td>0.128589</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.173270</td>
      <td>0.131246</td>
      <td>0.116125</td>
      <td>0.134518</td>
      <td>0.116640</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.095000</td>
      <td>0.130000</td>
      <td>0.100000</td>
      <td>0.080000</td>
      <td>0.035000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.200000</td>
      <td>0.200000</td>
      <td>0.160000</td>
      <td>0.150000</td>
      <td>0.110000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.300000</td>
      <td>0.295000</td>
      <td>0.240000</td>
      <td>0.245000</td>
      <td>0.190000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.000000</td>
      <td>0.700000</td>
      <td>0.710000</td>
      <td>0.800000</td>
      <td>0.600000</td>
    </tr>
  </tbody>
</table>
</div>


## First Thoughts
- Dataset scope: 163 stores across 6 states, tracking insurance purchase rates over 5 months
- Overall trend: Increasing percentage of customers buying insurance with devices
- Recent slowdown: Growth stagnating in last 2 months, likely due to fewer transactions (common in recent dataset entries) and slightly higher standard deviation
- Outliers present: Maximum values significantly exceed the 3rd quartile
- Data quality concern: Some entries show 80-100% insurance purchase rates, but these may be misleading due to very low customer counts


## Branch Level Performance Benchmarking

<img src="./images/Branch Level Performance Benchmarking.png">
=== Summary Statistics ===
Overall Average: 0.18%

Branch Performance:
Branch
Pune         0.276500
Delhi_Ncr    0.243682
Mumbai       0.173474
Thane        0.148600
Gujarat      0.134583
Telangana    0.118350

Branches Above Average: 2
Branches Below Average: 4


## Understanding Monthly Branch level performances

<img src="./images/Understanding Monthly Branch level performances.png">

=== Branch Rankings by Month ===
           Aug  Sep  Oct  Nov  Dec
Branch                            
Delhi_Ncr    2    2    2    2    2
Gujarat      5    5    5    6    3
Mumbai       3    3    3    3    4
Pune         1    1    1    1    1
Telangana    6    6    6    4    5
Thane        4    4    4    5    6

=== Biggest Ranking Changes (Aug to Dec) ===

Biggest Improvements (moved up):
  Gujarat: moved up 2 positions
  Telangana: moved up 1 positions

Biggest Declines (moved down):
  Mumbai: moved down 1 positions
  Thane: moved down 2 positions


## Monthly Outliers Analysis

<img src="./images/Monthly Outliers Analysis.png">

=== Outlier Analysis by Branch ===

Note: Each Store is analysed 5 times, one for each month.

Branches Ranked by Number of Outliers:
================================================================================
Pune            | Outliers:   8 ( 10.0%) | IQR:   0.15 | Range: [  0.00,   0.71]
Delhi_Ncr       | Outliers:   4 (  1.8%) | IQR:   0.18 | Range: [  0.00,   1.00]
Telangana       | Outliers:   4 (  2.0%) | IQR:   0.13 | Range: [  0.00,   0.83]
Gujarat         | Outliers:   1 (  0.8%) | IQR:   0.12 | Range: [  0.00,   0.46]
Mumbai          | Outliers:   1 (  1.1%) | IQR:   0.14 | Range: [  0.00,   0.60]
Thane           | Outliers:   0 (  0.0%) | IQR:   0.16 | Range: [  0.00,   0.44]

=== Summary ===
Branch with most outliers: Pune (8 outliers)
Branch with least outliers: Thane (0 outliers)

Average outliers per branch: 3.0
Total outliers across all branches: 18


## Branch Level Outlier Analysis with ANOVA and Tukey HSD tests

<img src="./images/Branch Level Outlier Analysis with ANOVA and Tukey HSD tests.png">

=== STORE-LEVEL Outlier Analysis by Branch ===

Note: Each store is analyzed once using its 5-month average

Branches Ranked by Number of Outlier STORES:
==========================================================================================
Branch          Total Stores  Outlier Stores  Outlier %    IQR      Range
------------------------------------------------------------------------------------------
Telangana       40            2               5.0          5.90     [0.00, 29.00]
Delhi_Ncr       44            1               2.3          14.95    [6.40, 62.20]
Pune            16            1               6.2          10.30    [10.60, 58.60]
Gujarat         24            1               4.2          5.70     [0.00, 22.40]
Thane           20            1               5.0          9.00     [0.00, 36.20]
Mumbai          19            0               0.0          10.50    [0.00, 33.60]

==========================================================================================
ANOVA ANALYSIS (Store-Level)
==========================================================================================
F-statistic: 14.5393
P-value: 0.000000

Effect Size (η²): 0.3165
Branch explains 31.65% of variance

Pairwise Significant Differences (p < 0.05):
• Delhi_Ncr vs Gujarat (p=0.0000, diff=10.91%)
• Delhi_Ncr vs Thane (p=0.0011, diff=9.51%)
• Delhi_Ncr vs Telangana (p=0.0000, diff=12.53%)
• Delhi_Ncr vs Mumbai (p=0.0429, diff=7.02%)
• Pune vs Gujarat (p=0.0000, diff=14.19%)
• Pune vs Thane (p=0.0003, diff=12.79%)
• Pune vs Telangana (p=0.0000, diff=15.82%)
• Pune vs Mumbai (p=0.0080, diff=10.30%)

==========================================================================================


## Branch level Statistics

<img src="./images/Branch level Statistics.png">

================================================================================
PERFORMANCE CLUSTER ANALYSIS
================================================================================

High Performers (2): Pune, Delhi_Ncr
Lower Performers (4): Mumbai, Thane, Gujarat, Telangana

--- HIGH PERFORMERS ---
Pune            | Mean: 27.65% | Std: 0.1605
Delhi_Ncr       | Mean: 24.37% | Std: 0.1507

--- LOWER PERFORMERS ---
Mumbai          | Mean: 17.35% | Std: 0.1218
Thane           | Mean: 14.86% | Std: 0.1123
Gujarat         | Mean: 13.46% | Std: 0.0894
Telangana       | Mean: 11.83% | Std: 0.1109

================================================================================
High Performers Avg:  26.01%
Lower Performers Avg: 14.38%
Performance Gap:     11.63%
Relative Difference: 80.93%
================================================================================


## Classifying Stores Based on Performance

<img src="./images/Classifying Stores Based on Performance.png">

================================================================================
STORE PERFORMANCE CLASSIFICATION REPORT
================================================================================

--- CLASSIFICATION CRITERIA ---
Lower Fence (Q1 - 1.5×IQR):     -0.0600%
Q1 (25th Percentile):           0.1170%
Median (50th Percentile):       0.1640%
Q3 (75th Percentile):           0.2350%
Upper Fence (Q3 + 1.5×IQR):     0.4120%
IQR (Interquartile Range):      0.1180%

--- OVERALL CLASSIFICATION SUMMARY ---
Average Performer 
(Above Median)   | Count:  43 ( 26.4%) | Avg Rate: 0.1945%
Average Performer 
(Below Median)   | Count:  38 ( 23.3%) | Avg Rate: 0.1346%
High Performer                      | Count:  38 ( 23.3%) | Avg Rate: 0.3017%
Low Performer                       | Count:  41 ( 25.2%) | Avg Rate: 0.0686%
Outlier (High)                      | Count:   3 (  1.8%) | Avg Rate: 0.5407%

--- CLASSIFICATION BY BRANCH ---
================================================================================

Delhi_Ncr:
  Average Performer 
(Above Median)   |  11 stores ( 25.0%)
  Average Performer 
(Below Median)   |   5 stores ( 11.4%)
  High Performer                      |  22 stores ( 50.0%)
  Low Performer                       |   5 stores ( 11.4%)
  Outlier (High)                      |   1 stores (  2.3%)

Gujarat:
  Average Performer 
(Above Median)   |   8 stores ( 33.3%)
  Average Performer 
(Below Median)   |  10 stores ( 41.7%)
  Low Performer                       |   6 stores ( 25.0%)

Mumbai:
  Average Performer 
(Above Median)   |   5 stores ( 26.3%)
  Average Performer 
(Below Median)   |   5 stores ( 26.3%)
  High Performer                      |   4 stores ( 21.1%)
  Low Performer                       |   5 stores ( 26.3%)

Pune:
  Average Performer 
(Above Median)   |   5 stores ( 31.2%)
  High Performer                      |   8 stores ( 50.0%)
  Low Performer                       |   1 stores (  6.2%)
  Outlier (High)                      |   2 stores ( 12.5%)

Telangana:
  Average Performer 
(Above Median)   |   6 stores ( 15.0%)
  Average Performer 
(Below Median)   |  14 stores ( 35.0%)
  High Performer                      |   2 stores (  5.0%)
  Low Performer                       |  18 stores ( 45.0%)

Thane:
  Average Performer 
(Above Median)   |   8 stores ( 40.0%)
  Average Performer 
(Below Median)   |   4 stores ( 20.0%)
  High Performer                      |   2 stores ( 10.0%)
  Low Performer                       |   6 stores ( 30.0%)

--- ACTIONABLE INSIGHTS ---
================================================================================

✓ 3 HIGH-PERFORMING OUTLIERS identified:
  → Study their best practices for replication
    • Delhi(Hauz Khas) (Delhi_Ncr): 0.622%
    • Pune(Kondhawa) (Pune): 0.414%
    • Pune(Hadapsar) (Pune): 0.586%

✗ 41 STORES NEED IMMEDIATE ATTENTION:
  → Require intervention, training, or support
    • MAHIM(VS Next) (Mumbai): 0.000%
    • Ts(Jubilee Hills) (Telangana): 0.080%
    • Ts(Warangal) (Telangana): 0.040%
    • Nallasopara Br (Thane): 0.086%
    • Currey Road (Thane): 0.000%
    • Chembur Br (Mumbai): 0.114%
    • Ts(Attapur) (Telangana): 0.116%
    • Gandhinagar(Sargasan) (Gujarat): 0.052%
    • Ahmedabad(Chandkheda Rd) Br (Gujarat): 0.106%
    • Ts(Nagole) (Telangana): 0.116%

--- BRANCH-LEVEL INSIGHTS ---

Delhi_Ncr:
  High Performers: 23/44 (52.3%)
  Low Performers:  5/44 (11.4%)
  → Strong branch overall

Gujarat:
  High Performers: 0/24 (0.0%)
  Low Performers:  6/24 (25.0%)

Mumbai:
  High Performers: 4/19 (21.1%)
  Low Performers:  5/19 (26.3%)

Pune:
  High Performers: 10/16 (62.5%)
  Low Performers:  1/16 (6.2%)
  → Strong branch overall

Telangana:
  High Performers: 2/40 (5.0%)
  Low Performers:  18/40 (45.0%)

Thane:
  High Performers: 2/20 (10.0%)
  Low Performers:  6/20 (30.0%)

--- EXPORTING RESULTS ---
✓ Classification results exported to: store_classification_results.csv
================================================================================

## Forecasts for the month of January

<img src="./images/Forecasts for the month of January.png">

====================================================================================================
HIERARCHICAL FORECAST MODEL - JANUARY 2025
====================================================================================================

Model: Store Trend (60%) + Branch Trend (40%) with Adaptive Weighting
Branch information leveraged to improve forecast accuracy

----------------------------------------------------------------------------------------------------
Branch       Dec      Jan(F)   Change   R²(S)   R²(B)   R²(Avg)  #High 
----------------------------------------------------------------------------------------------------
Delhi_Ncr      28.3%   32.5% ↑  4.16%  0.408  0.935   0.672   0/44
Gujarat        19.1%   20.7% ↑  1.61%  0.342  0.747   0.544   0/24
Mumbai         18.3%   24.6% ↑  6.29%  0.354  0.508   0.431   0/19
Pune           28.8%   38.0% ↑  9.19%  0.419  0.607   0.513   0/16
Telangana      18.1%   23.3% ↑  5.18%  0.433  0.840   0.636   0/40
Thane          15.2%   18.0% ↑  2.78%  0.377  0.236   0.307   0/20

====================================================================================================
FORECAST CONFIDENCE SUMMARY
====================================================================================================
Low            : 160 stores ( 98.2%) | Avg Combined R²: 0.555
Medium         :   3 stores (  1.8%) | Avg Combined R²: 0.745

====================================================================================================
TREND DIRECTION SUMMARY
====================================================================================================
Increasing  : 118 stores ( 72.4%) | Avg Jan Forecast: 24.06%
Decreasing  :  38 stores ( 23.3%) | Avg Jan Forecast: 31.71%
Stable      :   7 stores (  4.3%) | Avg Jan Forecast: 35.45%

====================================================================================================
ACTION PRIORITIES
====================================================================================================

⚠️  HIGH-RISK STORES (3 total):
    (Declining trend + Below-median performance)
    • Vadodara(Alkapuri) Br     (Gujarat     ): Dec  18.0% → Jan  17.5%
    • Panvel Br                 (Thane       ): Dec  18.0% → Jan  17.6%
    • Ahmedabad(Maninagar) Br   (Gujarat     ): Dec  19.0% → Jan  17.9%

✓  MOMENTUM BUILDERS (0 total):
    (Increasing trend + High confidence forecast)

✓ Detailed forecast exported to: hierarchical_forecast_jan2025.csv
====================================================================================================