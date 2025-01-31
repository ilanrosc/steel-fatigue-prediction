# Outlier Analysis for Selected Features

## 📌 Overview
Before proceeding with model training, we need to analyze and treat potential outliers in our **final selected features** to ensure data quality and model stability. This step helps identify extreme values that might distort model performance.

## 🔹 Selected Features for Analysis
The following features were retained after **Feature Selection** and will be analyzed for outliers:
- **NT** (Normalizing Temperature)
- **Ct** (Carburization Time)
- **Dt** (Diffusion Time)
- **QmT** (Quenching Media Temperature)
- **TT** (Tempering Temperature)
- **C** (Carbon Content)
- **Si** (Silicon Content)
- **Mn** (Manganese Content)
- **P** (Phosphorus Content)
- **Cr** (Chromium Content)
- **Mo** (Molybdenum Content)
- **RedRatio** (Reduction Ratio)
- **dA** (Area Proportion of Inclusions Deformed by Plastic Work)

## 🔹 Normality Check
Before proceeding with outlier detection, we need to assess the normality of our features. This helps determine whether features are normally distributed, which influences our choice of outlier treatment methods.

### **Methods Used for Normality Check**
1️⃣ **Histogram and KDE Plots** - Visual inspection of distributions.  
2️⃣ **Shapiro-Wilk Test** - Statistical test for normality.  
3️⃣ **Kolmogorov-Smirnov Test** - Another test for assessing normal distribution.  
4️⃣ **Q-Q Plots** - Checking if data follows a normal distribution curve.  

## 📊 Normality Test Results

| Feature    | Shapiro-Wilk Statistic | p-value |
|------------|------------------------|---------|
| **NT**     | 0.824224                | 1.57e-21 |
| **Ct**     | 0.348856                | 1.25e-36 |
| **Dt**     | 0.340081                | 8.34e-37 |
| **QmT**    | 0.303890                | 1.63e-37 |
| **TT**     | 0.674344                | 4.09e-28 |
| **C**      | 0.962550                | 4.11e-09 |
| **Si**     | 0.265794                | 3.17e-38 |
| **Mn**     | 0.714815                | 1.28e-26 |
| **P**      | 0.980479                | 1.29e-05 |
| **Cr**     | 0.847688                | 3.91e-20 |
| **Mo**     | 0.709567                | 8.03e-27 |
| **RedRatio** | 0.687874              | 1.24e-27 |
| **dA**     | 0.948611                | 3.52e-11 |

**Interpretation:** The **p-values for all features are very low (< 0.05)**, indicating that **none of the features follow a normal distribution**. This suggests that we should consider **non-parametric outlier detection methods**.

## 📊 Kolmogorov-Smirnov Normality Test Results

|Feature | KS Statistic | p-value |
|--------|--------------|---------|
| **NT**     |      0.331296 |   3.040798e-43 |
| **Ct**     |      0.515336 |  2.534310e-108 |
| **Dt**     |      0.511320 |  1.599316e-106 |
| **QmT**     |      0.501499 |  3.370870e-102 |
| **TT**     |      0.355752 |   5.375249e-50 |
| **C**     |      0.099564 |   3.184237e-04 |
| **Si**     |      0.396003 |   2.630964e-62 |
| **Mn**     |      0.313821 |   9.583218e-39 |
| **P**     |      0.071328 |   2.228355e-02 |
| **Cr**     |      0.196511 |   2.916202e-15 |
| **Mo**     |      0.357902 |   1.290584e-50 |
| **RedRatio**     |      0.231523 |   4.444605e-21 |
| **dA**     |      0.155941 |   9.537693e-10 |

**Interpretation:** The Kolmogorov-Smirnov test results indicate that the selected features **deviate from a normal distribution**, confirming the findings from the Shapiro-Wilk test. Since most features have very high p-values, we continue with the assumption that the data is **non-normally distributed**.

## 📊 IQR-Based Outlier Detection Results

| Feature    | Lower Bound | Upper Bound | Outlier Count |
|------------|------------|------------|--------------|
| **NT**     | 857.5000    | 877.5000    | 173 |
| **Ct**     | 0.0000      | 0.0000      | 48  |
| **Dt**     | 0.0000      | 0.0000      | 48  |
| **QmT**    | 30.0000     | 30.0000     | 48  |
| **TT**     | 400.0000    | 800.0000    | 59  |
| **C**      | 0.2050      | 0.5650      | 38  |
| **Si**     | 0.1650      | 0.3650      | 15  |
| **Mn**     | 0.5500      | 0.9500      | 96  |
| **P**      | 0.0015      | 0.0295      | 3  |
| **Cr**     | -1.1700     | 2.2700      | 0  |
| **Mo**     | -0.2550     | 0.4250      | 0  |
| **RedRatio** | -367.0000   | 2185.0000   | 3  |
| **dA**     | -0.0550     | 0.1450      | 0  |

**Interpretation:** The IQR method identified several outliers in our dataset, with **NT, Ct, Dt, QmT, Mn, and TT showing the highest number of outliers**. Features like **Cr, Mo, and dA** have no detected outliers, suggesting they fall within a reasonable range.

## 📊 Skewness Analysis Results
Since the normality test results showed deviation from a normal distribution, it is essential to check skewness before deciding how to handle outliers. Skewness analysis helps determine whether a feature is symmetrical or significantly distorted, guiding us in choosing the appropriate outlier treatment and transformation methods.

If a feature is highly skewed, applying transformations such as log, square root, or Box-Cox can help normalize the distribution, stabilize variance, and improve the performance of machine learning models that assume a more linear relationship between features.

| Feature    | Skewness |
|------------|----------|
| **NT**     | 0.682492  |
| **Ct**     | 3.072213  |
| **Dt**     | 3.410004  |
| **QmT**    | 4.456059  |
| **TT**     | -1.868327 |
| **C**      | -0.131750 |
| **Si**     | 5.945403  |
| **Mn**     | 1.722104  |
| **P**      | 0.344301  |
| **Cr**     | -0.133219 |
| **Mo**     | 0.590002  |
| **RedRatio** | 3.793718  |
| **dA**     | 0.493326  |

**Interpretation:**
- **Features with high positive skewness (> 1.5):** `Ct, Dt, QmT, Si, RedRatio` indicate strong right-skewed distributions, suggesting the need for **log or square root transformations**.
- **Features with high negative skewness (< -1.5):** `TT` shows left-skewness, which may require a **power transformation**.
- **Features close to normal (-1 to 1):** `NT, C, P, Cr, Mo, dA` are nearly symmetric and may not need transformations.

## Observations from Our Dataset
- **Highly right-skewed features (>+1.5):**
	- **Si (5.945), QmT (4.456), RedRatio (3.794), Dt (3.410), Ct (3.072), Mn (1.722)**
	- These features have **extreme high values**, meaning they contain **significant outliers** in the upper range.
- **Highly left-skewed feature (<-1.5):**
	- **TT (-1.868)**
	- This feature has **extreme low values**, indicating an **outlier presence in the lower range**.
- **Moderately skewed features (-1 to +1):**
	- **NT (0.682), Mo (0.590), dA (0.493), P (0.344), C (-0.132), Cr (-0.133)**
	- These features show **mild skewness**, and transformations may not be necessary.

**Decision on Next Steps**

Since several features (**Si, QmT, RedRatio, Dt, Ct, Mn, and TT**) have **high skewness**, we will apply **data transformations** to reduce skewness before moving to model training.

- **For right-skewed features**, we will use **log transformation** (log1p) or **Box-Cox transformation** (if data is strictly positive).
- **For the left-skewed feature (TT)**, we may apply a **Box-Cox transformation**.
- **For mildly skewed features**, no transformation is needed unless further analysis suggests otherwise.

## The Zero/Negative Value Analysis shows that:

**Final Transformation Decision:**
| Feature | Skewness | Zero/Negative Values? | Best Transformation|
|---------|----------|-----------------------|--------------------|
|**Si (5.945)** | ✅ Highly right-skewed | ❌ No | Box-Cox |
|**QmT (4.456)** | ✅ Highly right-skewed | ❌ No | Box-Cox |
|**RedRatio (3.794)** | ✅ Highly right-skewed | ❌ No | Box-Cox |
|**Dt (3.410)** | ✅ Highly right-skewed | ⚠️ Yes (389 zeros) | Log (log1p) |
|**Ct (3.072)** | ✅ Highly right-skewed | ⚠️ Yes (389 zeros) | Log (log1p) |
|**Mn (1.722)** | ✅ Right-skewed | ❌ No | Box-Cox |
|**TT (-1.868)** | ❌ Left-skewed | ❌ No | Box-Cox |


## Next Steps

We will now:

1. Apply Box-Cox transformation to Si, QmT, RedRatio, Mn, and TT.
2. Apply Log transformation (log1p) to Dt and Ct (since they contain zeros).

## Summary of What We Did:

✅ **Applied Box-Cox transformation** to:
- **Si, QmT, RedRatio, Mn, and TT** (since they are strictly positive).

✅ **Applied Log transformation** (log1p) to:
- **Dt and Ct** (since they contain zero values).

**Key Findings:**
Significant improvement in skewness for all features:
- **Si (-0.294), QmT (0.000), RedRatio (0.008), and Mn (-0.102)** are now close to 0, indicating near-normal distribution.
- **TT (-1.014)** still has some **left skewness**, but it's significantly reduced.

## Final Skewness Analysis After Transformation

The **final skewness results** confirm that the transformations have successfully reduced skewness:

| Feature | Skewness Before | Skewness After |
|---------|-----------------|----------------|
| Si | 5.945 | -0.294 ✅ (Significantly improved) |
| QmT | 4.456 | 0.000 ✅ (Perfectly normalized) |
| RedRatio | 3.794 | 0.008 ✅ (Very close to normal) |
| Mn | 1.722 | -0.102 ✅ (Much improved) |
| TT | -1.868 | -1.014 ⚠️ (Still left-skewed, but better) |

## Final Feature Status Summary:

| Feature | Initial Skewness | Final Skewness | Transformation Applied |
|---------|------------------|----------------|------------------------|
|      **NT** |  0.682 |    NaN |        None |
|      **Ct** |  3.072 | -0.294 | Log (log1p) |
|      **Dt** |  3.410 |  0.000 | Log (log1p) |
|     **QmT** |  4.456 |  0.008 |     Box-Cox |
|      **TT** | -1.868 | -1.014 |     Box-Cox |
|       **C** | -0.132 |    NaN |        None |
|      **Si** |  5.945 | -0.294 |     Box-Cox |
|      **Mn** |  1.722 | -0.102 |     Box-Cox |
|       **P** |  0.344 |    NaN |        None |
|      **Cr** | -0.133 |    NaN |        None |
|      **Mo** |  0.590 |    NaN |        None |
|**RedRatio** |  3.794 |  0.008 |     Box-Cox |
|      **dA** |  0.493 |    NaN |        None |

**Key Observations:**
1. **Successfully Transformed Features:**

- Box-Cox Transformation Applied to: QmT, TT, Si, Mn, RedRatio
	- ✅ Skewness significantly reduced (values close to 0).
-Log Transformation (log1p) Applied to: Ct, Dt
	- ✅ Both features' skewness is now well-controlled.
- Features That Required No Transformation:
	- NT, C, P, Cr, Mo, dA
	- ✅ These features had acceptable skewness and did not require transformation.

## Final Correlation Check:

**1️⃣ Strong Positive Correlations (Potential Multicollinearity)**
- **Ct, Dt, QmT** are **highly correlated** with each other (>0.98).
	- This suggests that these features might **contain redundant information**.
	- We may need to remove one of them or apply dimensionality reduction (e.g., PCA, VIF check).
- **Cr and Mo (0.61)** → Indicates **a moderate correlation**, but not necessarily an issue.

**2️⃣ Strong Negative Correlations**
- **NT and C (-0.88)** → Suggests an inverse relationship between these two features.
- **NT and TT (-0.57)** → Shows that as NT increases, TT decreases.
- **Ct, Dt, QmT vs. TT (-0.73 to -0.74)** → Suggests a strong inverse relationship, meaning TT behaves differently from these.
**3️⃣ Low or Weak Correlations (Feature Independence)**
- **Si, Mn, P, RedRatio, dA** have mostly weak correlations (< |0.3|) with other features.
- These features **should be kept** as they bring independent information.


## 📌 Next Steps: How Should We Handle This?

**Multicollinearity Check for Ct, Dt, QmT**

✅ Apply Variance Inflation Factor (VIF) to see if one should be removed.

✅ If VIF is very high (>10) for one feature, we drop it.

**VIF Analysis Interpretation**
|Feature | VIF Value | Interpretation |
|--------|-----------|----------------|
|Ct | 27.21 | 🚨 High multicollinearity |
|Dt | 27.21 | 🚨 High multicollinearity |
|QmT | 1.12 | ✅ No multicollinearity issue |

**What This Means**
- **Ct and Dt have extremely high VIF values (>10)** → They are highly redundant.
- **QmT has a low VIF (1.12)** → It does **not contribute to multicollinearity** and can be safely kept.

**📌 Decision: Remove *Ct* or *Dt* Based on Domain Knowledge**

Since both **Ct (Carburization Time)** and **Dt (Diffusion Time)** are highly skewed and show a large number of outliers, we need to decide which one to remove while keeping the most relevant feature for predicting fatigue strength. **Both `Ct` and `Dt` had extremely high VIF values (>10), meaning they were highly redundant.**

**🔹 Domain Knowledge Considerations**

**1️⃣ Carburization Time (Ct)**
- Represents the time during which a metal is exposed to a carbon-rich environment to increase surface hardness.
- Mainly impacts surface properties, which may not significantly influence the overall fatigue strength.
- If diffusion is already considered in another feature (e.g., Dt), it might be redundant.

**2️⃣ Diffusion Time (Dt)**
- Represents the time allowed for carbon (or other elements) to diffuse deeper into the metal.
- More critical for internal material strength, which directly affects fatigue resistance over long cycles.
- If carburization time is short but diffusion is longer, the metal might still have improved fatigue properties.

**Decision: Remove `Ct`, Keep `Dt`**

✅ Why Keep `Dt` (Diffusion Time)?
- Diffusion affects the entire material, not just the surface.
- More relevant for fatigue strength, which depends on deep material properties, not just surface hardening.
- Stronger physical correlation with long-term fatigue behavior.

**🚨 Why Remove `Ct` (Carburization Time)?**
- More focused on surface hardening, which may be less critical for fatigue strength.
- If `Dt` is present, `Ct` could be redundant and introduce multicollinearity.

## Conclusion:
- The dataset is now well-prepared for model training with a better distribution balance.
- Next Steps: We can proceed with feature scaling and move on to model training.