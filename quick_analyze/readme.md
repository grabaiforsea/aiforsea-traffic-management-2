## Here are the random forest and xgboost testing code utilize the various train test data to verify my model.

**Random Forest model**:
1. forest_perform_train08_test02.ipynb - training data splits into 80% train and 20% test.
2. rf_xgb_traintest60_holdout61.ipynb - training data splits into train data (first 60 days) and test data (day 61).
3. forest_perform_test61_t0.ipynb - training data splits into train data (first 60 days) and test data (day 61 timestamp 0:0).
4. forest_perform_test61_t15.ipynb - training data splits into train data (first 60 days) and test data (day 61, timestamp less than and equal to 0:15).
5. forest_perform_test61_t1145.ipynb - training data splits into train data (first 60 days) and test data (day 61, timestamp less than 12:00).
6. forest_perform_train47_test14.ipynb - training data splits into train data (first 47 days) and test data (last 14 days).
7. forest_perform_test61.ipynb - training data splits into train data (first 60 days, 75%), test data (first 60 days, 25%) and hold out data (day 61).

**XGBoost model**:
1. xgboost_perform_train08_test02.ipynb - training data splits into 80% train and 20% test.
2. rf_xgb_traintest60_holdout61.ipynb - training data splits into train data (first 60 days) and test data (day 61).
3. xgboost_perform_test61_t0.ipynb - training data splits into train data (first 60 days) and test data (day 61 timestamp 0:0).
4. xgboost_perform_test61_t15.ipynb - training data splits into train data (first 60 days) and test data (day 61, timestamp less than and equal to 0:15).
5. xgboost_perform_test61_t1145.ipynb - training data splits into train data (first 60 days) and test data (day 61, timestamp less than 12:00).
6. xgboost_perform_train47_test14.ipynb - training data splits into train data (first 47 days) and test data (last 14 days).
7. xgboost_perform_test61.ipynb - training data splits into train data (first 60 days, 75%), test data (first 60 days, 25%) and hold out data (day 61).
