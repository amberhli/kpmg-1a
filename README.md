# 🤖 KPMG 1A: Measuring the Impact of AI on Energy Optimization and Sustainability

[![KPMG Logo](https://img.shields.io/badge/Project-KPMG%201A-blue)]()
[![Project Focus](https://img.shields.io/badge/Focus-Energy%20Optimization%20|%20Sustainability-green)]()
[![Methodology](https://img.shields.io/badge/Model-Random%20Forest%20|%20Gradient%20Boosting-red)]()
[![GitHub contributors](https://img.shields.io/github/contributors/amberhli/kpmg-1a)]()

## 💡 Project Mission and Overview

The project was driven by the finding that **30% of the energy used in commercial buildings is wasted**, according to the U.S. Environmental Protection Agency (EPA).

Our mission was to reframe this loss as a design and operational opportunity. We analyzed **NREL Large Office Buildings time-series data** to identify the energy end uses that most drive site energy reductions, and then translated those findings into actionable, AI-driven recommendations for KPMG’s new Manhattan workspace.

### 🎯 Goals and Business Impact

| Goal Area | Objective | Target Impact |
| :--- | :--- | :--- |
| **Sustainability** | Quantify carbon footprint reduction via energy-saving strategies. | **15%+** energy savings |
| **Energy Optimization** | Develop and test machine learning models to predict energy consumption. | High prediction accuracy (e.g., MAPE under 4%) |
| **Productivity** | Identify highest-impact end uses and forecast energy to support planning. | Actionable recommendations for KPMG's workspace |

---

## ⚙️ Methodology and Process

Our data science process followed four core stages:

| Step | Description | Key Technologies |
| :--- | :--- | :--- |
| **01. Data Preparation** | Collected and cleaned datasets (NREL). Handled missing values, outliers, and aligned timestamps. | Pandas, Time-series preprocessing |
| **02. Exploratory Data Analysis (EDA)** | Visualized energy and IT load patterns. Identified correlations and key predictive features. | Jupyter Notebook, Matplotlib/Seaborn |
| **03. Model Development** | Trained and evaluated supervised regression models for time-series forecasting, including **Random Forest** and **Gradient Boosting**. | Scikit-learn, Random Forest, Gradient Boosting |
| **04. Optimization & Insights** | Tuned models for accuracy and generated actionable recommendations targeting over **15% energy savings**. | Error Metrics (MAE/RMSE), Feature Importance |

### Data Source Selection: NREL Large Office Buildings

We initially considered three datasets: Harvard HouseZero, CU-BEMS, and NREL Large Office Buildings.

| Dataset | Reason for Exclusion | Reason for Selection |
| :--- | :--- | :--- |
| **Harvard HouseZero** | Too sensor-heavy, difficult to integrate. Missing aggregated energy metrics needed for forecasting. | |
| **CU-BEMS** | Climate mismatch (Bangkok vs. NYC). Outdated (Pre-Pandemic) data that does not reflect hybrid work patterns. | |
| **NREL Large Office** | | **Chosen:** Aligned with U.S. building standards, high-resolution (15-minute intervals) data, and detailed end-use breakdowns (heating, cooling, lighting, plug loads, etc.). |

---

## 📊 Key Findings from Data Analysis

Our analysis identified clear, actionable patterns in the building's energy consumption:

### I. Energy Usage Patterns

| Pattern | Finding | Quantitative Difference |
| :--- | :--- | :--- |
| **Hourly Cycle** | Energy peaks around **8:00 AM** at 2.44M kWh. Lowest consumption is around **12:00 AM** (midnight) at 1.61M kWh. | Peak load is **~1.5x higher** than off-peak load. |
| **Work Schedule** | Business hours (9 AM–5 PM) average consumption is significantly higher than after-hours. | Business hours use **+32.3% more** energy than after-hours/weekends. |
| **Weekly Cycle** | Energy consumption is consistent across weekdays. | Weekdays use **~29% more** energy than weekends. |
| **Seasonal Cycle** | Consumption shows clear annual variation. | Peak seasons are **Winter & Summer**, and the low season is **Spring**. |

### II. Consumption Breakdown

* **Dominant Source:** Electricity is the largest energy source, accounting for **68.3%** of the total average site energy. 
* **Key Electricity End Uses** (Average kWh/hour):
    * **Electricity Interior Equipment:** 46.1% (629,323.73 kWh)
    * **Electricity Cooling:** 19.3% (263,442.99 kWh)
    * **Electricity Fans:** 13.8% (187,921.28 kWh)
    * **Electricity Interior Lighting:** 12.7% (173,462.39 kWh)

---

## 🧪 Model Performance and Feature Importance

To accurately forecast consumption, we engineered several features, including temporal features (hour, day, month, business hours flags) and time-series features like lagged consumption (1h, 24h, 168h) and rolling averages (24h, 168h).

### Model Comparison ($R^{2}$ Score) 

| Model Name | R-squared ($R^{2}$) | MAPE (Average Error) | Overall Accuracy (within $\pm 10\%$) | Why it Performed Well |
| :--- | :--- | :--- | :--- | :--- |
| **Baseline (Moving Avg.)** | 0.2767 | 17.06% | 32.5% | Fails to capture complex and operational patterns. |
| **Random Forest (RF)** | **0.9408** | **3.87%** | **93.7%** | Handles non-linear relationships and is robust to outliers. |
| **Gradient Boosting (GB)** | 0.9343 | 4.02% | 92.6% | Excels at learning from residual errors and is suited for complex patterns. |

**Conclusion:** The **Random Forest** model provided the highest performance, accurately predicting energy consumption within $\pm 10\%$ of the actual value 93.7% of the time. 

### Top Feature Importance (Random Forest)

The model confirmed that recent consumption and time-based features are the strongest predictors:

1.  `energy_lag_1h` (Previous 1 hour consumption): **0.9493**
2.  `hour` (Hour of the day)
3.  `energy_lag_168h` (Previous 1 week consumption)

---

## 💡 Actionable Recommendations for KPMG

Based on the finding that electricity, heating, and cooling are the main drivers of energy consumption, we recommend the following for the Manhattan workspace:

### 1. Optimize Electricity End Uses

Focus on interior equipment, lighting, and fans, which constitute the largest loads.

* Install **sensor lighting** (motion-activated) in conference rooms, restrooms, and corridors.
* Implement **smart controls** and **smart plugs** for interior equipment.

### 2. Optimize Heating and Cooling

Address the high impact of heating and cooling.

* Install **programmable thermostats** with time-of-use optimization features.
* Set HVAC systems to **'setback mode'** outside of core business hours (e.g., **7:00 AM – 7:00 PM** weekdays).

---

## ➡️ Potential Next Steps

1.  **Model Upgrades:** Further tune the Random Forest, and explore **XGBoost/LightGBM** for potential performance gains.
2.  **Run Scenarios:** Execute detailed "what-if" scenarios (e.g., reduce after-hours plug load by X%, shift peak load by Y hours) and estimate impact.
3.  **Build a Dashboard:** Develop a simple operational dashboard for hourly trends, peak alerts, weekday/weekend splits, and forecasted usage.

---

## 🤝 Contributors

* [Lucy Liu](https://github.com/lucyrliu) (Stony Brook University)
* [Anour Ibrahim](https://github.com/anouribrahim10) (City College of New York)
* [Anveetha Suresh](https://github.com/anveetha) (The University of Texas at Dallas)
* Noble Adike (Howard University)
* Ramissa Khan (Union College)
* [Amber Li](https://github.com/amberhli) (Columbia University)
