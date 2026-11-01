# Classification and Feature Selection Using Synthetic Gene-Labeled Data

## Overview

This project examines the effects of feature selection on supervised classification using a synthetic dataset generated with scikit-learn's `make_classification()`.

The dataset contains 500 observations, 100 numerical features, and three target classes. Of the 100 features, 20 were generated as informative and 10 as redundant. The features are assigned gene-style labels for illustrative purposes, but they do not represent actual RNA-seq measurements.

Four classifiers were evaluated using the complete feature set: Gaussian Naive Bayes, L1-regularized Logistic Regression, L2-regularized Logistic Regression, and Gradient Boosting. ANOVA F-test feature selection was then used to retain 20 features and compare the performance of Gaussian Naive Bayes and Gradient Boosting before and after feature selection.

The objective is to demonstrate preprocessing, feature selection, and model comparison in a controlled synthetic classification experiment.

---

## Key Results

| Model | All 100 Features | Selected 20 Features |
|---|---:|---:|
| Gaussian Naive Bayes | 61% | 64% |
| L1 Logistic Regression | 61% | Not evaluated |
| L2 Logistic Regression | 54% | Not evaluated |
| Gradient Boosting | 63% | 66% |

**Key findings:**

- ANOVA F-test feature selection reduced the predictor space from 100 features to 20.
- Gaussian Naive Bayes and Gradient Boosting each improved by three percentage points after feature selection.
- Gradient Boosting achieved the highest observed test accuracy at 66%.
- The selected features are simulated numerical variables, not validated biological biomarkers.

These results are based on a single stratified 80/20 train/test split, with 400 training observations and 100 held-out testing observations. The improvements are modest and may not generalize to other simulated datasets or real gene-expression measurements.

---

## Methods and Workflow

1. **Data generation:** Generate a three-class synthetic dataset using `make_classification()` with a fixed random seed.
2. **Data preparation:** Assign gene-style feature labels and create a stratified 80/20 train/test split.
3. **Scaling:** Fit `StandardScaler` on the training set and apply the fitted transformation to the test set.
4. **Baseline modeling:** Evaluate four classifiers using all 100 features.
5. **Feature selection:** Fit `SelectKBest` with an ANOVA F-test on the training data and retain the 20 highest-scoring features.
6. **Filtered modeling:** Retrain Gaussian Naive Bayes and Gradient Boosting using the selected features.
7. **Evaluation:** Compare held-out classification accuracy, examine confusion matrices, and visualize Gradient Boosting feature importances.

---

## Tools and Libraries

- Python 3
- JupyterLab / Jupyter Notebook
- scikit-learn
- pandas
- NumPy
- matplotlib
- seaborn
- Git and GitHub

---

## How to Run Locally

Clone the repository:

```bash
git clone https://github.com/stephfn/rna-seq-classification-pipeline.git
cd rna-seq-classification-pipeline
```

Install the main dependencies:

```bash
python -m pip install numpy pandas matplotlib seaborn scikit-learn jupyterlab
```

Launch JupyterLab:

```bash
jupyter lab
```

Open `Notebooks/synthetic_gene_feature_classification.ipynb` and select **Run All Cells**.

The notebook generates its own synthetic dataset, so no external data download is required.

**Note:** The corrected notebook is currently on the `rna-seq-cleanup` branch. The `main` branch will contain these updates after the cleanup pull request is merged.

---

## Limitations and Future Work

The experiment uses synthetic numerical features rather than actual RNA-seq measurements. It does not model biological expression distributions, sequencing depth, batch effects, or other technical variation found in real transcriptomic datasets.

The evaluation uses one train/test split, and the number of selected features was not optimized through cross-validation. Model comparisons should therefore be interpreted as exploratory.

Future work could include cross-validation with feature selection performed inside each training fold, evaluation on real TCGA or GEO gene-expression datasets, and batch-aware validation where appropriate.

---

## Repository Contents

- `Notebooks/synthetic_gene_feature_classification.ipynb`: Main synthetic classification and feature-selection analysis.
- `Notebooks/rna_seq_classifier_scratch.ipynb`: Earlier exploratory notebook.
- `Notebooks/Scripts/`: Supporting project scripts.

---

## Author

Stephanie Nord  
Master's Student in Data Science
