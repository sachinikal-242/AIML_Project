# 2026-Y2-S1-MLB-B13G2-02

## IT2011 -- Artificial Intelligence and Machine Learning

### Progress Review I -- Data Preprocessing and Exploratory Data Analysis

## Project Overview

This project contains the group preprocessing and exploratory data
analysis work for the **Medical Insurance Dataset**. The work is
organized into six individual preprocessing contributions and one
integrated group preprocessing pipeline.

The group pipeline applies the preprocessing techniques sequentially and
produces processed training, testing, and combined datasets for later
model-development work.

## Dataset

The raw dataset is stored at:

`data/raw/insurance.csv`

The dataset contains the following variables:

  Feature      Description
  ------------ ------------------------------
  `age`        Age of the insured person
  `sex`        Sex of the insured person
  `bmi`        Body Mass Index
  `children`   Number of dependent children
  `smoker`     Smoking status
  `region`     Residential region
  `charges`    Medical insurance charges

`charges` is retained as the target variable for later predictive
modelling.

## Group Member Contributions

  -----------------------------------------------------------------------
  Member                  Student ID              Preprocessing Technique
  ----------------------- ----------------------- -----------------------
  Member 1                IT25100065              Missing value
                                                  detection/handling and
                                                  duplicate removal

  Member 2                IT25102316              Outlier detection and
                                                  handling using IQR

  Member 3                IT25100060              Categorical variable
                                                  encoding using One-Hot
                                                  Encoding

  Member 4                IT25102313              Feature engineering
                                                  using an Age-BMI
                                                  interaction feature

  Member 5                IT25100050              Correlation-based
                                                  exploratory feature
                                                  selection

  Member 6                IT25102309              Train-test split and
                                                  feature scaling using
                                                  StandardScaler
  -----------------------------------------------------------------------

## Preprocessing Workflow

The integrated `group_pipeline.ipynb` follows this sequence:

1.  Load the original medical insurance dataset.
2.  Check missing values and remove duplicate records.
3.  Detect BMI outliers using the Interquartile Range (IQR) method and
    cap extreme BMI values at the calculated boundaries.
4.  Convert `sex`, `smoker`, and `region` into numerical features using
    One-Hot Encoding.
5.  Create an `Age-BMI` interaction feature.
6.  Examine feature relationships with `charges` and perform
    correlation-based exploratory feature selection.
7.  Split the dataset into 80% training data and 20% testing data.
8.  Standardize continuous numerical predictors using `StandardScaler`.
9.  Fit the scaler only on the training data and use the fitted scaler
    to transform the testing data.
10. Save the final processed datasets.

## Exploratory Data Analysis

The repository contains EDA visualizations produced by the individual
members and the group pipeline, including:

-   Insurance charges distribution
-   BMI boxplot before outlier handling
-   BMI boxplot after outlier handling
-   Smoker vs. insurance charges
-   Age-BMI interaction vs. insurance charges
-   Feature correlation matrix
-   Age distribution before scaling
-   Age distribution after scaling
-   Group pipeline correlation matrix

The visualizations are stored in:

`results/eda_visualizations/`

## Project Structure

``` text
2026-Y2-S1-MLB-B13G2-02/
│
├── README.md
├── requirements.txt
├── .gitignore
├── group_pipeline.ipynb
│
├── data/
│   └── raw/
│       └── insurance.csv
│
├── notebooks/
│   ├── Member1_IT25100065_Missing_Duplicates.ipynb
│   ├── Member2_IT25102316_Outliers.ipynb
│   ├── Member3_IT25100060_Encoding.ipynb
│   ├── Member4_IT25102313_Feature_Engineering.ipynb
│   ├── Member5_IT25100050_Feature_Selection.ipynb
│   └── Member6_IT25102309_Scaling.ipynb
│
└── results/
    ├── eda_visualizations/
    │   ├── group_pipeline_correlation_matrix.png
    │   ├── member1_charges_distribution.png
    │   ├── member2_bmi_before.png
    │   ├── member2_bmi_after.png
    │   ├── member3_smoker_vs_charges.png
    │   ├── member4_age_bmi_vs_charges.png
    │   ├── member5_correlation_matrix.png
    │   ├── member6_age_before_scaling.png
    │   └── member6_age_after_scaling.png
    │
    └── outputs/
        ├── member1_cleaned.csv
        ├── member2_outlier_handled.csv
        ├── member3_encoded.csv
        ├── member4_feature_engineered.csv
        ├── member5_feature_selected.csv
        ├── member6_scaled.csv
        ├── insurance_train_processed.csv
        ├── insurance_test_processed.csv
        └── insurance_processed.csv
```

## Individual Notebooks

### Member 1 -- Missing Values and Duplicates

Checks the dataset for incomplete observations and duplicate records.
Duplicate records are removed before later preprocessing. The notebook
also includes an EDA visualization of the insurance charges
distribution.

### Member 2 -- Outlier Detection and Handling

Uses the IQR method to identify potential BMI outliers. Extreme BMI
observations are capped at the calculated IQR boundaries instead of
deleting complete customer records. Before-and-after BMI boxplots are
included.

### Member 3 -- Categorical Encoding

Applies One-Hot Encoding to categorical variables because the categories
do not have a natural ordinal relationship. A smoker vs. charges
visualization is included to explore the importance of smoking status.

### Member 4 -- Feature Engineering

Creates an Age-BMI interaction feature by combining `age` and `bmi`. The
notebook examines the relationship between the engineered feature and
insurance charges.

### Member 5 -- Feature Selection

Uses Pearson correlation as an exploratory feature-selection method. An
absolute correlation threshold of `0.05` is used as a simple exploratory
rule. Low Pearson correlation is not treated as proof that a feature is
useless, because nonlinear or interaction-based relationships may still
exist.

### Member 6 -- Feature Scaling

Splits the data into training and testing sets before scaling.
`StandardScaler` is fitted only on the continuous training features, and
the same learned transformation is applied to the testing data to avoid
data leakage.

## Group Pipeline

`group_pipeline.ipynb` integrates all six member contributions into one
sequential preprocessing workflow.

The pipeline preserves the train-test split and generates:

-   `insurance_train_processed.csv`
-   `insurance_test_processed.csv`
-   `insurance_processed.csv`

These files are stored under `results/outputs/`.

## Requirements

The project uses Python and common data-science libraries. Install the
required dependencies using:

``` bash
python -m pip install -r requirements.txt
```

For Google Colab, most required libraries are already available.

## How to Run

### Google Colab

1.  Open Google Colab.
2.  Upload the required notebook.
3.  Upload or make the `insurance.csv` dataset available using the
    expected path.
4.  Run all notebook cells from top to bottom.
5.  Review the code outputs, EDA visualizations, and interpretations.

### Jupyter Notebook / VS Code

1.  Open the project folder.
2.  Install the dependencies from `requirements.txt`.
3.  Open the required `.ipynb` file.
4.  Select the correct Python/Jupyter kernel.
5.  Run all cells from top to bottom.

For the complete group workflow, run:

`group_pipeline.ipynb`

## Outputs

Intermediate member outputs and final processed datasets are available
in:

`results/outputs/`

EDA charts are available in:

`results/eda_visualizations/`

## Conclusion

The project integrates six preprocessing contributions into a single
logical workflow. It covers data-quality checks, duplicate removal,
IQR-based outlier handling, categorical encoding, feature engineering,
exploratory correlation-based feature selection, train-test splitting,
and feature standardization. The resulting processed datasets provide
the prepared inputs for subsequent machine-learning model development.
