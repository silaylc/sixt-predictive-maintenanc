# sixt-predictive-maintenance
Data mining and business analytics workflows for SIXT SE, featuring predictive maintenance, driver profiling, and bundle sales optimization using KNIME.
# SIXT SE: Advanced Fleet Intelligence & Predictive Analytics Architecture

![Data Mining](https://img.shields.io/badge/Domain-Data_Mining_&_Analytics-0052CC?style=for-the-badge)
![KNIME](https://img.shields.io/badge/Platform-KNIME_Analytics-F3D30F?style=for-the-badge&logo=knime&logoColor=white)

## 📌 Project Overview
This project applies Knowledge Discovery in Databases (KDD) processes to solve three operational challenges for SIXT SE, a mobility service provider with a fleet of over 240,000 vehicles[cite: 1]. Developed entirely within the KNIME Analytics Platform, the project leverages data mining to optimize maintenance strategies, analyze driver behavior, and maximize sales revenue[cite: 1].

**Authors:** Satı Sıla Yolcu, Emre Hekimoğlu, Kaan Bilben[cite: 1].

## 🎯 Strategic Business Domains & Methodology
The analytical pipeline addresses three enterprise-level challenges using distinct datasets and machine learning algorithms:

### 1. Predictive Maintenance
* **Objective:** Predict potential vehicle failures to schedule maintenance before unexpected breakdowns occur[cite: 1].
* **Dataset:** AI4I 2020 Predictive Maintenance Dataset (approx. 24,000 samples)[cite: 1].
* **Methodology:** Implemented a Decision Tree classification algorithm to create an interpretable, rule-based model for maintenance engineers[cite: 1].
* **Data Processing:** Handled missing sensor readings using mean/median imputation and removed irrelevant identifier columns[cite: 1].

### 2. Driver Behavior Profiling
* **Objective:** Group drivers into categories to understand behavior, assess risk, and improve vehicle longevity[cite: 1].
* **Dataset:** Eco-driving behavior dataset (approx. 24,000 trip records)[cite: 1].
* **Methodology:** Applied the k-Means clustering algorithm to discover natural groupings, alongside a surrogate Decision Tree to make the numeric clusters human-readable[cite: 1].
* **Data Processing:** Normalized numeric features (e.g., fuel consumption, braking counts) to a [0,1] range to ensure algorithm stability[cite: 1].

### 3. Bundle Sales Optimization
* **Objective:** Discover which add-on items are frequently rented together to optimize product recommendations and packages[cite: 1].
* **Dataset:** Car Rental transactional dataset[cite: 1].
* **Methodology:** Utilized Association Rule mining (Apriori-style) to identify frequent itemsets and generate rules based on Support, Confidence, and Lift metrics[cite: 1].
* **Data Processing:** Converted individual rental line-items into a single basket format per transaction using a Column Aggregator node[cite: 1].

## 📊 Business Value Realization & Insights

### Predictive Maintenance Insights
* **Model Performance:** The Decision Tree model achieved an overall accuracy of 98.2% and a Cohen's Kappa of 0.68[cite: 1].
* **Business Action:** SIXT can transition from a preventive maintenance approach to a predictive one, focusing inspections only on vehicles flagged as problematic to minimize unexpected breakdown costs[cite: 1].
* **Deployment Recommendation:** In a production deployment, the decision threshold should be tuned to reduce false negatives (24 missed failures in the test set) to prevent critical system misses[cite: 1].

### Driver Profiling Insights
* **Model Performance:** The k-Means algorithm successfully segmented drivers into "Bad Driver", "Average", and "Good Driver" clusters[cite: 1]. The surrogate Decision Tree yielded an accuracy of 82.267% in classifying these generated categories[cite: 1].
* **Key Differentiator:** Fuel consumption was identified as the single strongest differentiator; drivers with fuel consumption > 8.835 L/100km are overwhelmingly (75.6%) classified as "Bad Driver"[cite: 1].
* **Business Action:** SIXT can use this high fuel consumption threshold to make decisions about risk-based insurance deposits, provide targeted eco-driving trainings, or reassign vehicles to extend fleet lifespan[cite: 1].

### Bundle Sales Insights
* **Model Performance:** The Association Rule Learner outputted zero qualifying rules at the default minimum support and confidence thresholds[cite: 1].
* **Business Action:** This indicates that the purchasing pattern of add-ons for SIXT is highly fragmented, with no single add-on mix being disproportionately popular[cite: 1].
* **Strategic Recommendation:** SIXT should reduce the minimum support threshold (e.g., from 10%-20% down to 1%-5%) and segment customers based on demographics (like age) before running the analysis again to uncover hidden moderately common bundles[cite: 1].

## 📂 System Execution Guidelines
To replicate the analytics pipeline locally:
1. Clone this repository.
2. Initialize KNIME Analytics Platform.
3. Navigate to `File -> Import KNIME Workflow...` and load the `.knwf` file.
4. Execute the KDD pipeline. Ensure that the configuration of the CSV Reader nodes is properly mapped to the local dataset paths.
