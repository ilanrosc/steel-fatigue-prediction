# Exploratory Data Analysis (EDA)

## 📌 Purpose of EDA
Exploratory Data Analysis (EDA) helps us understand the dataset before building predictive models. The main objectives are:

1. **Understand Data Structure**: Inspect rows, columns, and data types.
2. **Identify Missing Values**: Handle incomplete data appropriately.
3. **Detect Outliers**: Find extreme values that may impact model performance.
4. **Analyze Feature Distributions**: Examine value ranges and transformations.
5. **Investigate Correlations**: Identify relationships between features and the target variable.

---
## 1️⃣ Dataset Overview
- **Total records:** 437 rows  
- **Total features:** 27 columns  
- **No missing values** – All columns have complete data.  
- **Data Types:**  
  - **Integer features:** Processing parameters, fatigue strength.  
  - **Float features:** Chemical composition, inclusion properties.  

---

## 2️⃣ Feature Distributions
- **Chemical Composition Features (C, Si, Mn, P, etc.)**  
  - Represented as small fractional values.  
  - Likely to have strong influence on fatigue strength.  

- **Processing Parameters (NT, THT, THt, etc.)**  
  - Ranges are well-defined, with some features having uniform values.  
  - Need to check for variance and redundancy in modeling.

- **Fatigue Strength (Target Variable)**  
  - Ranges from **225 to 1190**.  
  - Mean fatigue strength: **~553**.  
  - Needs further investigation to understand distribution shape.  

---

## 3️⃣ Missing Data Check
- ✅ **No missing values** in the dataset.  
- No need for imputation, but verifying data consistency is still necessary.  

---

## 4️⃣ Next Steps
Now that we have a basic understanding, the next steps in EDA include:  
- **Outlier Detection** – Checking extreme values in fatigue strength and chemical elements.  
- **Feature Relationships** – Exploring **correlations** between fatigue strength and other factors.  
- **Variance & Redundancy Analysis** – Identifying low-variance or duplicated features.  

---

## 🔹 Next Action: Outlier Detection
We will now analyze outliers using **boxplots and the IQR method** to check for extreme values.

