<!-- PROJECT SHIELDS -->
[![LinkedIn][linkedin-shield]][linkedin-url]
___

<a href="https://www.aiforsea.com/"><h2 align="center">AI for S.E.A.</h2></a>
<p align="center">
  :bar_chart: How may we improve the traffic congestion for Southeast Asia's roads by leveraging Grab's booking demand data? <strong>Traffic Management</strong>
  <br><br>
  <a href="https://www.aiforsea.com/traffic-management">
    <img alt="Traffic Management" src="https://static.wixstatic.com/media/397bed_5d7ca71009b54dcf895b447920495d40~mv2.png/v1/fill/w_305,h_305,al_c,q_80,usm_0.66_1.00_0.01/Grab%20EDM_Safety.webp">
  </a>
</p>

___

<!-- TABLE OF CONTENTS -->
### Table of Contents

* [Grab Challenge](#Grab-Challenge)
  * [Problem Statement](#Problem-Statement)
  * [Objective](#Objective)
  * [Built With](#built-with)
* [Quick Link to Code](#Quick-Link)  
* [Prerequisites](#prerequisites)
* [Getting Started](#getting-started)
  * [Data Preparation](#Data-Preparation)
* [Feature Engineering](#Feature-Engineering)
  * [Train Test Data](#Train-Test-Data)
* [Data Visualization and Exploration](#Data-Visualization-and-Exploration)
* [Train the Regression Model](#Train-the-Regression-Model)
* [Model Comparison](#Model-Comparison)
* [Best Model](#Best-Model)
* [Complete Data Science Model](#Complete-Data-Science-Model)
* [Contact](#contact)
* [Acknowledgements](#acknowledgements)

___

<!-- ABOUT THE PROJECT -->
## Grab Challenge
### Traffic Management
How may we improve the traffic congestion for Southeast Asia's roads by leveraging Grab's booking demand data? This is a data science assignment where you are expected to create a data model from a given training dataset.

### Problem Statement
Economies in Southeast Asia are turning to AI to solve traffic congestion, which hinders mobility and economic growth. The first step in the push towards alleviating traffic congestion is to understand travel demand and travel patterns within the city.

Can we accurately forecast travel demand based on historical Grab bookings to predict areas and times with high travel demand?

### Objective
To build a model trained on a historical demand dataset, that can forecast demand on a Hold-out test dataset. The model should be able to accurately forecast ahead by T+1 and T+5 time intervals (where each interval is 15-min) given all data up to time T.

### Built With
* [Anaconda](https://www.anaconda.com/)
* [Jupyter Notebook](https://jupyter.org/)
* [Spyder](https://www.spyder-ide.org/)
* [Google Colab](https://colab.research.google.com/notebooks/welcome.ipynb)
___

<!-- Quick Link -->
## Quick Link
* [Export train test data](https://github.com/cmxteng/aiforsea-traffic-management/blob/master/export_train_test_set.ipynb) is quick split of train and test data, it can include day 61 only data.
* [Complete code documentation](https://github.com/cmxteng/aiforsea-traffic-management/blob/master/complete_code_documentation.ipynb) is the documentation of the complete code with all models.
* [Complete codebase](https://github.com/cmxteng/aiforsea-traffic-management/blob/master/complete_codebase.ipynb) is quick analysis of my selected model code, **XGBoost AI model for this challenge**.

___

<!-- Prerequisites -->
## Prerequisites
* geohash
```sh
pip install python-geohash
```
* xgboost
```sh
conda install -c anaconda py-xgboost
```
or
```sh
pip install xgboost
```

___

<!-- GETTING STARTED -->
## Getting Started
The given dataset contains normalised historical demand of a city, aggregated spatiotemporally within geohashes and over 15 minute intervals. The dataset span over a two month period. A brief description of data set fields are found below:

* geohash: geohash level 6
* day: day, where the value indicates the sequential order and not a particular day of the month
* timestamp: start time of 15-minute intervals, in the following format: hour and minute, where hour range from 0 to 23 and minute is either one of (0,15,30,45)
* demand: aggregate demand normalised to be in the range [0,1]

What to do?
1. Day column is from day 1 to day 61. Do I need to split a day for testing?
2. Timestamp type is object/time format. Convert to float number?
3. Geohash6 is encoded. Should I decode to latitude and longitude?
4. Demand column is in normalized. [0,1]

Abbreviation:
* Explained Variance, EV.
* Mean Absolute Error, MAE.
* Mean Squared Error, MSE.
* Root Mean Squared Error, RMSE.
* Cross Validation, CV.
* Grid search cross validation, GSCV.
* Extreme Gradient Boosting, XGBoost.

<!-- DATA PREP -->
### Data Preparation
1. Getting the data, click [here](https://s3-ap-southeast-1.amazonaws.com/grab-aiforsea-dataset/traffic-management.zip) to get the data.
2. Data Investigation.
    * Print and view the data to check for potential feature and label.
    * Check the quality of data including find missing value in data.
    * Investigate the data type such as float, int, string, etc.
    * Examine the class label, categorical or numerical.  

___

<!-- FEATURE ENGINEERING -->
## Feature Engineering
1. Deciding what features to create.
2. Decode geohash6 into readable format, float.
3. Convert the timestamp into readble format, float.
4. Cleaning the data.
5. Adjust the day and timestamp to ascending order for viewing purpose.
6. Split the training data into train dataset and test dataset.
7. Create features.
8. Check how the features work with the model.
9. Improving the features created.
10. Go back to deciding more features until the work is done if necessary.

Click [data split](https://github.com/cmxteng/aiforsea-traffic-management/blob/master/export_train_test_set.ipynb) for quick view on the data splitting code.

<!-- TRAIN TEST DATA -->
### Train Test Data
The train and test dataset I used to train my model to find the best parameter is:
* training data splits into 75% train and 25% test

Here are the train test data I have split to verfiy my model:
1. Training data splits into 80% train and 20% test.
2. Training data splits into train data (first 60 days) and test data (day 61).
3. Training data splits into train data (first 60 days) and test data (day 61 timestamp 0:0).
4. Training data splits into train data (first 60 days) and test data (day 61, timestamp less than and equal to 0:15).
5. Training data splits into train data (first 60 days) and test data (day 61, timestamp less than 12:00).
6. Training data splits into train data (first 47 days) and test data (last 14 days).
7. Training data splits into train data (first 60 days, 75%), test data (first 60 days, 25%) and hold out data (day 61).
___

<!-- DATA VISUALIZATION -->
## Data Visualization and Exploration
* Visualize the demand using histogram chart.
* Explore the rest of the features and the demand.

Click [complete code](/traffic_complete.ipynb) to find the Data Visualization and Exploration, this will link you to the complete codebase.

___

<!-- TRAINING -->
## Train the regression model
The demand column is a continuous variable, hence regression model is selected.
The regression models that I have chosen to test are:
  * Decision Tree
  * Random Forest
  * Xgboost

Each of the regression model will validate with cross validation method and train with the best parameters by using grid search cross validation method.

I will select one of these regression as the best model where the model has overcomes the underfitting and overfitting as low as possible.

Here are the [random forest and xgboost testing code](https://github.com/cmxteng/aiforsea-traffic-management/tree/master/quick_analyze) utilize the various train test data to verify my model.

Random Forest model:
1. forest_perform_train08_test02.ipynb - training data splits into 80% train and 20% test.
2. rf_xgb_traintest60_holdout61.ipynb - training data splits into train data (first 60 days) and test data (day 61).
3. forest_perform_test61_t0.ipynb - training data splits into train data (first 60 days) and test data (day 61 timestamp 0:0).
4. forest_perform_test61_t15.ipynb - training data splits into train data (first 60 days) and test data (day 61, timestamp less than and equal to 0:15).
5. forest_perform_test61_t1145.ipynb - training data splits into train data (first 60 days) and test data (day 61, timestamp less than 12:00).
6. forest_perform_train47_test14.ipynb - training data splits into train data (first 47 days) and test data (last 14 days).
7. forest_perform_test61.ipynb - training data splits into train data (first 60 days, 75%), test data (first 60 days, 25%) and hold out data (day 61).

XGBoost model:
1. xgboost_perform_train08_test02.ipynb - training data splits into 80% train and 20% test.
2. rf_xgb_traintest60_holdout61.ipynb - training data splits into train data (first 60 days) and test data (day 61).
3. xgboost_perform_test61_t0.ipynb - training data splits into train data (first 60 days) and test data (day 61 timestamp 0:0).
4. xgboost_perform_test61_t15.ipynb - training data splits into train data (first 60 days) and test data (day 61, timestamp less than and equal to 0:15).
5. xgboost_perform_test61_t1145.ipynb - training data splits into train data (first 60 days) and test data (day 61, timestamp less than 12:00).
6. xgboost_perform_train47_test14.ipynb - training data splits into train data (first 47 days) and test data (last 14 days).
7. xgboost_perform_test61.ipynb - training data splits into train data (first 60 days, 75%), test data (first 60 days, 25%) and hold out data (day 61).


The results of the three models will show in the Model Comparison section.

Click [Training and Testing](/train_test.ipynb) for quick view on the training and testing model.

___

<!-- MODEL COMPARISON -->
## Model Comparison

1. Training data splits into 80% train and 20% test 

| Models                 | Random Forest | **XGBoost** |
|------------------------|---------------|-------------|
|CV Train RMSE:          | 0.0330        | **0.0414**  |
|Prediction RMSE:        | 0.0322        | **0.0413**  |

2. Training data splits into train data (first 60 days) and test data (day 61)

| Models                 | Random Forest | **XGBoost** |
|------------------------|---------------|-------------|
|CV Train RMSE:          | 0.0312        | **0.0409**  |
|Prediction RMSE:        | 0.0735        | **0.0689**  |

3. Training data splits into train data (first 60 days) and test data (day 61 timestamp 0:0) 

| Models                 | Random Forest | **XGBoost** |
|------------------------|---------------|-------------|
|CV Train RMSE:          | 0.0312        | **0.0409**  |
|Prediction RMSE:        | 0.0732        | **0.0708**  |

4. Training data splits into train data (first 60 days) and test data (day 61, timestamp less than and equal to 0:15)

| Models                 | Random Forest | **XGBoost** |
|------------------------|---------------|-------------|
|CV Train RMSE:          | 0.0312        | **0.0409**  |
|Prediction RMSE:        | 0.0740        | **0.0717**  |

5. Training data splits into train data (first 60 days) and test data (day 61, timestamp less than 12:00)

| Models                 | Random Forest | **XGBoost** |
|------------------------|---------------|-------------|
|CV Train RMSE:          | 0.0312        | **0.0409**  |
|Prediction RMSE:        | 0.0831        | **0.0768**  |

6. Training data splits into train data (first 47 days) and test data (last 14 days)

| Models                 | Random Forest | **XGBoost** |
|------------------------|---------------|-------------|
|CV Train RMSE:          | 0.0308        | **0.0403**  |
|Prediction RMSE:        | 0.0870        | **0.0799**  |

7. Training data splits into train data (first 60 days, 75%), test data (first 60 days, 25%) and hold out data (day 61)

| Models                 | Random Forest (test) | **XGBoost** (test) |Random Forest (hold out) | **XGBoost** (hold out) |
|------------------------|----------------------|--------------------|-------------------------|------------------------|
|CV Train RMSE:          | 0.0741               | **0.0413**         | 0.0741                  | **0.0413**             |
|Prediction RMSE:        | 0.0320               | **0.0410**         | 0.0732                  | **0.0692**             |

___

<!-- BEST MODEL -->
## Best Model
The best model was trained and tested with cross validation method to avoid overfitting. The best parameter was determined by the grid search cross validation method.

Based on the cross validation and prediction from the model comparison, Xgboost shows low RMSE and lowest distance difference between train and predicted RMSE. Therefore, the conclusion of the best model is XGBoost. An optimal balance of bias and variance would never overfit or underfit the model.

The bias is an error from erroneous assumptions in the learning algorithm. Model with high bias pays very little attention to the training data and oversimplifies the model. The variance is an error from sensitivity to small fluctuations in the training set. Model with high variance pays a lot of attention to training data and does not generalize on the data which it hasn’t seen before.

In supervised learning, underfitting happens when a model unable to capture the underlying pattern of the data. Overfitting happens when our model captures the noise along with the underlying pattern in data.

Click [Perform](https://github.com/cmxteng/aiforsea-traffic-management/blob/master/complete_codebase.ipynb) for a quick prediction on your hold out dataset in **Xgboost model**.

___

<!-- COMPLETE DATA SCIENCE MODEL -->
## Complete Data Science Model
* Click [complete codebase](https://github.com/cmxteng/aiforsea-traffic-management/blob/master/complete_codebase.ipynb) for a complete test of my XGBoost model code.

* Click [complete code documentation](https://github.com/cmxteng/aiforsea-traffic-management/blob/master/complete_code_documentation.ipynb) for a quick view of my code documentation from getting start to the best model I obtained.

___

<!-- CONTACT -->
## Contact

Teng Chun Man - [@linkedin](https://www.linkedin.com/in/tengchunman/)

Email: tengchunman@gmail.com

Project Link: [https://github.com/cmxteng/aiforsea-traffic-management](https://github.com/cmxteng/aiforsea-traffic-management)

___

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [Understanding the Bias-Variance Tradeoff](https://towardsdatascience.com/understanding-the-bias-variance-tradeoff-165e6942b229)
* [Mean squared error](https://en.m.wikipedia.org/wiki/Mean_squared_error)
* [XGBoost (python)](https://wuhuhu800.github.io/2018/02/28/XGboost_param_share/)

<!-- MARKDOWN LINKS & IMAGES -->
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/tengchunman/
