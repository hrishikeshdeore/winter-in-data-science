WiDS 2024
UID-31(Dynamic stock market analysis) Final Report
Goal :The goal of the code is to implement a Long Short-Term Memory (LSTM) neural network for predicting future prices of Tata Motors stock based on historical price data. The script leverages the TVDatafeed library for fetching historical stock data, pandas_ta which conducts technical analysis, preprocesses the data, and trains an LSTM model for time series prediction.
Code Overview:
Data Retrieval and Technical Analysis:
Historical stock price data for Tata Motors is retrieved using the TVDatafeed library.
Technical analysis features such as Relative Strength Index (RSI) and Exponential Moving Averages (EMAs) are calculated and added to the dataset.
Data Preprocessing:
Unnecessary columns (volume, symbol, open, high, low, datetime) are dropped from the dataset.
The remaining dataset is normalized using Min-Max scaling.
Sequence Generation:
Sequences of historical data (backcandles -number of previous data points) are created for each technical analysis feature.
The sequences are organized to be compatible with the LSTM input format.
Model Architecture:
An LSTM neural network is created with one LSTM layer and one dense layer.
The model is compiled using the Adam optimizer and Mean Squared Error (MSE) loss.
The model is trained on the prepared training data for a specified number of epochs.
Prediction:
The trained model is used to predict future values based on the test data.
The predicted values are stored in the y_pred variable.
Visualization:
The actual test data (y_test) and the predicted values (y_pred) are visualized using a line plot.

Report:
The code effectively combines financial data retrieval, technical analysis, and deep learning to predict future prices for stocks (I have used Tata motors). The use of an LSTM neural network allows the model to capture temporal dependencies in the data, making it suitable for time series prediction tasks.
The LSTM model is trained on a set of historical data and tested on unseen data to evaluate its predictive performance. The visualization at the end of the code provides a clear comparison between the actual test prices and the predicted prices, allowing for a qualitative assessment of the model's accuracy.
It's important to note that the success of the model relies on the quality and relevance of the features used for prediction, as well as the appropriate tuning of hyperparameters. Continuous monitoring and refinement of the model may be necessary to adapt to changing market conditions.


Strategy: 
I have used the trading strategy of ‘go with trend’. In this strategy we see the current trend of stock price, if it is in uptrend we buy, if it is in down trend we sell. For this trend identification I have used EMA8,EMA8,EMA21 and EMA44 indicators in pandas_ta library. When the slope of all the indicators is increasing, we say that the stock is in uptrend. Using these features of dataset the model identifies the uptrend or downtrend and predicts the future trend. The model works well on daily and hourly time frames.
