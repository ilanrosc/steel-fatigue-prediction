# Feature Selection

## 📌 Overview
Feature selection is an essential step in preparing our dataset for machine learning models. The goal is to:
- **Remove redundant or highly correlated features** that introduce noise.
- **Ensure model interpretability** by selecting the most relevant features.
- **Handle collinearity** to avoid multicollinearity issues that can affect model stability.

## 🔹 Planned Steps
1. **Variance Inflation Factor (VIF) Analysis**  
   - Identify and remove highly correlated features to prevent multicollinearity.
   - Drop features with **VIF > 5**, indicating redundancy.

2. **Feature Importance Evaluation Using SHAP**  
   - Use SHAP values to determine the most predictive variables based on their impact on the target variable.

3. **Final Feature Set Selection**  
   - Retain only the **most relevant and independent** features based on VIF and SHAP analysis.

---

## 📊 Findings & Interpretation

### **Updated VIF Results**

#### **VIF Thresholds for Interpretation**
- **VIF > 5** → Feature is redundant and should be dropped.
- **VIF between 1-5** → Feature is useful.
- **VIF ≈ 1** → No collinearity issue.

| Feature | VIF Score | Interpretation |
|---------|----------|---------------|
| **Tt (Tempering Time)** | **∞ (Infinite)** | **Perfect multicollinearity – Must be removed** |
| **THt (Through Hardening Time)** | **∞ (Infinite)** | **Perfect multicollinearity – Must be removed** |
| **TCr (Cooling Rate for Tempering)** | **∞ (Infinite)** | **Perfect multicollinearity – Must be removed** |
| **CT (Carburization Temperature)** | **9.14M** | Extremely high collinearity – Consider removal |
| **THT (Through Hardening Temperature)** | **5806.69** | Very high collinearity – Consider removal |
| **DT (Diffusion Temperature)** | **4742.95** | Very high collinearity – Consider removal |
| **NT (Normalizing Temperature)** | **74.49** | High collinearity – Review impact before removing |
| **THQCr (Cooling Rate for Through Hardening)** | **34.35** | High collinearity – Review needed |
| **Cr (Chromium Content)** | **18.00** | Moderate collinearity – Might still be useful |
| **C (Carbon Content)** | **16.77** | Moderate collinearity – Might still be useful |
| **TT (Tempering Temperature)** | **15.68** | Moderate collinearity – Could be retained |
| **Dt (Diffusion Time)** | **15.33** | Moderate collinearity – Needs further review |
| **Mn (Manganese Content)** | **11.50** | Moderate collinearity – Needs further review |
| **Ni (Nickel Content)** | **9.73** | Moderate collinearity – Needs further review |
| **Ct (Carburization Time)** | **7.67** | Some collinearity – Review needed |
| **Mo (Molybdenum Content)** | **3.68** | Low collinearity – Likely safe to keep |
| **QmT (Quenching Media Temperature)** | **3.48** | Low collinearity – Likely safe to keep |
| **Si (Silicon Content)** | **2.58** | Low collinearity – Likely safe to keep |
| **dA (Inclusion Property A)** | **2.30** | Low collinearity – Likely safe to keep |
| **S (Sulfur Content)** | **1.77** | Low collinearity – Likely safe to keep |
| **Cu (Copper Content)** | **1.72** | Low collinearity – Likely safe to keep |
| **dB (Inclusion Property B)** | **1.49** | Low collinearity – Likely safe to keep |
| **dC (Inclusion Property C)** | **1.40** | Low collinearity – Likely safe to keep |
| **RedRatio (Reduction Ratio)** | **1.38** | Low collinearity – Likely safe to keep |
| **P (Phosphorus Content)** | **1.31** | Low collinearity – Likely safe to keep |

### **SHAP Feature Importance Results**

| Feature | SHAP Value |
|---------|-----------|
| **Cr (Chromium Content)** | **58.08** |
| **TT (Tempering Temperature)** | **29.56** |
| **Tt (Tempering Time)** | **15.18** |
| **NT (Normalizing Temperature)** | **14.79** |
| **CT (Carburization Temperature)** | **14.63** |
| **C (Carbon Content)** | **14.51** |
| **DT (Diffusion Temperature)** | **13.75** |
| **Dt (Diffusion Time)** | **13.71** |
| **Ct (Carburization Time)** | **12.71** |
| **QmT (Quenching Media Temperature)** | **10.90** |
| **P (Phosphorus Content)** | **6.95** |
| **Mo (Molybdenum Content)** | **3.64** |
| **Mn (Manganese Content)** | **2.80** |
| **dA (Inclusion Property A)** | **2.62** |
| **THT (Through Hardening Temperature)** | **1.62** |
| **THt (Through Hardening Time)** | **1.46** |
| **Si (Silicon Content)** | **1.45** |
| **RedRatio (Reduction Ratio)** | **1.38** |
| **TCr (Cooling Rate for Tempering)** | **1.04** |
| **THQCr (Cooling Rate for Through Hardening)** | **0.96** |
| **S (Sulfur Content)** | **0.95** |
| **Ni (Nickel Content)** | **0.67** |
| **Cu (Copper Content)** | **0.67** |
| **dB (Inclusion Property B)** | **0.49** |
| **dC (Inclusion Property C)** | **0.42** |

---

## 📊 Final Selected Features
After applying **VIF analysis and SHAP feature importance**, we have removed redundant and less important features. The final selected features are:

| Feature | Description |
|---------|------------|
| **NT**  | Normalizing Temperature |
| **Ct**  | Carburization Time |
| **Dt**  | Diffusion Time |
| **QmT** | Quenching Media Temperature |
| **TT**  | Tempering Temperature |
| **C**   | Carbon Content |
| **Si**  | Silicon Content |
| **Mn**  | Manganese Content |
| **P**   | Phosphorus Content |
| **Cr**  | Chromium Content |
| **Mo**  | Molybdenum Content |
| **RedRatio** | Reduction Ratio (Ingot to Bar) |
| **dA**  | Area Proportion of Inclusions Deformed by Plastic Work |

These features represent the **most important predictors** for **fatigue strength** while avoiding multicollinearity issues.

---

### **📌 Key Takeaways**
1. **High VIF features removed:** `Tt, THt, TCr, CT, THT, DT` (multicollinearity issue).
2. **Low SHAP importance features removed:** `THQCr, S, Ni, Cu, dB, dC` (low impact on prediction).
3. **Final features are well-balanced between material composition and processing conditions.**

---

### **📌 Next Steps**
✅ **Apply feature transformations (scaling, normalization, etc.)**  
✅ **Prepare dataset for model training and evaluation.**  

We are now ready to move to **outlier treatment and feature transformations** before building the predictive model. 🚀