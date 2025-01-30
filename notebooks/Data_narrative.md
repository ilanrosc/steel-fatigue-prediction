# Data Narrative for Steel Fatigue Strength Prediction

## 📌 What is Fatigue Strength?
- Fatigue strength refers to a material's ability to withstand **repeated stress cycles** without failing.
- In **automotive, aerospace, and construction industries**, materials must endure continuous stress variations. Predicting fatigue strength helps in **selecting the right steel composition** for durability and cost-effectiveness.

---

## 📊 Dataset Overview
We have a dataset that contains **chemical composition, processing conditions, and mechanical properties** of steel samples. The goal is to **predict fatigue strength**, a critical mechanical property.

### 📉 Key Aspects of the Dataset
| Feature Type | Examples | Description | Possible Influence on Strength |
|-------------|---------|-------------|--------------------------------|
| **Chemical Composition** | C, Si, Mn, P, S, Cr, Ni | Percentage of each element in steel | Different elements impact hardness, ductility, and toughness |
| **Processing Parameters** | Heat Treatment, Cooling Rate | How the steel was processed | Can influence grain structure and material durability |
| **Mechanical Properties** | Yield Strength, Hardness | Physical characteristics of steel | Strong correlation with fatigue strength |
| **Target Variable** | Fatigue Strength | The property we aim to predict | Determines how well the steel resists cyclic stress |

## Details
#### **Chemical Composition**
- Represents the percentage of various elements in the steel, affecting hardness, ductility, and toughness.
- Certain elements, such as **Carbon (C)** and **Chromium (Cr)**, can increase strength but may also reduce ductility.
- Other elements influence corrosion resistance, machinability, or thermal stability.

| Abbreviation | Description |
|-------------|-------------|
| C  | % Carbon |
| Si | % Silicon |
| Mn | % Manganese |
| P  | % Phosphorus |
| S  | % Sulphur |
| Ni | % Nickel |
| Cr | % Chromium |
| Cu | % Copper |
| Mo | % Molybdenum |

#### **Processing Parameters**
- Define how the steel is treated to modify its mechanical properties.
- Heat treatments, cooling rates, and diffusion times influence the final grain structure and stress resistance.
- A higher **Tempering Temperature (TT)** may reduce hardness but improve toughness.

| Abbreviation | Description |
|-------------|-------------|
| NT   | Normalizing Temperature |
| THT  | Through Hardening Temperature |
| THt  | Through Hardening Time |
| THQCr | Cooling Rate for Through Hardening |
| CT   | Carburization Temperature |
| Ct   | Carburization Time |
| DT   | Diffusion Temperature |
| Dt   | Diffusion Time |
| QmT  | Quenching Media Temperature (for Carburization) |
| TT   | Tempering Temperature |
| Tt   | Tempering Time |
| TCr  | Cooling Rate for Tempering |

#### **Mechanical Properties**
- Physical characteristics that determine the steel's structural performance.
- **Reduction Ratio (RedRatio)** affects grain refinement and strength.

| Abbreviation | Description |
|-------------|-------------|
| RedRatio | Reduction Ratio (Ingot to Bar) |

#### **Inclusion Properties**
- Describe the distribution of inclusions (impurities) in the steel.
- Inclusions can impact fatigue life by acting as stress concentration points.
- A higher proportion of **isolated inclusions (dC)** may negatively affect material integrity.

| Abbreviation | Description |
|-------------|-------------|
| dA | Area Proportion of Inclusions Deformed by Plastic Work |
| dB | Area Proportion of Inclusions Occurring in Discontinuous Array |
| dC | Area Proportion of Isolated Inclusions |

#### **Target Variable**
- The **dependent variable** that we aim to predict.
- A higher **Fatigue Strength (Fatigue)** means better resistance to cyclic stress failures.

| Abbreviation | Description |
|-------------|-------------|
| Fatigue | Rotating Bending Fatigue Strength (10^7 Cycles) |

---

## 🎯 Key Questions for Analysis
1. **How do different chemical compositions influence fatigue strength?**
   - Do certain elements (like **carbon or chromium**) significantly improve durability?
2. **How do processing conditions affect strength?**
   - Does **heat treatment** or **cooling rate** play a major role?
3. **What are the most influential features for prediction?**
   - Are there strong correlations with **yield strength, hardness, or specific elements**?
4. **Are there any missing or inconsistent values?**
   - Need to handle missing data before modeling.

---

## 🔬 Next Step: Exploratory Data Analysis (EDA)
Now that we understand the dataset's context, the next step is to:
1. Load the data and inspect **rows, columns, and data types**.
2. Identify **missing values and outliers**.
3. Analyze **correlations and distributions**.

The results of EDA will be documented in `EDA.md`.

