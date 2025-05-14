# CIS890

# 📊 'Race and Gender Inference in Mortgage Lending: A Machine Learning Fairness Analysis' Pipeline

This repository contains a modular, step-by-step pipeline for preprocessing mortgage loan data, performing classification, feature selection, evaluating fairness, and visualizing dimensionality reduction. The project is structured into multiple Jupyter notebooks organized across preprocessing, classification, feature selection, fairness analysis, and clustering.

---

## 🧭 Pipeline Overview

### 1. 📂 Data Merging and Initial Analysis
**Notebook:** `Data_MergeAndAnalysis.ipynb`

- **Cell 1**: Standardizes column names across multiple years using `Feature_comparison.xlsx` for consistency.
- **Cell 2**: Loads all yearly CSVs from `./Yearly/`, merges them, and exports the full dataset as a single CSV file.  
- **Output:** `Data/merged_data.csv`
- Remaining cells are for exploratory analysis (optional).

---

### 2. 🧼 Data Cleaning and Preprocessing  
**Notebook:** `Data_PreProcessing.ipynb`

- **Cell 1**: Handles missing value removal.  
  ➤ Output: `Data/merged_data_dropped.csv`

- **Cell 2**: General preprocessing and feature formatting.  
  ➤ Output: `Data/Cleaned_data.csv`

- **Cells 3–4**: Adjusts monetary features for inflation.  
  ➤ Output: `Data/Cleaned_data_Inflation_Adjusted.csv`

- **Cells 5–6**: One-hot encoding and normalization *(optional – handled during model training if needed)*

---

### 3. 🤖 Classification & Sampling  
**Notebook:** `Classification/Classification.ipynb`

- Samples the data for each target variable and saves:
  - `Samples/BoGender.csv`
  - `Samples/BoRace.csv`
  - `Samples/CoGender.csv`
  - `Samples/CoRace.csv`

- Performs:
  - Train/test split classification
  - Cross-validation classification

- **Results saved in folders:**
  - `{Target}_SPLIT/`
  - `{Target}_CV/`

---

### 4. 🧠 Feature Selection  
**Notebook:** `Classification/Feature_Selection.ipynb`

- Uses **RFECV (Recursive Feature Elimination with Cross-Validation)** for feature selection.
- **Output folders:**
  - `{Target}_RFECV/`

---

### 5. ⚖️ Fairness Analysis  
**Notebook:** `Classification/Fairness.ipynb`

- Evaluates fairness for each target using metrics like demographic parity, equal opportunity, etc.
- Outputs:
  - `{Target}_Fairness.csv`
  - `{Target}_Fairness_Plot.png`

---

### 6. 🔍 Dimensionality Reduction (PCA)  
**Notebook:** `Clustering/Clustering.ipynb`

- Applies **Principal Component Analysis (PCA)** to visualize high-dimensional data.
- **Output:**
  - `{Target}_pca.png`

```

## 📁 Folder Structure

├── Data/                         # Cleaned and merged datasets
│   ├── merged_data.csv
│   ├── merged_data_dropped.csv
│   ├── Cleaned_data.csv
│   ├── Cleaned_data_Inflation_Adjusted.csv
│
├── Classification/Samples/       # Sampled datasets for each target
│   ├── BoGender.csv
│   ├── BoRace.csv
│   ├── CoGender.csv
│   └── CoRace.csv
│
├── Classification/
│   ├── Classification.ipynb
│   ├── Feature_Selection.ipynb
│   └── Fairness.ipynb
│
├── Clustering/
│   └── Clustering.ipynb
│
├── Yearly/                       # Raw yearly CSVs (input)
│
├── Feature_comparison.xlsx       # Reference for standardizing column names
├── Data_MergeAndAnalysis.ipynb
└── Data_PreProcessing.ipynb


```

1. Run: Data_MergeAndAnalysis.ipynb
2. Run: Data_PreProcessing.ipynb
3. Run: Classification/Classification.ipynb
4. Run: Classification/Feature_Selection.ipynb
5. Run: Classification/Fairness.ipynb
6. Run: Clustering/Clustering.ipynb



