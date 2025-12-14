# 🤖 KPMG 1A: Measuring the Impact of AI on Energy Optimization and Sustainability

[![KPMG Logo](https://img.shields.io/badge/Project-KPMG%201A-blue)](https://github.com/amberhli/kpmg-1a)
[![Project Focus](https://img.shields.io/badge/Focus-Energy%20Optimization%20|%20Sustainability-green)](https://github.com/amberhli/kpmg-1a)
[![Methodology](https://img.shields.io/badge/Model-Random%20Forest%20|%20Gradient%20Boosting-red)](https://github.com/amberhli/kpmg-1a)
[![GitHub contributors](https://img.shields.io/github/contributors/amberhli/kpmg-1a)](https://github.com/amberhli/kpmg-1a/graphs/contributors)

## 💡 Project Mission and Overview

[cite_start]The project was driven by the finding that **30% of the energy used in commercial buildings is wasted**, according to the U.S. Environmental Protection Agency (EPA)[cite: 46].

[cite_start]Our mission was to reframe this loss as a design and operational opportunity[cite: 47]. [cite_start]We analyzed **NREL Large Office Buildings time-series data** [cite: 47, 50] [cite_start]to identify the energy end uses that most drive site energy reductions, and then translated those findings into actionable, AI-driven recommendations for KPMG’s new Manhattan workspace[cite: 48, 75, 76].

### 🎯 Goals and Business Impact

| Goal Area | Objective | Target Impact |
| :--- | :--- | :--- |
| **Sustainability** | Quantify carbon footprint reduction via energy-saving strategies. | [cite_start]**15%+** energy savings [cite: 77] |
| **Energy Optimization** | Develop and test machine learning models to predict energy consumption. | [cite_start]High prediction accuracy (e.g., MAPE under 4%) [cite: 499, 561] |
| **Productivity** | Identify highest-impact end uses and forecast energy to support planning. | [cite_start]Actionable recommendations for KPMG's workspace [cite: 75, 76] |

---

## ⚙️ Methodology and Process

Our data science process followed four core stages:

| Step | Description | Key Technologies |
| :--- | :--- | :--- |
| **01. Data Preparation** | Collected and cleaned NREL Large Office Building datasets. [cite_start]Handled missing values, outliers, and aligned timestamps[cite: 58]. | Pandas, Time-series preprocessing |
| **02. Exploratory Data Analysis (EDA)** | Visualized energy and IT load patterns. [cite_start]Identified correlations, seasonal, weekly, and hourly features to use for prediction[cite: 60]. | Jupyter Notebook, Matplotlib/Seaborn |
| **03. Model Development** | [cite_start]Trained and evaluated supervised regression models for time-series forecasting, including **Random Forest** and **Gradient Boosting**[cite: 65, 482, 544]. | Scikit-learn, Random Forest, Gradient Boosting |
| **04. Optimization & Insights** | [cite_start]Tuned models for accuracy (MAE/RMSE) [cite: 67] [cite_start]and generated recommendations targeting **15%+ energy savings**[cite: 69]. | Error Metrics, Feature Importance |

### Data Source Selection: NREL Large Office Buildings

[cite_start]We initially considered three datasets [cite: 85][cite_start]: Harvard HouseZero [cite: 84][cite_start], CU-BEMS [cite: 87][cite_start], and NREL Large Office Buildings[cite: 86].

| Dataset | Reason for Exclusion | Reason for Selection |
| :--- | :--- | :--- |
| **Harvard HouseZero** | [cite_start]Too sensor-heavy, difficult to integrate, and missing aggregated energy metrics needed for forecasting[cite: 90, 93, 95, 96]. | |
| **CU-BEMS** | [cite_start]Climate mismatch (Bangkok vs. NYC) and outdated (pre-pandemic) data that does not reflect modern hybrid work patterns[cite: 100, 103, 105, 106]. | |
| **NREL Large Office** | | [cite_start]**Chosen:** Aligned with U.S. building standards (ASHRAE), high-resolution (15-minute intervals) data, and detailed end-use breakdowns (heating, cooling, lighting, etc.)[cite: 114, 115, 117]. |

---

## 📊 Key Findings from Data Analysis

Our analysis identified clear, actionable patterns in the building's energy consumption:

### I. Energy Usage Patterns

| Pattern | Finding | Quantitative Difference |
| :--- | :--- | :--- |
| **Hourly Cycle** | [cite_start]Energy peaks around **8:00 AM** at 2.44M kWh[cite: 760, 286]. [cite_start]Lowest consumption is around **12:00 AM** (midnight) at 1.61M kWh[cite: 760, 272]. | [cite_start]Peak load is **~1.5x higher** than off-peak load[cite: 761]. |
| **Work Schedule** | [cite_start]Business hours (9 AM–5 PM) average consumption is significantly higher than after-hours[cite: 759, 328, 330]. | [cite_start]Business hours use **+32.3% more** energy than after-hours/weekends[cite: 427, 428, 449]. |
| **Weekly Cycle** | [cite_start]Energy consumption is consistent across weekdays[cite: 342]. | [cite_start]Weekdays use **~29% more** energy than weekends[cite: 762, 377]. |
| **Seasonal Cycle** | Consumption shows clear annual variation. | [cite_start]Peak seasons are **Winter** and **Summer**, and the low season is **Spring**[cite: 764, 410, 411]. |

### II. Consumption Breakdown

* [cite_start]**Dominant Source:** Electricity is the largest energy source, accounting for **68.3%** of the total average site energy[cite: 257].
* [cite_start]**Key Electricity End Uses** (Average kWh/hour)[cite: 259]:
    1.  **Electricity Interior Equipment:** 46.1% (629,323.73 kWh)
    2.  **Electricity Cooling:** 19.3% (263,442.99 kWh)
    3.  **Electricity Fans:** 13.8% (187,921.28 kWh)
    4.  **Electricity Interior Lighting:** 12.7% (173,462.39 kWh)

---

## 🧪 Model Performance and Feature Importance

[cite_start]To accurately forecast consumption, we engineered several features, including temporal features (hour, month, business hours flag) and lag/rolling average features (1h, 24h, 168h consumption)[cite: 455, 457, 458, 460].

### Model Comparison ($R^{2}$ Score) 
| Model Name | R-squared ($R^{2}$) | MAPE (Average Error) | Overall Accuracy (within $\pm 10\%$) | Why it Performed Well |
| :--- | :--- | :--- | :--- | :--- |
| **Baseline (Moving Avg.)** | [cite_start]0.2767 [cite: 474, 621] | [cite_start]17.06% [cite: 475] | [cite_start]32.5% [cite: 473] | [cite_start]Fails to capture complex, weather-driven, and operational patterns[cite: 478, 479, 480]. |
| **Random Forest (RF)** | [cite_start]**0.9408** [cite: 501, 617] | [cite_start]**3.87%** [cite: 499] | [cite_start]**93.7%** [cite: 496, 514] | [cite_start]Handles non-linear relationships and is robust to outliers[cite: 482]. |
| **Gradient Boosting (GB)** | [cite_start]0.9343 [cite: 563, 619] | [cite_start]4.02% [cite: 561] | [cite_start]92.6% [cite: 557, 570] | [cite_start]Achieves high precision on complex patterns, ideal for subtle daily/seasonal variations[cite: 545]. |

[cite_start]**Conclusion:** The **Random Forest** model provided the highest performance, accurately predicting energy consumption within $\pm 10\%$ of the actual value 93.7% of the time[cite: 496, 514].

### Top Feature Importance (Random Forest)

[cite_start]The model confirmed that recent consumption and time-based features are the strongest predictors[cite: 484, 485]:

1.  `energy_lag_1h` (Previous 1 hour consumption): **0.9493**
2.  `hour` (Hour of the day)
3.  `energy_lag_168h` (Previous 1 week consumption)
4.  `energy_rolling_24h` (24-hour moving average)
5.  `energy_lag_24h` (Previous 24 hour consumption)

---

##  actionable Recommendations for KPMG

[cite_start]Based on the finding that electricity, heating, and cooling are the main drivers of energy consumption and prediction accuracy [cite: 765, 147, 151][cite_start], we recommend the following for the Manhattan workspace[cite: 800]:

### 1. Optimize Electricity End Uses

[cite_start]Focus on interior equipment, lighting, and fans, which constitute the largest loads[cite: 259].

* Install **sensor lighting** (motion-activated) in conference rooms, restrooms, and corridors.
* [cite_start]Implement **smart controls** and **smart plugs** for interior equipment[cite: 801].

### 2. Optimize Heating and Cooling

[cite_start]Address the high impact of heating and cooling[cite: 802].

* Install **programmable thermostats** with time-of-use optimization features.
* [cite_start]Set HVAC systems to **'setback mode'** outside of core business hours (e.g., **7:00 AM – 7:00 PM** weekdays)[cite: 803].

---

## ➡️ Potential Next Steps

1.  [cite_start]**Model Upgrades:** Further tune the Random Forest model, and explore other tree-based ensembles like XGBoost/LightGBM for potential performance gains[cite: 805].
2.  [cite_start]**Run Scenarios:** Execute detailed "what-if" scenarios (e.g., reducing after-hours plug load by X%, shifting peak load by Y hours) to estimate exact cost and carbon reduction impact[cite: 806].
3.  [cite_start]**Build a Dashboard:** Develop a simple operational dashboard for real-time tracking, including hourly trends, peak demand alerts, and forecasted usage[cite: 807].

---

## 🤝 Contributors

* [cite_start][Lucy Liu](https://github.com/lucyrliu) (Stony Brook University) [cite: 20, 21]
* [cite_start][Anour Ibrahim](https://github.com/anouribrahim10) (City College of New York) [cite: 23]
* [cite_start][Anveetha Suresh](https://github.com/anveetha) (The University of Texas at Dallas) [cite: 24]
* [cite_start]Noble Adike (Howard University) [cite: 25]
* [cite_start]Ramissa Khan (Union College) [cite: 26]
* [cite_start][Amber Li](https://github.com/amberhli) (Columbia University) [cite: 27]
