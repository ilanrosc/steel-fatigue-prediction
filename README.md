# Steel Fatigue Strength Prediction

## 📝 Project Overview
This project aims to build a predictive model for estimating the fatigue strength of steel based on its chemical composition and processing parameters. The goal is to understand the factors that influence material strength and apply machine learning techniques to predict performance under cyclic loads.

## 📊 Dataset Description
The dataset contains information on:
- **Chemical Composition**: Elements like Carbon (C), Silicon (Si), Manganese (Mn), etc.
- **Processing Parameters**: Heat treatment, cooling rate, etc.
- **Target Variable**: Fatigue strength of steel.

**Data Source**: [Steel Fatigue Strength Dataset (Kaggle)](https://www.kaggle.com/datasets/chaozhuang/steel-fatigue-strength-prediction/data)

## 🎯 Objectives
1. Perform **Exploratory Data Analysis (EDA)** to understand the dataset.
2. Engineer meaningful features to improve model accuracy.
3. Build and compare multiple **regression models**.
4. Explain the model's predictions using **feature importance** techniques.

## 🚀 Getting Started

### Prerequisites
- Python 3.x
- Git

### Installation
1. **Clone the repository:**
   ```bash
   git clone https://github.com/ilanrosc/steel-fatigue-prediction.git
   cd steel-fatigue-prediction
   ```

2. **Set up a virtual environment (optional but recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate   # On macOS/Linux
   venv\Scripts\activate      # On Windows
   ```

3. **Install required packages:**
   ```bash
   pip install -r requirements.txt
   ```

## 📂 Usage

1. Download the dataset from Kaggle and place it in the `data/` folder.
2. Open Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
3. Explore and run the notebooks in the `notebooks/` directory.

## 📝 Project Structure
```
steel-fatigue-prediction/
│── data/                  # Raw dataset
│── documentation/         # All .md documentation files
│── notebooks/             # Jupyter Notebooks
│── README.md              # Project overview
│── requirements.txt       # Python dependencies
│── .gitignore             # Ignored files
│── LICENSE                # MIT License
```

## 📈 Results and Findings
Key findings and model performance metrics are documented in `documentation/` folder.

## 📬 Contact
For any inquiries, please reach out to [ilana.roscina@gmail.com].

## 📝 License
This project is licensed under the MIT License.

