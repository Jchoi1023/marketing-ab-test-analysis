# Marketing A/B Test Analysis

## Overview
This project analyzes the effectiveness of ad campaigns versus public service announcements (PSA) on user conversion rates using a dataset of 588,101 users. The analysis includes EDA, A/B hypothesis testing, and business recommendations.

**Tools:** Python · statsmodels · pandas · Tableau

---

## Dataset
- **Source:** [Kaggle - A/B Testing Dataset](https://www.kaggle.com/datasets/amirmotefaker/ab-testing-dataset)
- **Size:** 588,101 users
- **Columns:** `user_id`, `test_group`, `converted`, `total_ads`, `most_ads_day`, `most_ads_hour`
- **Groups:** Ad (564,577 users) vs PSA (23,524 users)

---

## A/B Test Design
| | |
|---|---|
| **Control (A)** | PSA group |
| **Treatment (B)** | Ad group |
| **Metric** | Conversion rate (True/False) |
| **Test** | Two-proportion Z-test |
| **Significance level** | α = 0.05 |

**H₀:** There is no significant difference in conversion rates between the ad and PSA groups.  
**H₁:** The ad group has a significantly higher conversion rate than the PSA group.

---

## EDA

### 1. Overall Conversion Rate: Ad vs PSA
![Overall Conversion Rate: Ad vs PSA](image/Overall_Conversion_Rate_Ad_vs_PSA.png)

**Insight:** The ad group shows a higher overall conversion rate (2.55%) compared to the PSA group (1.79%), a difference of 0.76 percentage points.

---

### 2. Conversion Rate by Day of Week
![Conversion Rate by Day of Week](image/Conversion_Rate_by_Day_of_Week_Ad_vs_PSA.png)

**Insight:** Monday shows the highest conversion rate for both groups (Ad: 3.32%, PSA: 2.26%). Saturday consistently shows the lowest conversion rates. The ad group outperforms PSA on every day of the week.

---

### 3. Conversion Rate by Hour of Day
![Conversion Rate by Hour of Day](image/Conversion_Rate_by_Hour_of_Day_Ad_vs_PSA.png)

**Insight:** Conversion rates peak between 3 PM–4 PM (15:00–16:00) for both groups. The ad group maintains consistently higher conversion rates throughout the day. PSA conversion rates drop near zero during early morning hours (12 AM–6 AM) due to low sample size.

---

### 4. Conversion Rate by Ad Exposure
![Conversion Rate by Ad Exposure](image/Conversion_Rate_by_Ad_Exposure.png)

![Conversion Rate by Ad Exposure Table](image/Conversion_Rate_by_Ad_Exposure_Table.png)

**Insight:** Conversion rates increase sharply once users are exposed to 51+ ads. This suggests a frequency threshold effect — users need sufficient ad exposure before converting. The ad group shows a stronger lift from increased exposure compared to PSA.

---

## A/B Test Results

![Conversion Rate: Ad vs PSA](image/Conversion_Rate_Ad_vs_PSA.png)

```
H₀: No significant difference in conversion rates between ad and PSA groups
H₁: Ad group has a significantly higher conversion rate than PSA group

Z-statistic: 7.3701
P-value: 0.0000 (p < 0.001)

Conclusion: Reject H₀ — Ad group significantly outperforms PSA group
```

The ad campaign produces a statistically significant higher conversion rate than PSA (2.55% vs 1.79%, z=7.37, p<0.001).

---

## Business Recommendations

1. **Prioritize ad campaigns over PSA** — Ad exposure produces a statistically significant lift in conversion rate (p<0.001).
2. **Focus ad spend on Mondays** — Monday consistently shows the highest conversion rates for both groups (Ad: 3.32%).
3. **Schedule ads between 3 PM–4 PM** — Peak conversion hours across both groups.
4. **Increase ad frequency to 51+ exposures** — Conversion rates jump significantly after 51 ad exposures (1.89% → 11.63%), suggesting a minimum frequency threshold for effective campaigns.
