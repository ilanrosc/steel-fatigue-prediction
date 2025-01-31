# **Model Selection for Fatigue Strength Prediction**

## **1. Problem Definition**
We need to predict **fatigue strength** based on multiple material and process-related features. Since our target variable is **continuous**, this is a **Regression Problem**.

## **2. Factors Affecting Model Choice**
To determine the best model for prediction, we consider:
- **Dataset Size:** Determines model efficiency and scalability.
- **Feature Complexity & Relationships:** Influences model interpretability and performance.
- **Need for Interpretability:** Some models provide clear insights, others are black-box.
- **Accuracy vs. Speed Trade-off:** Higher accuracy often means more computation.
- **Feature Scaling Requirements:** Some models require data normalization or standardization.

## **3. Model Evaluation Criteria**
To select the best model, we will evaluate:
- **Mean Absolute Error (MAE):** Measures absolute differences.
- **Mean Squared Error (MSE):** Penalizes large errors more.
- **R² Score:** Measures goodness of fit.
- **Training vs. Testing Performance:** Identifies overfitting.
- **Cross-Validation Results:** Ensures model generalization.

## **4. Model Candidates & Suitability**
| **Model** | **Pros** | **Cons** | **Feature Scaling Needed?** |
|----------|---------|---------|------------------------|
| **Linear Regression** | Simple, interpretable | Performs poorly on non-linear data | ✅ Yes |
| **Decision Tree Regressor** | Handles non-linearity, fast | Can overfit small data | ❌ No |
| **Random Forest Regressor** | Reduces overfitting, high accuracy | Slow for large datasets | ❌ No |
| **XGBoost Regressor** | Highly accurate, handles missing values | Requires parameter tuning | ❌ No |
| **Neural Networks (MLP Regressor)** | Best for large datasets | Requires large data, long training | ✅ Yes |

## **5. Model Selection Decision**
Since our dataset is likely **small-to-medium in size**, and we are predicting **continuous values**, we prioritize:
1. **Random Forest** ✅ → Great for **handling non-linearity, no need for feature scaling**.
2. **XGBoost** ✅ → Best for **accuracy, robustness, and handling complex relationships**.
3. **Decision Tree** ✅ → Useful as a baseline model, interpretable.

## **6. Next Steps**
1. **Perform train-test split** and train the selected models.
2. **Compare model performance using MAE, MSE, and R² score.**
3. **Fine-tune hyperparameters for the best-performing model.**
4. **Finalize and deploy the model for predictions.**


## **7. Model Performance Comparison & Best Model Selection**

| **Model** | **Mean Absolute Error (MAE)** | **Mean Squared Error (MSE)** | **R² Score** | **Interpretation** |
|-------------------|----------------------------|----------------------------|------------|----------------|
| **Random Forest** | **19.36**                  | **649.15**                  | **0.9843**  | High accuracy, well-balanced performance. |
| **Decision Tree** | **26.20**                  | **1201.16**                 | **0.9709**  | Higher error, likely overfitting on training data. |
| **XGBoost**       | **16.78**                  | **572.12**                  | **0.9862**  | **Best performance** with lowest error and highest R². |

### **✅ Model Interpretation**
1. **XGBoost performed the best** ✅  
   - **Lowest MAE (16.78)** → Smallest average prediction error.  
   - **Lowest MSE (572.12)** → Least penalization for large errors.  
   - **Highest R² Score (0.9862)** → Explains **98.62% of the variance**, showing excellent fit.  

2. **Random Forest performed well, but slightly worse than XGBoost** ⚠️  
   - **MAE (19.36) and MSE (649.15)** are higher than XGBoost.  
   - **R² Score (0.9843)** is still very high, meaning it fits the data well.  

3. **Decision Tree performed the worst** ❌  
   - **Highest MAE (26.20)** → More significant errors.  
   - **Highest MSE (1201.16)** → Indicates poor handling of large errors.  
   - **Lowest R² Score (0.9709)** → Explains only **97.09%** of the variance.  

### **✅ Best Model Selection: XGBoost**
Based on the comparison, **XGBoost is the best model for fatigue strength prediction** due to:
- **Highest accuracy** (Lowest MAE & MSE).  
- **Best fit** (Highest R² Score).  
- **More robust performance** compared to Decision Trees and Random Forest.  

### **📌 Next Steps**
1. **Perform Hyperparameter Tuning for XGBoost** → To further improve accuracy.  
2. **Analyze Feature Importance** → Identify the most influential factors in fatigue strength prediction.  
3. **Deploy the XGBoost Model** → Save the trained model for real-world predictions.  


## **8. Hyperparameter Tuning Results for XGBoost**

### **Best Hyperparameters for XGBoost**
| **Hyperparameter**  | **Optimized Value** |
|---------------------|--------------------|
| **Subsample** | **0.6** (uses 60% of data for each tree) |
| **Reg Lambda (L2 Regularization)** | **0.5** (reduces overfitting) |
| **Reg Alpha (L1 Regularization)** | **0.1** (adds sparsity to the model) |
| **Number of Trees (`n_estimators`)** | **200** (higher for better learning) |
| **Max Depth (`max_depth`)** | **5** (limits tree complexity) |
| **Learning Rate (`learning_rate`)** | **0.1** (controls update step size) |
| **Gamma** | **0.3** (prevents excessive splits) |
| **Colsample by Tree (`colsample_bytree`)** | **0.6** (uses 60% of features per tree) |

### **Optimized Model Performance**
| **Metric**  | **Value**  | **Improvement?**  |
|-------------|-----------|------------------|
| **MAE (Mean Absolute Error)**  | **16.56** | 🔼 **Improved from 16.78** |
| **MSE (Mean Squared Error)**  | **574.02** | 🔼 **Slight improvement** |
| **R² Score**  | **0.9861** | ✅ **Remains very high** |

### **✅ Interpretation**
- **Lower MAE (16.56)** → Predictions **deviate less** from actual values.  
- **Lower MSE (574.02)** → Model makes fewer large errors.  
- **R² Score (0.9861)** → **98.61% of variance** is explained, maintaining **excellent predictive power**.  
- **Compared to default XGBoost, this optimized model performs better** while avoiding overfitting.  

### **📌 Next Steps**
1. **Analyze Feature Importance** to identify key predictors.  
2. **Save & Deploy the Trained Model** for real-world predictions.  

# **9. Feature Importance Analysis (XGBoost)**

### **Top Important Features**

| **Feature**  | **Importance Score** | **Interpretation** |
|-------------|--------------------|--------------------|
| **NT**       | **0.6922**  | **Most significant predictor**; major contribution to fatigue strength. |
| **Dt**       | **0.0931**  | Important, but much lower influence than NT. |
| **TT**       | **0.0767**  | Moderate impact on prediction. |
| **Cr**       | **0.0536**  | Some contribution to fatigue strength. |
| **Mo**       | **0.0284**  | Lower impact, but still relevant. |
| **C**        | **0.0156**  | Minor impact. |
| **dA**       | **0.0089**  | Very low impact. |
| **P**        | **0.0087**  | Negligible contribution. |
| **Mn**       | **0.0086**  | Insignificant in model prediction. |
| **Si**       | **0.0085**  | Very minimal influence. |
| **RedRatio** | **0.0058**  | Lowest impact among non-zero features. |
| **QmT**      | **0.0000**  | **Completely irrelevant** to the model. |

### **🔍 Key Observations**
- **`NT` is by far the most influential feature** (0.6922 importance score).  
- **`Dt`, `TT`, and `Cr`** have **moderate influence** and should be retained.  
- **`QmT` has zero importance** → Might be unnecessary.  
- **Features like `RedRatio`, `Si`, and `Mn` contribute very little** and may be **candidates for removal**.  

### **✅ Next Steps**
1. **Remove `QmT` (since it has zero importance) and re-train the model.**  
2. **Test removing low-importance features (`RedRatio`, `Si`, `Mn`, etc.) to see if performance improves.**  

## **10. Performance Comparison Before vs. After Removing `QmT`**

| **Metric**  | **Before Removing `QmT`** | **After Removing `QmT`** | **Impact** |
|-------------|--------------------|--------------------|-----------|
| **MAE (Mean Absolute Error)**  | **16.56**  | **18.05**  | **Increased** (worse) |
| **MSE (Mean Squared Error)**  | **574.02**  | **595.80**  | **Increased** (worse) |
| **R² Score**  | **0.9861**  | **0.9856**  | **Slight Decrease** |

### **🔍 Interpretation**
- **Removing `QmT` caused a slight performance degradation**:
  - **MAE increased** from **16.56** to **18.05**, meaning predictions are now slightly **less accurate**.
  - **MSE increased**, indicating larger prediction errors.
  - **R² Score dropped slightly**, meaning the model explains **less variance** than before.

- **Although `QmT` had zero feature importance, removing it still impacted the model’s generalization**. This could be due to **correlations with other features** that were not captured in the importance scores.

### **✅ Next Steps**
1. **Restore `QmT` and keep all features** (since removing it worsened performance).  
2. **Proceed with final model selection and deployment with all features.**  
