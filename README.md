"# High-Dimensional RNA-Seq Classification Pipeline" 
# 🧬 High-Dimensional RNA-Seq Classification & Feature Selection Pipeline

## Overview
In high-dimensional transcriptomics (P >> N), high feature noise can easily cause standard classification models to collapse toward random guessing. This project establishes an end-to-end Python pipeline to benchmark baseline probabilistic classifiers, regularized estimators (L1/L2), and non-linear tree ensembles across noisy vs. feature-selected expression spaces.

---

## 📊 Key Results & Key Takeaways

| Pipeline Strategy | Model Architecture | Accuracy | Key Observation |
| :--- | :--- | :--- | :--- |
| **Unfiltered High Noise** | Gaussian Naive Bayes | **32.00%** | Model collapsed under background noise ($P \gg N$). |
| **Unfiltered High Noise** | Random Forest | **23.00%** | Tree splits overfit to noisy random features. |
| **Full Feature Regularization** | $L_2$ (Ridge) Logistic Regression | **40.00%** | Ridge penalty shrank noise weights, preserving small collective signals. |
| **ANOVA $F$-Test Filtered** | Gaussian Naive Bayes | **64.00%** | Removing noise restored probabilistic classification accuracy. |
| **ANOVA $F$-Test Filtered** | Gradient Boosting | **66.00%** | Isolated biomarker features enabled non-linear boundary learning. |

* **Dimensionality Reduction is Essential:** Filtering out background noise boosted classification accuracy from baseline levels up to **66%**.
* **Model Robustness:** Tree ensembles (Gradient Boosting) captured non-linear co-expression relationships between gene features far better than linear/naive models.

---

## 🛠️ Stack & Methods

* **Language & Environment:** Python 3, Jupyter Notebook
* **ML Frameworks:** `scikit-learn` (`GaussianNB`, `LogisticRegression`, `GradientBoostingClassifier`, `SelectKBest`, `StandardScaler`)
* **Data & Visualization:** `pandas`, `numpy`, `matplotlib`, `seaborn`
* **Version Control:** Git, GitHub

---

## 🚀 How to Run Locally

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/stephfn/rna-seq-classification-pipeline.git](https://github.com/stephfn/rna-seq-classification-pipeline.git)
   cd rna-seq-classification-pipeline
