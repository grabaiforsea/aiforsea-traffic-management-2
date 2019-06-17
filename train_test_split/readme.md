# Train Test Data
The code is to splits the training.csv data into several types of input data.

The train and test dataset I used to train my model to find the best parameter is:
* training data splits into 75% train and 25% test

Here are the train test data that I have split to verfiy my model:
1. 80% train and 20% test.
2. Train data (first 60 days) and test data (day 61).
3. Train data (first 60 days) and test data (day 61 timestamp 0:0).
4. Train data (first 60 days) and test data (day 61, timestamp less than and equal to 0:15).
5. Train data (first 60 days) and test data (day 61, timestamp less than 12:00).
6. Train data (first 47 days) and test data (last 14 days).
7. Train data (first 60 days, 75%), test data (first 60 days, 25%) and hold out data (day 61).
