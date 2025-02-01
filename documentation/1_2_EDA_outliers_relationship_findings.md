# Exploratory Data Analysis (EDA) - Outliers and Feature Relationships Findings

## 1️⃣ Outlier Detection (IQR Method)
To identify outliers, we used **boxplots** and the **Interquartile Range (IQR) method**. The following key observations were made:

### **Boxplots for Outlier Detection**
- A **boxplot** was generated for all numerical features to visualize the presence of extreme values.
- Features with a significant number of **outliers** include:
  - **NT (173 outliers)** – Normalizing Temperature.
  - **THQCr (161 outliers)** – Cooling Rate for Through Hardening.
  - **Ni (102 outliers)** – Nickel percentage.
  - **Mn (96 outliers)** – Manganese percentage.
  - **Fatigue Strength (63 outliers)** – The target variable contains extreme values.
- Features like **S, Cr, Mo, and dA** have minimal or no outliers, suggesting more stable distributions.

### **IQR-Based Outlier Count**
- The **IQR method** was used to detect extreme values numerically, confirming the findings from boxplots.
- The number of outliers per feature was computed and summarized in the results.

**Outliers detected (IQR method):**
|Feature | IQR-Based Outlier Count |
|--------| ------------------------|
| Sl. No. | 0 |
| NT | 173 |
| THT | 92 |
| THt | 59 | 
| THQCr | 161 | 
| CT | 48 | 
| Ct | 48 | 
| DT | 48 |
| Dt | 48 | 
| QmT | 48 |
| TT | 59 |
| Tt | 59 |
| TCr | 59 |
| C | 38 | 
| Si | 15 |
| Mn | 96 |
| P | 3 |
| S | 0 |
| Ni | 102 | 
| Cr | 0 |
| Cu | 2 | 
| Mo | 0 |
| RedRatio | 3 |
| dA | 0 |
| dB | 96 |
| dC | 35 |
| Fatigue | 63 |

---

## 2️⃣ Feature Distributions
To understand the spread of the data, **histograms** were plotted for all features.

### **Histogram Analysis**
- **Most chemical composition features (C, Si, Mn, etc.) are right-skewed**, indicating a need for potential transformations.
- **Fatigue Strength appears approximately normal** but includes some extreme values that might impact modeling.
- **Processing parameters (NT, THT, TT, etc.) show varying distributions**, with some appearing uniform and others having clear peaks.

---

## 3️⃣ Correlation Analysis
A **correlation matrix heatmap** was plotted to examine relationships between features.

### **Findings from Correlation Analysis**
- **Strong correlations observed:**
  - **NT (Normalizing Temperature) vs. THT (Through Hardening Temperature)** – These may be redundant.
  - **C (Carbon) and RedRatio** – Suggests that carbon content is related to the reduction process in steel.
- **Fatigue Strength (Target Variable) has moderate correlations** with:
  - **C (Carbon) and RedRatio** – Carbon is known to influence fatigue resistance.
  - **Cr (Chromium) and Ni (Nickel)** – Typically contribute to material hardness, but their correlation with fatigue strength is weaker than expected.

---

## 4️⃣ Feature Relationships (Scatter Plots)
Scatter plots were generated for key feature pairs to explore potential trends.

In our scatter plot analysis, we selected four specific feature relationships:

- **C vs. Fatigue**
- **Cr vs. Fatigue**
- **Si vs. Fatigue**
- **RedRatio vs. Fatigue**

We prioritized these because:

- **Domain Knowledge**: These features are expected to **influence fatigue strength** based on metallurgy and material science.
- **Correlation Insights**: These features showed some correlation with **Fatigue Strength** in our **correlation heatmap**.
- **Feature Engineering Considerations**: Certain chemical compositions (C, Cr, Si) are **known to affect steel properties**, and **RedRatio (Reduction Ratio)** relates to processing.


### **Scatter Plot Observations**
- **C vs. Fatigue Strength:**
  - Some increasing trends are visible, meaning **higher carbon levels might enhance fatigue resistance**.
  - However, the relationship is not perfectly linear, suggesting additional influencing factors.
- **Cr vs. Fatigue Strength:**
  - No clear trend is observed, meaning **Chromium might not be a strong predictor**.
- **RedRatio vs. Fatigue Strength:**
  - Shows a somewhat linear relationship, indicating that **higher reduction ratios correlate with higher fatigue strength**.

Ideally, we should examine all numerical features to uncover hidden relationships. However, plotting scatter plots for all features at once may be overwhelming.
- While we started with **4 features**, we **should explore all relationships**.
- Using **pairplots and automated feature selection** helps us **avoid manual bias**.
- We can now **extend our analysis to all relevant features** and update our findings.

### **Updated Scatter Plot Analysis**
#### **🔹 Automatically Selected Features for Fatigue Strength Relationship**
The following features were **automatically selected** based on a correlation threshold **(0.3 or higher with Fatigue Strength):**
- **Tt** (Tempering Time)
- **CT** (Carburization Temperature)
- **DT** (Diffusion Temperature)
- **Ct** (Carburization Time)
- **Dt** (Diffusion Time)
- **QmT** (Quenching Media Temperature)
- **THT** (Through Hardening Temperature)
- **THt** (Through Hardening Time)
- **TCr** (Cooling Rate for Tempering)
- **NT** (Normalizing Temperature)
- **TT** (Tempering Temperature)
- **THQCr** (Cooling Rate for Through Hardening)
- **Cr** (Chromium Content)
- **C** (Carbon Content)
- **Mo** (Molybdenum Content)

### **Understanding Correlation Strength**
Correlation values range from -1 to 1:

| Correlation Coefficient | Strength of Relationship |
|-------------------------|--------------------------|
|0 to ±0.1 | Very weak (Negligible)
|±0.1 to ±0.3 | Weak correlation
|±0.3 to ±0.5 | Moderate correlation ✅ (Threshold chosen)
|±0.5 to ±0.7 | Strong correlation
|±0.7 to ±1.0 | Very strong correlation

- Below 0.3 → Relationship is often too weak to be meaningful.
- Above 0.3 → Indicates a moderate or stronger linear relationship.
- Above 0.5 → More strongly related but may be too restrictive, excluding useful features.

### **Final Justification for 0.3**
- Balanced Approach → Includes moderately relevant features without excessive noise.
- Industry Standard → Many studies consider 0.3 a reasonable cut-off for exploratory analysis.

### **Scatter Plot Observations**
- **Tt (Tempering Time) vs. Fatigue Strength**
  - Somewhat spread distribution; no clear linear relationship.
- **CT, DT, Ct, Dt** vs. Fatigue Strength  
  - Diffusion and Carburization temperatures **show some clustering**, suggesting possible influence but with high variability.
- **THQCr (Cooling Rate for Through Hardening) vs. Fatigue Strength**  
  - Shows some **non-linear trends**, indicating a potential threshold effect.
- **C (Carbon) vs. Fatigue Strength**  
  - Slight upward trend suggesting **higher carbon content might contribute to higher fatigue strength**.
- **Cr (Chromium) vs. Fatigue Strength**  
  - **No clear relationship**, suggesting Chromium **may not be a primary predictor**.
- **QmT (Quenching Media Temperature) vs. Fatigue Strength**
  - Appears to have a **moderate positive trend**, indicating that higher quenching media temperatures may improve fatigue strength.
- **THT (Through Hardening Temperature) vs. Fatigue Strength**
  - Shows **strong clustering**, indicating a possible threshold effect in heat treatment processes.
- **THt (Through Hardening Time) vs. Fatigue Strength**
  - Exhibits **non-linear trends**, suggesting that **certain ranges of through hardening time optimize fatigue resistance**.
- **TCr (Cooling Rate for Tempering) vs. Fatigue Strength**
  - Has **high variability**, making it difficult to determine a clear pattern.
- **NT (Normalizing Temperature) vs. Fatigue Strength**
  - Displays **some correlation**, but variations exist, possibly influenced by other parameters.
- **TT (Tempering Temperature) vs. Fatigue Strength**
  - Shows **a weak relationship**, indicating tempering temperature alone may not strongly impact fatigue strength.

---

## **📌 Conclusion and Next Steps**
### **Key Takeaways**
- Several features have **a high number of outliers**, particularly in **processing parameters and chemical composition**.
- **Fatigue Strength** is influenced by **Carbon, RedRatio, and potentially other factors**, but not all relationships are strong.
- **Certain features are highly correlated (e.g., NT and THT),** which may require feature selection to remove redundancy.

### **Next Steps**
1. **Outlier Treatment**
   - Decide whether to **remove, cap, or transform outliers** based on their impact on model performance.
2. **Feature Selection & Engineering**
   - Remove or combine redundant features (e.g., NT and THT).
   - Apply transformations (e.g., log/square root) to skewed features to improve normality.
3. **Proceed to Model Preparation**
   - Prepare the dataset for training, ensuring data is clean and properly scaled.

The next phase will focus on **outlier handling and feature selection** to improve model performance. 🚀

