# 🏎️ Predicting F1 Pit Stops (Kaggle Playground Series)

[![Kaggle Competition](https://shields.io)](https://www.kaggle.com/competitions/playground-series-s6e5) 
[![Python](https://shields.io)](https://python.org)
[![Metric](https://shields.io)](https://kaggle.com)

## 📌 Project Overview
In Formula 1, pit stop timing is a high-stakes strategic decision. This project participates in the Kaggle Playground Series to predict the likelihood of a driver making a pit stop on the very next lap (`PitNextLap`) based on telemetry and race context variables. 

By framing this as a **Binary Classification** problem, the pipeline handles tabular race data to assist real-time race engineering simulations.

## 🎯 Key Objectives
* **Feature Engineering:** Extract meaningful indicators from lap-by-lap data, tire compounds, tire life, degradation metrics, and relative track position change.
* **Predictive Modeling:** Build and optimize gradient-boosted decision trees and ensemble methods to evaluate the probability of pit events.
* **Optimization:** Maximize the **ROC-AUC score** to ensure clear separation between active racing laps and upcoming pit entries.

## 🛠️ Tech Stack & Libraries
* **Language:** Python
* **Data Engineering:** Pandas, NumPy
* **Visualization:** Matplotlib
* **Machine Learning:** Scikit-Learn, LightGBM, XGBoost, CatBoost

## 🤖 Models & Validation Results
We implemented a robust Stratified K-Fold cross-validation strategy to mirror race-to-race variability. Here is the breakdown of the model performance:


| Machine Learning Model | Validation ROC-AUC | Key Parameters Tuned |
| :--- | :---: | :--- |
| **LightGBM Classifier** | `[Ví dụ: 0.9420]` | `learning_rate`, `num_leaves`, `reg_alpha` |
| **XGBoost Classifier** | `[Ví dụ: 0.9455]` | `max_depth`, `subsample`, `colsample_bytree` |
| **CatBoost Classifier** | `[Ví dụ: 0.9470]` | `depth`, `l2_leaf_reg`, `iterations` |
| **Ensemble (Voting/Stacking)** | **`[0.9510]`** | Combined predictions from top models |

*👉 **Current Standings:** The ensemble pipeline achieves a Cross-Validation ROC-AUC of **[Điền điểm CV vào đây]**, effectively capturing strategic triggers like tire life thresholds and race progress percentages.*

## 💡 Top Strategic Insights
1. **Tire Degradation Curve:** The interaction between tire compound and tire life remains the strongest signal for an imminent pit entry.
2. **Race Progress Metrics:** Target behaviors for `PitNextLap` change significantly depending on whether the race is in its early window or approaching the final stint sequences.
3. **Track & Traffic Context:** Position changes and gap metrics reveal that drivers in dirty air (stuck behind opponents) often trigger earlier undercuts.

## 🚀 How to Run the Project
1. Clone this repository:
   ```bash
   git clone https://github.com
   ```
2. Setup the environment dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn lightgbm xgboost catboost
   ```
3. Run the complete training pipeline inside the Jupyter Notebook:
   ```bash
   jupyter notebook "Predicting F1 Pit Stops.ipynb"
   ```
