# TSA-Temperature-Forecast
Temperature forecasting using time-series analysis models

Goal:
This is home work assigned by Spiced Academy. A short-term temperature forecast will be created with time series model.

   1. Get and clean temperature data from www.ecad.eu. Daily temperature data in Berlin Tempelhof area was downloaded. Due to the end of second world war, some data in year 1945 are outliers, they were droped out. 
![image](https://github.com/bd-z/TSA-Temperature-Forecast/blob/main/IMG/index.png)
![image](https://github.com/bd-z/TSA-Temperature-Forecast/blob/main/IMG/cleaned.png)
   2. Build a baseline model to model the trend and seasonality. Add season dummies feature by using month value; Add time stemp features; linear regression was performed on the data. R2 score is 0.7509.
   ![image](https://github.com/bd-z/TSA-Temperature-Forecast/blob/main/IMG/baseline.png)
   3. Plot and inspect the different components of a time series. The baseline model captures the trend and seasonality. Observed temperature deducting prediction of the baseline model is the remainder. shifting the remainder for one period is lag 1. the corelation between remainder and lag 1 is 0.8009. ACF and PACF was plot to determin how many lags should be taken into consideration.
   ![image](https://github.com/bd-z/TSA-Temperature-Forecast/blob/main/IMG/Auto_corelation_based_on_trend_seasonality_deducted_remainder.png)
   ![image](https://github.com/bd-z/TSA-Temperature-Forecast/blob/main/IMG/Partial_autocorelation_based_on_trend_seasonality_deducted_remainder.png)
   4. Model time dependence of the remainder using an AR model. With time_step, month_dummies, lag features, a linear regression model is built. with lag1 the R2 score is 0.9106. with lag 2, the R2 score is 0.9120 which does not improve much. I decide to use lag1. Cross validation is performed on 5 folders. The mean value of the 5 R2 score is 0.909. Validating the model on test data indicates a R2 score of 0.9148. Overfitting is not observed.
   ![image](https://github.com/bd-z/TSA-Temperature-Forecast/blob/main/IMG/trend-season-lag1-model%20prediction.png)
   5. Compare the statistical output of different AR models. Using AutoReg package 3 lag is found by the ar_select_order method.The R2 score of AutoReg model on train set is 0.9114

