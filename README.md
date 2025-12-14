# 🤖 KPMG 1A: Measuring the Impact of AI on Energy Optimization and Sustainability

[![KPMG Logo](https://img.shields.io/badge/Project-KPMG%201A-blue)]()
[![Project Focus](https://img.shields.io/badge/Focus-Energy%20Optimization%20|%20Sustainability-green)]()
[![Methodology](https://img.shields.io/badge/Model-Random%20Forest%20|%20Gradient%20Boosting-red)]()
[![GitHub contributors](https://img.shields.io/github/contributors/amberhli/kpmg-1a)]()

## 💡 Project Mission and Overview

The project was driven by the finding that **30% of the energy used in commercial buildings is wasted**, according to the U.S. Environmental Protection Agency (EPA)[cite: 46].

Our mission was to reframe this loss as a design and operational opportunity[cite: 47]. We analyzed **NREL Large Office Buildings time-series data** to identify the energy end uses that most drive site energy reductions [cite: 47], and then translated those findings into actionable, AI-driven recommendations for KPMG’s new Manhattan workspace[cite: 48].

### 🎯 Goals and Business Impact

| Goal Area | Objective | Target Impact |
| :--- | :--- | :--- |
| **Sustainability** | Quantify carbon footprint reduction via energy-saving strategies[cite: 77]. | **15%+** energy savings [cite: 77] |
| **Energy Optimization** | Develop and test machine learning models to predict energy consumption[cite: 65, 67]. | High prediction accuracy (e.g., MAPE under 4%) [cite: 499, 561] |
| **Productivity** | Identify highest-impact end uses and forecast energy to support planning[cite: 72, 73]. | Actionable recommendations for KPMG's workspace [cite: 75, 76] |

---

## ⚙️ Methodology and Process

Our data science process followed four core stages[cite: 59]:

| Step | Description | Key Technologies |
| :--- | :--- | :--- |
| **01. Data Preparation** | Collected and cleaned datasets (NREL). Handled missing values, outliers, and aligned timestamps[cite: 58]. | Pandas, Time-series preprocessing |
| **02. Exploratory Data Analysis (EDA)** | Visualized energy and IT load patterns. Identified correlations and key predictive features[cite: 60]. | Jupyter Notebook, Matplotlib/Seaborn |
| **03. Model Development** | Trained and evaluated supervised regression models for time-series forecasting [cite: 65], including **Random Forest** and **Gradient Boosting**[cite: 482, 544]. | Scikit-learn, Random Forest, Gradient Boosting |
| **04. Optimization & Insights** | Tuned models for accuracy and generated actionable recommendations targeting over **15% energy savings**[cite: 69]. | Error Metrics (MAE/RMSE) [cite: 67], Feature Importance [cite: 484] |

### Data Source Selection: NREL Large Office Buildings

We initially considered three datasets: Harvard HouseZero, CU-BEMS, and NREL Large Office Buildings[cite: 85].

| Dataset | Reason for Exclusion | Reason for Selection |
| :--- | :--- | :--- |
| **Harvard HouseZero** | Too sensor-heavy, difficult to integrate[cite: 90, 94]. Missing aggregated energy metrics needed for forecasting[cite: 93, 97]. | |
| **CU-BEMS** | Climate mismatch (Bangkok vs. NYC)[cite: 100, 103]. Outdated (Pre-Pandemic) data that does not reflect hybrid work patterns[cite: 105, 106]. | |
| **NREL Large Office** | | **Chosen:** Aligned with U.S. building standards [cite: 114], high-resolution (15-minute intervals) data [cite: 115], and detailed end-use breakdowns (heating, cooling, lighting, plug loads, etc.)[cite: 117]. |

---

## 📊 Key Findings from Data Analysis

Our analysis identified clear, actionable patterns in the building's energy consumption:

### I. Energy Usage Patterns

| Pattern | Finding | Quantitative Difference |
| :--- | :--- | :--- |
| **Hourly Cycle** | Energy peaks around **8:00 AM** at 2.44M kWh[cite: 760, 323, 324]. Lowest consumption is around **12:00 AM** (midnight) at 1.61M kWh[cite: 760, 325, 326]. | Peak load is **~1.5x higher** than off-peak load[cite: 761, 327]. |
| **Work Schedule** | Business hours (9 AM–5 PM) average consumption is significantly higher than after-hours[cite: 759, 427, 429]. | Business hours use **+32.3% more** energy than after-hours/weekends[cite: 428, 449]. |
| **Weekly Cycle** | Energy consumption is consistent across weekdays[cite: 342, 343]. | Weekdays use **~29% more** energy than weekends[cite: 762, 364, 377]. |
| **Seasonal Cycle** | Consumption shows clear annual variation[cite: 764]. | Peak seasons are **Winter & Summer**, and the low season is **Spring**[cite: 410, 411]. |

### II. Consumption Breakdown

* **Dominant Source:** Electricity is the largest energy source, accounting for **68.3%** of the total average site energy[cite: 257]. 
* **Key Electricity End Uses** (Average kWh/hour)[cite: 259]:
    * **Electricity Interior Equipment:** 46.1% (629,323.73 kWh) [cite: 259]
    * **Electricity Cooling:** 19.3% (263,442.99 kWh) [cite: 259]
    * **Electricity Fans:** 13.8% (187,921.28 kWh) [cite: 259]
    * **Electricity Interior Lighting:** 12.7% (173,462.39 kWh) [cite: 259]

---

## 🧪 Model Performance and Feature Importance

To accurately forecast consumption, we engineered several features, including temporal features (hour, day, month, business hours flags) and time-series features like lagged consumption (1h, 24h, 168h) and rolling averages (24h, 168h)[cite: 455, 457, 458, 460].

### Model Comparison ($R^{2}$ Score) 

| Model Name | R-squared ($R^{2}$) | MAPE (Average Error) | Overall Accuracy (within $\pm 10\%$) | Why it Performed Well |
| :--- | :--- | :--- | :--- | :--- |
| **Baseline (Moving Avg.)** | 0.2767 [cite: 474] | 17.06% [cite: 475] | 32.5% [cite: 473] | Fails to capture complex and operational patterns[cite: 478, 480]. |
| **Random Forest (RF)** | **0.9408** [cite: 501] | **3.87%** [cite: 499] | **93.7%** [cite: 496, 514] | Handles non-linear relationships and is robust to outliers[cite: 483]. |
| **Gradient Boosting (GB)** | 0.9343 [cite: 563] | 4.02% [cite: 561] | 92.6% [cite: 557, 570] | Excels at learning from residual errors and is suited for complex patterns[cite: 545, 546]. |

**Conclusion:** The **Random Forest** model provided the highest performance, accurately predicting energy consumption within $\pm 10\%$ of the actual value 93.7% of the time[cite: 496, 514]. 

### Top Feature Importance (Random Forest)

The model confirmed that recent consumption and time-based features are the strongest predictors[cite: 484]:

1.  `energy_lag_1h` (Previous 1 hour consumption): **0.9493** [cite: 485]
2.  `hour` (Hour of the day) [cite: 485]
3.  `energy_lag_168h` (Previous 1 week consumption) [cite: 485]

---

## 💡 Actionable Recommendations for KPMG

Based on the finding that electricity, heating, and cooling are the main drivers of energy consumption[cite: 765, 801, 802], we recommend the following for the Manhattan workspace:

### 1. Optimize Electricity End Uses

Focus on interior equipment, lighting, and fans, which constitute the largest loads[cite: 801].

* Install **sensor lighting** (motion-activated) in conference rooms, restrooms, and corridors[cite: 801].
* Implement **smart controls** and **smart plugs** for interior equipment[cite: 801].

### 2. Optimize Heating and Cooling

Address the high impact of heating and cooling[cite: 802].

* Install **programmable thermostats** with time-of-use optimization features[cite: 802].
* Set HVAC systems to **'setback mode'** outside of core business hours (e.g., **7:00 AM – 7:00 PM** weekdays)[cite: 803].

---

## ➡️ Potential Next Steps

1.  **Model Upgrades:** Further tune the Random Forest, and explore **XGBoost/LightGBM** [cite: 805] for potential performance gains.
2.  **Run Scenarios:** Execute detailed "what-if" scenarios (e.g., reduce after-hours load by X%, shift peak load, adjust HVAC schedules) and estimate impact[cite: 806].
3.  **Build a Dashboard:** Develop a simple operational dashboard for hourly trends, peak alerts, weekday/weekend splits, and forecasted usage[cite: 807].

---

## 🤝 Contributors

* [Lucy Liu](https://github.com/lucyrliu) (Stony Brook University)
* [Anour Ibrahim](https://github.com/anouribrahim10) (City College of New York)
* [Anveetha Suresh](https://github.com/anveetha) (The University of Texas at Dallas)
* [Noble Adike] (Howard University)
*[Ramissa Khan] (Union College)
* [Amber Li](https://github.com/amberhli) (Columbia University)
