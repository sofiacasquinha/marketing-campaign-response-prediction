# Marketing Campaign Response Prediction

A machine learning classification project developed to predict which customers are most likely to respond to a marketing campaign.

The objective is to help a retail company improve campaign efficiency by prioritising likely responders and reducing unnecessary customer contacts.

## Business Objective

The target variable is:

* `Response = 1`: the customer accepted the latest campaign
* `Response = 0`: the customer did not accept the latest campaign

The model uses customer demographics, purchase behaviour, spending, previous campaign responses, and customer activity.

## Dataset

The project uses the provided `campaign.xlsx` dataset.

Main variable groups include:

* customer education and marital status;
* income and household composition;
* product spending;
* web, store, catalogue, and discounted purchases;
* website visits;
* recency;
* previous campaign acceptance;
* complaints;
* customer enrolment date.

## Project Workflow

The project follows the CRISP-DM methodology:

1. Business Understanding
2. Data Understanding
3. Data Preparation
4. Modeling
5. Evaluation
6. Deployment Planning

## Data Preparation

The main preparation steps included:

* removing identifier and constant variables;
* correcting data-quality issues;
* handling missing values;
* encoding categorical variables;
* creating engineered features;
* applying a stratified train-test split;
* scaling variables for Logistic Regression;
* applying SMOTE to the training data used by the baseline models.

Engineered features included:

* `Age`
* `Seniority`
* `Total_Spending`
* `Accepted_Total`

The test set remained unchanged throughout the modeling process.

## Models Tested

The following classification models were evaluated:

* Logistic Regression
* Decision Tree
* Random Forest
* Gradient Boosting

Hyperparameter tuning was performed using `GridSearchCV`.

## Model Performance

| Model                     | Accuracy | Precision | Recall | F1-score | ROC-AUC |
| ------------------------- | -------: | --------: | -----: | -------: | ------: |
| Tuned Gradient Boosting   |     0.90 |      0.73 |   0.45 |     0.56 |    0.90 |
| Tuned Logistic Regression |     0.83 |      0.45 |   0.74 |     0.56 |    0.90 |
| Random Forest             |     0.85 |      0.49 |   0.61 |     0.54 |    0.86 |
| Logistic Regression       |     0.85 |      0.51 |   0.55 |     0.53 |    0.87 |
| Tuned Random Forest       |     0.86 |      0.53 |   0.52 |     0.52 |    0.89 |
| Gradient Boosting         |     0.89 |      0.78 |   0.38 |     0.51 |    0.90 |
| Tuned Decision Tree       |     0.85 |      0.50 |   0.41 |     0.45 |    0.79 |
| Decision Tree             |     0.76 |      0.33 |   0.59 |     0.42 |    0.76 |

## Selected Model

**Tuned Gradient Boosting** was selected as the final model.

It achieved:

* Accuracy: `0.90`
* Precision: `0.73`
* Recall: `0.45`
* F1-score: `0.56`
* ROC-AUC: `0.90`

Confusion-matrix results:

* True negatives: `370`
* False positives: `11`
* False negatives: `36`
* True positives: `30`

The model achieved the highest test-set F1-score and ROC-AUC while maintaining relatively high Precision.

Tuned Logistic Regression achieved the highest Recall but generated substantially more false positives.
