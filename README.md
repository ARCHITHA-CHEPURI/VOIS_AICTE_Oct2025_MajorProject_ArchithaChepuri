# Netflix Content Analysis and Classification

## Overview

This project analyzes a Netflix titles dataset containing 7,789 records to explore content distribution, genres, countries, ratings, durations, and release-date trends. It combines Exploratory Data Analysis (EDA), feature engineering, data visualization, and machine learning classification to distinguish movies from TV shows.

The project uses Python-based data analysis and two classification algorithms: Logistic Regression and Random Forest.

## Objectives

- Analyze Netflix content distribution across movies and TV shows.
- Explore genre, country, rating, duration, and release-date patterns.
- Handle missing values and engineer features for machine learning.
- Train and evaluate classification models.
- Visualize model performance and identify influential features.

## Dataset

The dataset, `major project.csv`, contains 7,789 records and 11 original columns.

| Column | Description |
|---|---|
| `Show_Id` | Unique identifier for a title |
| `Category` | Movie or TV Show |
| `Title` | Title of the content |
| `Director` | Director information |
| `Cast` | Cast members |
| `Country` | Country or countries associated with the title |
| `Release_Date` | Date field provided in the dataset |
| `Rating` | Content rating |
| `Duration` | Runtime in minutes or number of seasons |
| `Type` | Genre and category descriptions |
| `Description` | Short content description |

## Technologies Used

- **Python** — Core programming language
- **Pandas and NumPy** — Data manipulation and feature engineering
- **Matplotlib and Seaborn** — Data visualization
- **Scikit-learn** — Machine learning pipelines, preprocessing, and evaluation
- **Google Colab** — Development and execution environment

## Project Workflow

### 1. Data Loading and Preprocessing

- Loaded the CSV dataset using Pandas.
- Standardized column names and converted the date field to datetime format.
- Examined dataset records and handled missing numerical values using median imputation.

### 2. Genre and Country Processing

- Extracted genre information from the `Type` column.
- Created genre lists and used keyword-based genre inference as a fallback when genre information was unavailable.
- Split country information into individual country entries.
- Created binary features for frequently occurring genres and countries.

**Note:** The keyword-based genre inference is only a heuristic. Existing genre information is retained when present.

### 3. Feature Engineering

Created numerical features for classification, including:

- `duration_num` — Numeric representation of duration
- `year_added` — Year derived from the provided date field
- `cast_len` — Number of cast entries
- `desc_len` — Length of the content description
- Genre and country indicator features
- Content rating features

### 4. Exploratory Data Analysis

Generated visualizations to investigate:

- Movies versus TV shows
- Content trends across years
- Genre trends over time
- Country-wise content distribution
- Feature importance in the Random Forest model

### 5. Machine Learning Models

Two classification algorithms were implemented using Scikit-learn pipelines.

**Logistic Regression**
- Used as a baseline classification model.
- Applied one-hot encoding to the rating feature.
- Evaluated using classification metrics and ROC-AUC.

**Random Forest Classifier**
- Trained using 400 decision trees.
- Used the engineered numerical and categorical indicator features.
- Evaluated using classification reports, confusion matrices, and feature importance.

The target variable is derived from the `Category` column and contains two classes: `Movie` and `TV Show`.

### 6. Model Evaluation

The code evaluates model performance using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC for Logistic Regression
- Confusion matrices
- Random Forest feature importance

The initial run reported approximately 97% accuracy for Logistic Regression and 100% for Random Forest. These are preliminary results from the current feature setup, not independently validated performance estimates.

**Important evaluation consideration:** Duration is strongly associated with the target category because TV shows are represented by seasons and movies by minutes. This can make classification artificially easy. Further validation and feature-leakage checks are needed before interpreting the Random Forest result as evidence of generalization.

## Visualizations

The project generates:

1. Movies versus TV shows trend chart
2. Top genre trends over time
3. Top countries by title count
4. Logistic Regression confusion matrix
5. Random Forest confusion matrix
6. Top 20 Random Forest feature importances

## How to Run

### Option 1: Google Colab

1. Open Google Colab.
2. Create a new notebook.
3. Upload `major project.csv` when prompted by the upload cell.
4. Install any missing dependencies if necessary.
5. Execute the notebook cells in order.

### Option 2: Run Locally

Clone your repository:

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

Place `major project.csv` in the working directory and run the notebook or Python script.

If using a Jupyter notebook locally, install Jupyter if necessary:

```bash
pip install notebook
jupyter notebook
```

## Future Improvements

- Investigate target leakage and evaluate models without duration-derived shortcuts.
- Add stratified cross-validation and compare cross-validation results.
- Improve missing-value handling and data-quality validation.
- Tune hyperparameters and compare additional classification algorithms.
- Explore text-based features from content descriptions.
- Add a structured analytical report with key findings and limitations.
- Introduce SQL-based analysis if the dataset is migrated to a relational database.

## Conclusion

This project demonstrates an end-to-end data analysis and machine learning workflow, from CSV ingestion and preprocessing to feature engineering, classification, evaluation, and visualization. It provides a foundation for understanding content catalog patterns and applying supervised learning to structured datasets.

## Author

**Architha Chepuri**

Computer Science and Technology Undergraduate

