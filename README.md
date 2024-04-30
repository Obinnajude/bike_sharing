# bike_sharing
# Predict bike sharing with Autogluon
## Report: Predict Bike Sharing Demand with AutoGluon key take aways

In this project, I used the AutoGluon library to train several models for the Bike Sharing Demand competition in Kaggle. I used Tabular Prediction to fit data from CSV files provided by the competition. 

### Initial Training 
The top ranked model that performed was WeightedEnsemble_L3
followed by LightGBM_BAG_L2
And RandomForestMSE_BAG_L2.

### Exploratory data analysis and feature creation
The histogram display provided an overview of the data's distribution, allowing us to understand its central tendency, spread, and shape. They gave us a sense of the data's characteristics and help identify any patterns, trends, or anomalies present. New feature were added from the datetime feature in the train and test data using train["hour"] =
train['datetime'].dt.hour, test["hour"] = test['datetime'].dt.hour. The dtype for
season and weather were changed from being just an integer data type to category data type.
### Model Performance
The model performed better by adding new additional features with a percentage increase in
performance of 66%. This I think was because of improved representation, which helped the
model capture meaningful patterns or relationships that weren’t apparent from the original
column alone. By deriving features at different time granularities (e.g., day, month, year), you can perform temporal aggregations and summarize the data at different levels. This enables one to analyze trends over time, identify long-term patterns, or compare data across different time periods. They provide additional information and context that might be relevant for predicting the target variable.
### Hyper parameter tuning
The model did perform much better with a kaggle score of approximately 21% better through
hyper parameter tuning than when the new feature was added, but I think with more parameter
tuning it might even get better.

index model hpo1 hpo2 hpo3 score
0 initial time_limit=600 time_limit = 600 time_limit = 600 1.80438
1 add_features presets =best_quality presets= best_quality presets = best_quality 0.61215
2 hpo num_boost_round: 100 num_boost_round: 100 num_boost_round: 100 0.48518
### Line plot showing the top model score for the three training runsduring the project.

![modelscore2](https://github.com/Obinnajude/bike_sharing/assets/45057355/1c809e1b-3141-437a-b80b-7258c5de1981)


### Line plot showing the top kaggle score for the three prediction submissions during the project.
![kagglescore](https://github.com/Obinnajude/bike_sharing/assets/45057355/895fc892-b3c8-46d8-9f20-fef0fbaeee4e)

### Summary
The leaderboard shows WeightedEnsemble_L3
As the top-performing model, with the lowest rmse score value. Feature importance was shown,
as adding the hour feature and changing the dtype for the season and weather features of the
dataset improved the model kaggle score performance to 66%. Hyper parameter optimization
improved the kaggle score from the additional feature performance to approximately 21%
