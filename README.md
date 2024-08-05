# COVID-19 Severity and Mortality Risk Prediction

## Table of Contents
- [COVID Severity and Mortality Analysis Dashboard Initial Setup](#covid-severity-and-mortality-analysis-dashboard-initial-setup)
- [Introduction and Problem Definition](#introduction-and-problem-definition)
- [Proposed Method](#proposed-method)
- [Algorithm](#algorithm)
- [Experiments and Evaluation](#experiments-and-evaluation)
- [Conclusions & Discussion](#conclusions--discussion)
- [Example Images](#example-images)
- [Project Infom]

## Introduction and Problem Definition

### Objective

Our goal is to create a predictive model for assessing COVID-19 severity and mortality risk using the Kaggle Mexican patient COVID-19 dataset. We will evaluate COVID-19 severity and mortality by examining patient records to determine the extent of medical interventions required, such as hospitalization, ICU admission, intubation, and mortality. Additionally, this investigation will explore whether specific demographics or underlying health conditions correlate with a higher risk of severe COVID-19 outcomes.

Model development will be done in Python, exploring multiple models to select the most accurate one. Tableau will be used for interactive visualization, providing insights and enabling real-time outcome simulations for patients. Our approach ensures a comprehensive understanding of the influence of patient data, including health conditions, on COVID-19 outcomes.

### Current Methodology & Limitations

According to Cascella (2020), COVID-19 caused over 6 million deaths in 2020. Despite the availability of vaccines, persistent outbreaks due to mutant variants necessitate real-time diagnostics. Current severity assessments rely on symptom monitoring, health analysis, clinical evaluations, and PCR tests. Berlin's research highlights the importance of prompt treatment for severe COVID-19 to avoid negative outcomes. However, limitations arise from Cascella's lack of live predictions and Berlin's focus on only pulmonary complications. Our work addresses these gaps by innovatively assessing a wider range of conditions and patient information, providing live outputs.

## Proposed Method

Our model leverages a comprehensive dataset and advanced machine learning techniques to capture complex factors contributing to severe outcomes. This allows our model to surpass the predictive capabilities of traditional diagnostic tools. Real-time predictions enable prompt interventions, potentially saving lives by effectively targeting high-risk individuals. Our approach introduces several innovative features not identified in existing literature, including:

- COVID-19 Severity Prediction
- Advanced Visualization
- Patient Risk Simulation

We believe that our approach surpasses the state-of-the-art by addressing current limitations and introducing innovative features. Current models primarily focus on COVID-19 diagnosis or mortality prediction. By shifting the focus to predicting COVID-19 severity and incorporating outcomes such as hospitalization, ICU admission, intubation, and mortality, our approach offers a more holistic understanding of disease progression and patient outcomes.

Additionally, our focus on advanced visualizations and real-time simulation within Tableau integrates both descriptive and predictive analytics. These capabilities address critical gaps in existing models, which often only offer descriptive insights. As a result, healthcare professionals will be equipped with actionable insights via a user-friendly interface that can be implemented in healthcare settings to support COVID-19 patient management.

## Algorithm

A Random Forest model was built in Python to predict patients at high risk of needing medical interventions based on underlying health data and age. The algorithm work consisted of three main steps:

### Data Preparation

- New feature columns were generated, including ones for patient death, COVID-19 status, and the sum of comorbidities.
- A binary "AT_RISK" variable was created to identify high-risk COVID-19 patients based on their outcomes (ICU, hospitalization, intubation, death).
- Missing data for health conditions were removed, and columns were converted into binary format to aid modeling.

### Model Development

- The model was iteratively improved and validated through rigorous testing to ensure a framework capable of accurately predicting COVID-19 risk.
- To optimize our model, we refined the representation of influential features, particularly age into one-hot encoded columns, and removed 5 non-influential columns.
- Our final model had an accuracy of ~66% and used patient gender, age, and 7 health conditions to generate predictions for at-risk patients.

### Model Deployment

- The final trained Random Forest model (deployed via TabPY), along with two datasets created during model development, were used to create a complex interactive Tableau dashboard.

## Experiments and Evaluation

### Random Forest Model Testing

For initial data modeling, we employed the `RandomForestClassifier` model, using the 'AT_RISK' column as the target, and all dataset columns as features. A patient was defined as at risk if they met any of the conditions for ICU, Death, and intubation when testing positive for COVID-19. The dataset was partitioned into training (70%) and testing (30%) sets. The initial model achieved an accuracy of approximately 61.45%.

Our experimental framework used a randomly selected subset comprising 50% of the original dataset to maximize variability and representativeness. The primary goal was to identify significant features impacting the 'AT_RISK' status and evaluate the model's predictive accuracy. We conducted five iterations of the random forest model, each with a different 50% sample. The average accuracy was approximately 61.80%, with a standard deviation of 0.17%.

### Feature Importance Analysis

The feature importance analysis identified key predictors by encoding categorical variables into numerical formats compatible with the RandomForest algorithm. 'AGE' and 'PNEUMONIA' were the most influential features, with importance scores of 50.9% and 27.8%, respectively. Other features like 'NUM_COMORBIDITIES', 'SEX', and 'DIABETES' also contributed significantly.

### Improving the Random Forest Model

To address the high feature importance score for 'AGE', we categorized age into decades (e.g., '10s', '20s') to reduce its overwhelming impact. We also streamlined the model by dropping features with minimal impact, like 'INMSUPR', 'ASTHMA', 'TOBACCO', 'COPD', and 'OTHER_DISEASE', now represented in the 'NUM_COMORBIDITIES' column. These refinements led to a significant improvement in the model's performance, increasing the average accuracy to 66%, a 4% improvement over the previous model.

### Multilayer Perceptron (MLP) Model

We evaluated our model against a Multi-layer Perceptron (MLP) using scikit-learn's `MLPClassifier`. Configured with a 'ReLU' activation function and an 'sgd' solver, the MLP model achieved an accuracy of 71% on a 70-30 training-testing dataset split. Despite the MLP's higher accuracy, we ultimately opted to proceed with the random forest due to its faster processing time.

### Model Performance Summary

| Model                       | Accuracy (%) | Precision (%) |
|-----------------------------|--------------|---------------|
| Initial Random Forest Model | 62           | 63            |
| Improved Random Forest Model| 66           | 65            |
| Multilayer Perceptron Model (MLP) | 71       | 70            |

## Conclusions & Discussion

Our team developed a COVID-19 risk and mortality prediction tool, leveraging a Random Forest model with 66% accuracy and a Tableau dashboard integrated with Python APIs. While the tool has limitations, it presents exciting opportunities for future refinement and expansion.

### Relevance & Impact

20% of COVID-19 hospitalized patients require ICU care, highlighting the model's importance for healthcare workers, administrators, policymakers, and patients. It provides quick risk and mortality predictions based on patient information, aiding in efficient treatment, risk stratification, and resource allocation during potential COVID-19 spikes. Public health officials and researchers can use the model's data to understand disease dynamics and intervention effectiveness across diverse populations.

### Risks and Limitations

The model is limited to Mexican patient data, making it non-universal. Success could lead to global expansion or separate models for each country. It's crucial to acknowledge that machine learning models aren't infallible, and incorrect predictions may occur. Currently, the model employs binary classification, which may oversimplify patient outcomes. Nevertheless, it aims to enhance decision-making for healthcare workers, improving treatment efficiency and quality.

### Example Images
#### Patient Analysis

![Patient Analysis](https://github.com/Ghostlun/COVID-19-Severity-and-Mortality-Analysis/blob/master/covid/team155final/Patient%20Analysis.png)"

#### Patient Flow

![Patient Flow](https://github.com/Ghostlun/COVID-19-Severity-and-Mortality-Analysis/blob/master/covid/team155final/Patient%20Flow.png)"

## COVID Severity and Mortality Analysis Dashboard Initial Setup

### Description

This repository contains the COVID Severity and Mortality Analysis dashboard, which utilizes a TabPy connection. The included Jupyter Notebook file will produce and deploy the model. This notebook requires `Covid Data.csv` as an input. The outputs include the deployed model to Tableau and two cleaned datasets: `Covid_Clean_Sankey.csv` and `Covid_Clean.csv`.

The Tableau dashboard allows analysis of trends in COVID outcomes and provides real-time predictions of COVID severity. A partial dashboard is available at: [Patient Analysis](https://public.tableau.com/app/profile/maria.tariq/viz/group155visualization_NoTabpy/PatientAnalysis?publish=yes). However, the full dashboard must be launched locally due to the TabPy connection. Instructions are included below.

### Installation

Follow these steps to set up the environment and deploy the model:

1. Open Terminal and run:
   ```bash
   pip install tabpy
   pip install tabpy-client
   tabpy

2. Once the installation runs successfully, you will see a line in the terminal with "Web service listening on port 9004". Note the port number displayed in the terminal.

3. In Tableau, navigate to Help > Settings and Performance > Manage Analytics Extension Connection.

4. Select TabPy and set the Hostname as localhost and the Port as the noted port number. Test the connection.

5. Open the Jupyter notebook and execute the entire file.

6. Go to Tableau and start using the notebook. If there are errors related to the Datasource, replace them with the same datasets in the folder.

