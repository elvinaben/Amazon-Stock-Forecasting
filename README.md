# Amazon Stock Price Forecasting with LSTM

## Project Overview

In this project, I developed an LSTM model for univariate time series prediction using Amazon's historical stock data from 1990 to 2022. The focus is on the Date and Close Price columns, aiming to forecast the stock price for the upcoming Monday based on data from the previous week (Monday to Friday).

## Methodology

### Data Preprocessing

To ensure the integrity of the input data, the following steps were implemented:

1. **Handling Incomplete Data**: Any sequences where the data for Monday to Friday is incomplete were dropped from the dataset. This step helps maintain consistent input for the model and prevents any inaccuracies in predictions.
  
2. **Windowing Technique**: A windowing technique was applied, where the input consists of a window size of 5 (Monday to Friday stock prices), and the output (horizon = 1) is the stock price for the next Monday. This transforms the raw time series data into a structured format for training.

## Models Developed

1. **Baseline Model**: A simple LSTM model with 50 units and ReLU activation, followed by a single-unit Dense layer for prediction.
2. **Tuned Model**: A model optimized with hyperparameters obtained through RandomSearch Tuner, featuring 70 LSTM units and a learning rate of 0.00013.
3. **Modified Model**: Similar to the Tuned model but includes an additional Dropout layer with a rate of 0.05 to mitigate overfitting.

### Model Evaluation
<img width="672" alt="image" src="https://github.com/user-attachments/assets/9cdb96f5-c63d-480c-872c-66432e4769fd">

## Metrics Overview

- **RMSE (Root Mean Squared Error)**: This metric measures the square root of the average squared differences between predicted and actual values. The Tuned model achieves an RMSE of 95.9478, indicating better accuracy compared to the Baseline model's RMSE of 110.4813.

- **MAE (Mean Absolute Error)**: This metric represents the average of the absolute differences between predicted and actual values. The Tuned model's MAE is 67.4480, which is lower than the Baseline model's MAE of 79.5820.

- **MAPE (Mean Absolute Percentage Error)**: This metric measures the average percentage of absolute errors between predicted and actual values. The Tuned model has a MAPE of 2.3474%, outperforming the Baseline model's MAPE of 2.7477%.

The reduction in RMSE, MAE, and MAPE values demonstrates the effectiveness of hyperparameter tuning in enhancing the model's performance. However, the Modified model, while slightly improved over the Baseline, did not surpass the Tuned model's accuracy.

## Conclusion

The Tuned model (Model 2) is the best performer, exhibiting the lowest RMSE, MAE, and MAPE values among the three models.

### Prediction vs Actual: Tuned Model Performance (Best Model)
<img width="814" alt="image" src="https://github.com/user-attachments/assets/4169c5f4-e772-4746-aa79-44cbf0216336">

The graph above shows the actual stock prices alongside the predicted prices from the tuned model for Mondays based on the test data. The time axis starts at 0, denoting the initial prediction in the test dataset, and advances sequentially. It is clear that the predicted prices are closely matched with the actual close prices, highlighting the model's effectiveness in forecasting.

