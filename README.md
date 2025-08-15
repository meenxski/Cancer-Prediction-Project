# Cancer Survival Prediction Analysis
This repository contains the code and findings for a machine learning project aimed at predicting cancer patient survival. The analysis leverages a clinical dataset to clean data, engineer relevant features, and train several classification models. A key focus of the project is addressing the severe class imbalance in the target variable through the SMOTE technique, ultimately leading to the selection of a Random Forest model with strong predictive capabilities, particularly a high recall for patient survival.

-----

## **Table of Contents**

  - [Methodology](https://www.google.com/search?q=%23methodology)
  - [Data Fields](https://www.google.com/search?q=%23data-fields)
  - [How to Reproduce](https://www.google.com/search?q=%23how-to-reproduce)
  - [Model Comparison](https://www.google.com/search?q=%23model-comparison)
  - [Analytical Insights](https://www.google.com/search?q=%23analytical-insights)
  - [Future Enhancements](https://www.google.com/search?q=%23future-enhancements)

-----

## **Methodology**

The analysis followed a standard machine learning pipeline:

1.  **Data Cleaning & Preparation**: The initial phase involved loading the dataset, imputing missing values using median/mode, and correcting outliers for features like `age`, `bmi`, and `cholesterol_level`.
2.  **Feature Engineering**: A new, highly predictive feature, `treatment_duration`, was created by calculating the difference between the `end_treatment_date` and `diagnosis_date`.
3.  **Exploratory Data Analysis (EDA)**: Key variables were visualized to understand their distributions and relationships. This included analyzing the correlations between numerical features.
4.  **Preprocessing**: Numerical features were scaled with `StandardScaler`, and categorical features were converted into a machine-readable format using one-hot encoding.
5.  **Addressing Class Imbalance**: The SMOTE (Synthetic Minority Over-sampling Technique) was applied to the training set to correct for the imbalanced nature of the `survived` target variable.
6.  **Model Training**: Four distinct classifiers were trained and evaluated:
      * Logistic Regression
      * Random Forest
      * Gradient Boosting
      * XGBoost
7.  **Evaluation**: Models were assessed on a suite of metrics including Accuracy, Precision, Recall, F1-score, and ROC-AUC. The Random Forest classifier was ultimately selected as the best model.

-----

## **Data Fields**

The project utilizes the `cancer_stage_data.csv` dataset, which includes the following information:

  * **ID**: A unique identifier for each patient.
  * **age**: The patient's age at the time of diagnosis.
  * **gender**: The patient's gender.
  * **country**: The patient's country of residence.
  * **diagnosis\_date**: The date of the initial cancer diagnosis.
  * **cancer\_stage**: The diagnosed stage of the cancer (e.g., Stage I, Stage IV).
  * **family\_history**: Indicates if the patient has a family history of cancer.
  * **smoking\_status**: The patient's smoking habits.
  * **bmi**: The patient's Body Mass Index.
  * **cholesterol\_level**: The patient's cholesterol level.
  * **hypertension**: Indicates the presence of hypertension.
  * **asthma**: Indicates the presence of asthma.
  * **cirrhosis**: Indicates the presence of cirrhosis.
  * **other\_cancer**: Indicates the presence of other cancers.
  * **treatment\_type**: The primary type of treatment administered.
  * **end\_treatment\_date**: The date treatment was completed.
  * **survived**: The target variable, indicating if the patient survived (1) or not (0).

-----

## **How to Reproduce**

To replicate this analysis, clone this repository and ensure the necessary Python libraries are installed.

1.  **Prerequisites**:

      * Python 3.7+
      * Jupyter Notebook (or another Python IDE)

2.  **Install Dependencies**:

    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn
    ```

3.  **Run the Analysis**:
    Ensure the `cancer_stage_data.csv` file is in the root directory. Execute the primary script (`cancer_survival_analysis.py`) from your terminal:

    ```bash
    python cancer_survival_analysis.py
    ```

    The script will run the full pipeline and save the resulting visualizations as PNG files in the project directory.

-----

## **Model Comparison**

The table below summarizes the performance of each model on the test set after applying SMOTE. The Random Forest model provided the best balance of metrics, especially in ROC-AUC and Recall.

| Model               | Accuracy | Precision | Recall | F1-score | ROC-AUC |
| ------------------- | -------- | --------- | ------ | -------- | ------- |
| Logistic Regression | 0.69     | 0.38      | 0.68   | 0.49     | 0.74    |
| **Random Forest** | **0.76** | **0.45** | **0.70** | **0.55** | **0.78**|
| Gradient Boosting   | 0.73     | 0.42      | 0.70   | 0.52     | 0.77    |
| XGBoost             | 0.75     | 0.44      | 0.68   | 0.53     | 0.76    |

-----

## **Analytical Insights**

This analysis provided several important insights into the factors that influence cancer survival.

#### **1. Model Performance Overview**

After balancing the dataset, the Random Forest classifier emerged as the superior model, demonstrating a robust ability to handle both precision and recall.
\*\*

#### **2. In-Depth Look at the Random Forest Model**

The confusion matrix for the Random Forest model shows its strong performance in correctly classifying both survivors and non-survivors. A recall of 0.70 for the 'Survived' class is a key result, as it is a critical metric for success in medical diagnostic models.
\*\*

#### **3. Key Predictors of Survival**

A feature importance analysis identified the most influential variables for predicting patient outcomes.

  * The engineered feature, **`treatment_duration`**, was the most significant predictor.
  * Clinical health indicators like **`cholesterol_level`**, **`bmi`**, and **`age`** were also strong predictors.
  * The **`cancer_stage`** at diagnosis was confirmed to be a critical factor.
    \*\*

-----

## **Future Enhancements**

  * **Hyperparameter Optimization**: Conduct a more thorough hyperparameter search using methods like GridSearchCV or RandomizedSearchCV to further refine the Random Forest model's performance.
  * **Advanced Feature Creation**: Investigate more complex feature interactions (e.g., the relationship between `age` and `cancer_stage`).
  * **Explore Alternative Algorithms**: Test other powerful models such as LightGBM or CatBoost, which are known for their high performance.
  * **Model Interpretability**: Employ techniques like SHAP (SHapley Additive exPlanations) to better understand the model's decision-making process for individual predictions.
