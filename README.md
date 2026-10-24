# Medication Adherence Prediction

A supervised machine learning project exploring how demographic, clinical, and insurance-related features can be used to predict medication adherence among patients with diabetes and/or hypertension.

Developed for **CMP466 (Fall 2025)** at the American University of Sharjah.

## Approach

Using a dataset of **24,084 records**, we:

1. Explored the data and prepared numerical and categorical features using ordinal encoding, log transformations, and standardization.
2. Trained and compared **K-Nearest Neighbors, Decision Trees, Gaussian and Bernoulli Naive Bayes, and Gradient Boosting**.
3. Evaluated models using an 80/20 stratified train/test split, cross-validation, feature selection, and PCA.

## Results

| Model | Accuracy | ROC-AUC |
| --- | ---: | ---: |
| K-Nearest Neighbors | 80.6% | 0.888 |
| Decision Tree | 81.5% | 0.894 |
| Gaussian Naive Bayes | 77.7% | 0.855 |
| Bernoulli Naive Bayes (feature selection) | 81.9% | 0.901 |
| **Gradient Boosting** | **82.0%** | **0.900** |

**Gradient Boosting achieved the highest reported accuracy** (82.0%) and an F1-score of **0.795**. Feature-selected Bernoulli Naive Bayes had a marginally higher ROC-AUC (0.9014 vs. 0.9003). Feature selection generally helped, while PCA tended to reduce performance.

*The table shows each model family’s highest reported accuracy across the evaluated variants. The Gradient Boosting baseline was independently rerun for this GitHub release, but the complete hyperparameter experiments were not rerun.*

## Repository structure

```text
.
├── data/
│   └── raw/
│       └── medication_adherence.xlsx
├── notebooks/
│   ├── 01_preprocessing.ipynb
│   └── 02_model_training.ipynb
├── .gitignore
├── README.md
└── requirements.txt
```

## Getting started

Install the Python dependencies from the repository root:

```bash
python -m pip install -r requirements.txt
jupyter lab
```

Run the notebooks **in order**:

1. `notebooks/01_preprocessing.ipynb` — explores and preprocesses the original dataset, creating `data/processed/preprocessed_dataset.csv`.
2. `notebooks/02_model_training.ipynb` — trains, tunes, and evaluates the classifiers.

The notebooks work when Jupyter is launched from either the repository root or the `notebooks/` directory. Some hyperparameter searches can take a while to run.

## Dataset

The dataset contains anonymized 2022 medical claims and patient-level records from **Cimas Medical Aid Society (Zimbabwe)** and was published by **Wellington Kanyongo, Tsitsi Moyo, Absalom El-Shamir Ezugwu, and Jean Vincent Fonou Dombeu**.

Source: [Mendeley Data — Medication Adherence Dataset (Version 2)](https://data.mendeley.com/datasets/zkp7sbbx64/2) (DOI: `10.17632/zkp7sbbx64.2`). This dataset is available under **CC0 1.0**. The original prepared spreadsheet is included for reproducibility; the generated CSV is not tracked.

## Team

- **Rayyan Agha Alnimer** — Data preprocessing, exploratory analysis, Gradient Boosting
- **Omar Aloruk** — K-Nearest Neighbors
- **Houssameddine Al Turk** — Decision Trees
- **Mohamad Zein** — Naive Bayes

Supervised by **Dr. Salam Dhou**.

> **Note:** This is an educational research project, not a clinically validated prediction tool. In the original workflow, scaling is fitted before the train/test split, which can introduce data leakage. The reported metrics should therefore be treated as exploratory rather than clinical performance estimates.
