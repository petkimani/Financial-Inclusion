# Financial Inclusion in Africa

A machine learning project that predicts whether an individual in East Africa is likely to have or use a bank account, based on demographic and socioeconomic survey data. Built as part of the Zindi "Financial Inclusion in Africa" challenge.

## Overview

Financial inclusion means that individuals and businesses have access to useful, affordable financial products and services — transactions, payments, savings, credit, and insurance — delivered responsibly and sustainably. This project explores survey data from Kenya, Rwanda, Tanzania, and Uganda to understand which demographic factors are associated with bank account ownership, and builds classification models to predict it.

## Dataset

The dataset contains demographic information and financial service usage for approximately 33,600 individuals across East Africa.

| Column | Description |
|---|---|
| `country` | Country of the respondent |
| `year` | Survey year |
| `uniqueid` | Unique respondent identifier |
| `bank_account` | Target variable — whether the respondent has a bank account (Yes/No) |
| `location_type` | Rural or Urban |
| `cellphone_access` | Whether the respondent has access to a cellphone |
| `household_size` | Number of people in the household |
| `age_of_respondent` | Age of the respondent |
| `gender_of_respondent` | Male or Female |
| `relationship_with_head` | Relationship to the head of household |
| `marital_status` | Marital status |
| `education_level` | Highest level of education attained |
| `job_type` | Type of employment |

## Workflow

1. **Data exploration** — inspect structure, generate an automated profiling report (`ydata-profiling`), and review summary statistics.
2. **Data cleaning** — check for and handle missing values and duplicates; drop non-predictive identifier columns (`country`, `year`, `uniqueid`).
3. **Exploratory visualization** — distribution of location type, bank account ownership, education level vs. bank account, age, and household size using Plotly, Seaborn, and Matplotlib.
4. **Outlier handling** — detect and remove outliers in numeric columns (`household_size`, `age_of_respondent`) using the IQR method.
5. **Feature encoding** — binary map categorical features (`bank_account`, `location_type`, `cellphone_access`, `gender_of_respondent`) and label-encode multi-class categorical features (`relationship_with_head`, `marital_status`, `education_level`, `job_type`).
6. **Modeling**
   - Decision Tree Classifier (with Gini impurity–based feature importance)
   - Random Forest Classifier
   - 5-fold cross-validation
7. **Evaluation** — accuracy score and classification report (precision, recall, F1) for both models, with a final accuracy comparison.

## Models

| Model | Notes |
|---|---|
| Decision Tree | `max_depth=4`, `criterion='gini'`, `min_samples_split=10` |
| Random Forest | `n_estimators=100`, `max_depth=4`, `criterion='gini'` |

Both models are trained on an 80/20 train-test split (`random_state=42`) and evaluated on held-out test data.

## Tech Stack

- **Python**
- **pandas** — data manipulation
- **ydata-profiling** — automated exploratory data analysis
- **scikit-learn** — modeling (Decision Tree, Random Forest), train/test split, cross-validation, metrics
- **Matplotlib / Seaborn / Plotly** — data visualization



## Data Source

Dataset provided by the [Zindi](https://zindi.africa/) platform as part of the Financial Inclusion in Africa challenge.

## License

This project is for educational purposes.
