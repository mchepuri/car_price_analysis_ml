# Used Car Price Analysis & Modeling

## 1. Business Understanding
A used car marketplace wants to understand the **key drivers of vehicle price** and build a pricing model.  
This will help sellers set competitive prices and buyers identify fair market value.  

**Business Goals:**
- Identify which factors (e.g., year, mileage, condition, brand) most influence car price.  
- Detect unusual listings (fraud, mispricing, or data errors).  
- Support decisions such as **market segmentation** by vehicle type, region, or fuel.  

---

## 2. Data Problem Definition
The business problem is reframed into a **data mining task** under CRISP-DM as follows:

- **Supervised Learning / Regression Task:**  
  Predict car prices (`price`) based on vehicle attributes.  

- **Feature Importance:**  
  Identify influential features (e.g., `year`, `odometer`, `manufacturer`, `condition`).  

- **Outlier Detection:**  
  Detect abnormal price listings using statistical methods (IQR).  

- **Segmentation / Clustering (optional):**  
  Segment the market by vehicle type, manufacturer, or fuel for deeper insights.  

---

## 3. Dataset Information
**Total Columns: 18**

| Column         | Description                                      |
|----------------|--------------------------------------------------|
| id             | Unique identifier for listing                    |
| region         | Region of the listing                            |
| price          | Target variable (car price)                      |
| year           | Manufacturing year                               |
| manufacturer   | Car brand (e.g., Ford, Toyota)                   |
| model          | Specific model name                              |
| condition      | Vehicle condition (e.g., new, excellent, fair)   |
| cylinders      | Number of engine cylinders                       |
| fuel           | Fuel type (e.g., gas, diesel, electric)          |
| odometer       | Mileage of the vehicle                           |
| title_status   | Ownership status (e.g., clean, salvage)          |
| transmission   | Transmission type (automatic, manual, other)     |
| VIN            | Vehicle Identification Number                    |
| drive          | Drivetrain (e.g., 4wd, fwd, rwd)                 |
| type           | Vehicle type (e.g., sedan, SUV, truck)           |
| paint_color    | Exterior color                                   |
| state          | State where car is listed                        |

---

## 4. Data Preparation & Quality
- **Missing Values:** Handle missing entries in categorical variables.  
- **Inconsistencies:** Standardize category values (e.g., fuel types, condition labels).  
- **Outlier Detection:**  
  - Apply **Interquartile Range (IQR)** to remove unrealistic price and odometer values.  
- **Feature Encoding:**  
  - Convert categorical variables into numeric representations (One-Hot Encoding).  
- **Scaling:**  
  - Normalize continuous features (`year`, `odometer`) for modeling.  

---

## 5. Exploratory Data Analysis (EDA)
**Goals:**
- Explore relationships between independent variables and price.  
- Identify potential nonlinear trends.  

**Examples:**
- How does **odometer (mileage)** correlate with price?  
- Do **newer cars (year)** show higher prices?  
- Does **condition** or **title_status** significantly affect price?  
- Are there regional variations in pricing?  

---

## 6. Modeling Approach
---

We will experiment with multiple regression approaches to identify the most suitable model for predicting car prices.  

**Modeling Options:**
1. **Simple Linear Regression**  
   - Baseline model to establish a benchmark for prediction accuracy.  
   - Assumes a linear relationship between features and price.  

2. **Ridge Regression**  
   - Adds L2 regularization to handle **multicollinearity** among predictors.  
   - Helps stabilize coefficients and improve generalization.  

3. **Ridge Regression with Feature Selection**  
   - Combines Ridge with a **feature selector** (e.g., `SelectFromModel`) to remove weak predictors.  
   - Improves model interpretability while retaining predictive power.  

**Next Step:**  
Run these models and compare performance using **R², RMSE, and MAE** to determine which approach yields the best prediction accuracy.  
 

**Evaluation Metrics:**
- R² Score (explained variance)  
- RMSE (Root Mean Squared Error)  
- MAE (Mean Absolute Error)  

---

## 7. CRISP-DM Mapping
- **Business Understanding** → Identify price drivers for competitive advantage.  
- **Data Understanding** → Explore 18 vehicle attributes.  
- **Data Preparation** → Clean missing values, encode categorical features, remove outliers.  
- **Modeling** → Regression models with regularization and feature selection.  
- **Evaluation** → Compare model performance using R², RMSE, MAE.  
- **Deployment** → Enable pricing tool for marketplace sellers and buyers.  

---
# 📊 Vehicle Price Prediction – Analysis Report

---

## 🎯 Objective
The goal of this analysis was to **understand the key factors influencing used vehicle prices** and to build predictive models that estimate prices more accurately.  

This enables dealers to:  
- 💰 **Price vehicles competitively**  
- 🔍 **Identify undervalued or overvalued inventory**  
- ⭐ **Prioritize features that add the most resale value**  

---

## 📂 Data & Features Considered
We used historical vehicle listings with the following attributes:  

- Manufacturer  
- Fuel Type  
- Transmission  
- Year of Manufacture  
- Odometer Reading  
- Condition (excellent, good, fair, etc.)  
- Cylinders  
- Title Status  

---

## 📈 Key Data Insights
- **Odometer (mileage):**  
  Strong negative correlation with price → higher mileage = lower resale value.  

- **Condition:**  
  Vehicles in *excellent* or *like new* condition fetch significantly higher prices than those in *fair/poor* condition.  

- **Year:**  
  Newer vehicles are priced higher, but depreciation accelerates after certain age thresholds.  

- **Manufacturer & Transmission:**  
  Certain brands and automatic transmissions consistently command higher prices.  

---

## 🤖 Modeling Approach
We compared three regression models:  

1. **Linear Regression**  
   - 📊 Accuracy (R²): ~65%  
   - ✅ Captured linear relationships  
   - ❌ Struggled with complex, nonlinear patterns  

2. **Ridge Regression (Regularized Linear)**  
   - 📊 Accuracy (R²): ~59%  
   - ❌ No improvement over linear regression, suggesting limited linear predictive power  

3. **Random Forest Regressor**  
   - 📊 Accuracy (R²): ~85%  
   - ✅ Captured nonlinear feature interactions effectively  
   - 🏆 **Best-performing model for this dataset**  

---

## 💡 Business Takeaways
- 🚗 **Mileage & Condition are the strongest price drivers** → highlight low-mileage, excellent-condition cars.  
- 🏷️ **Brand & Transmission add value** → certain manufacturers and automatic transmissions lead to higher resale prices.  
- 🤝 **Machine Learning adds real value** → Random Forest achieved ~85% accuracy, making it a reliable pricing tool.  

---

## 🔜 Next Steps
- 📌 **Feature Expansion:** Add variables like drive type, paint color, and regional effects.  
- ⚙️ **Model Deployment:** Integrate the Random Forest model into a dealer pricing tool.  
- 📆 **Continuous Monitoring:** Reassess and retrain models as market conditions evolve.  

---

## ✅ Conclusion
While **linear models** provided only modest accuracy, the **Random Forest model** delivered the best predictive power (~85%).  

👉 This approach empowers dealers to:  
- Optimize inventory decisions  
- Set **competitive and fair prices**  
- Maximize profitability in the resale market  