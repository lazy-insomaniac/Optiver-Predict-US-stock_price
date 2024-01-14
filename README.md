# Optiver-Predict-US-stock_price
This repo is for an open project by VLG on predicting closing price of stocks. Our task was to predict the closing proce i.e. 'target' for the last three days in the data provided by Nasdaq 100 
![image](https://github.com/lazy-insomaniac/Optiver-Predict-US-stock_price/assets/114395022/9c6fd3c3-fe6b-4b26-9f4b-c7066209a79d)


# Datasets Links 📑
Original training Data : https://drive.google.com/file/d/1HUClzGiyTt2jWmVAVUrbWtx8i26dNWrk/view?usp=drive_link
Preprocessed published on Kaggle : https://www.kaggle.com/datasets/dragon54/public-balanced-data/data   ( Recommended to save time ) 


# About the Data 
* train.csv : We get a tabular data containing the last 10 minute data of Nasdaq exchange.
 * There are 200 stocks , 55 entries of each stock each stock each day , 11000 entries in a single day.
*revealed_targets : This data is given by API on 0th seconds_in_bucket value of any day . They are the actual/ true target values of previous day.

# Libraries that need to be installed 🔩
Optuna : pip install optuna


# Set up for the project ⚙️
Use kaggle notebooks as they have more resources and paths in notebook are set according to them.
Import the notebook in Kaggle.
You are recommened to upload the data files accordingly as suggested below
  * /kaggle/input/optiver-trading-at-the-close/optiver2023
  * /kaggle/input/optiver-trading-at-the-close/public_timeseries_testing_util.py
  * /kaggle/input/optiver-trading-at-the-close/train.csv   actual training data (only do this one in preprocessing notebook) 
  * /kaggle/input/public-balanced-data/balanced_data.csv    ( this is the preprocessed training data )

![image](https://github.com/lazy-insomaniac/Optiver-Predict-US-stock_price/assets/114395022/8fd3b183-8194-4e31-9f52-df971159c1b5)



# Steps taken (Concise) 
* 1. On analysis the very first observation was that our dataset had some missing values , this was dealt by imputing medians over grouped data in the dataset to ensure that correct medians were being put for each stock_id and date_id
* 2. Another problem with the dataset as mentioned in the description was that not all time buckets had all stock_id , i.e. there were completely missing records in the dataset , again used median to deal with this as given in the code 
* 3. As the above steps were consuming a lot of time decided to publish the processed data as public and directly add it for usage 
* 4. Then proceeded to make some extra features that were useful specifically the time related features as they are highly informative about the market's behavior 
* 5. While performing EDA using sweetviz , found out that date_id , time_id and seconds_in_bucket were highly correlated , used this and self observation to find out the relation between the three as :  date_id = time_id/55 as int type and seconds_in_bucket=(time_id%55)*10 
* 6. Initially tried working on a LSTM model but found it difficult to implement the API , so then decided to switch on Lightgbm regressor as it works well with large datasets 
* 7. Tuned the hyperparameters of LGBM using optuna library while keeping the objective to minimise mean absolute error and implemented the API with the same model 
* 8. Also trained XGB model but after removing outliers as an experiment , but XGB proved to be better 
* 9. Finally Implemented the API along with Lightgbm model.
 
 # All other info has been given in the main notebook.

 # Results
 We were sucessfully able to create a model that predicts the target value . We were also able to achieve quite low mean absolute error  4.54 over public test data which is a good score in accordance with the   
 actual kaggle challenge's leaderboard.

 # Thank you 






