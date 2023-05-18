# Sales-Prediction-Time-Series-Analysis
Prediction of sales based upon time
### **The summary of the steps executed in ML model are:**

**1. Data collection and overview of the dataframe:**
- The data was extracted from csv file downloaded from kaggle.
- Data consist of 107 rows and 2 columns.
- Intuition of the data was gained via calling the first five and last five rows.
- There were 2 rows with NAN value.

**2. Data Preprocessing:**
- There were ~1-2 % of NAN value in the given feature of dataframe. So the same was dropped.
- Check for outlier using IQR method.
- There were 10 outliers in the upper limit of the data.
- Check was made to replace the values above upper whiskers with upper whiskers. Since there was drastic change in seasonality of data so self has retained the outliers.

**3. Feature Extraction and Exploration:**

Feature like year, month, date,week and weekday was extracted from the date feature of dataframe in order to check the trend of sale with respect to year, month, date,week and weekday. The following conclusion was drawn on fetching the plots:
- Highest sale occured in the year of 1971.
- December month got the highest sales compared to other months.
- Week four was having the highest sales in any month.
- Day one of week was having the highest sale.
    
**4. Check for Stationarity of data:**

The data was tested for Stationarity via adfuller test. The value of sales was checked with adfuller test. The test depeicted value of p > 0.05 which implies the data is not stationary. Thereafter shifting the values of Sale by 1 and performing adfuller test resulted in p value<=0.05 which implied that data is stationary on shifting the value by 1 and subtracting from the original sale value at same corresponding date. Since there was seasonality in data self has checked shifted the sales value by 12 and subtracted from the original sales value at same corresponding dates.The same passed the adfuller test as well. KDE plot was plotted represented shifted data sales is uniformally distributed which in turn implies stationarity of data.

**5. ARIMA Model building:**

Self has computed p,q and d value for ARIMA Model via two method:
- Plotting graphs ACF and PACF plot for computing p and q value respectively.
- Iterations method.

Based upon the result from ACF/ PACF plot and iteration method value of p,d,q was finalised to 7,5,7 respectively.Further via above fetched order values, ARIMA model was fit/trained and validation sales value was predcited. Thereafter futher 12 month values was predicted. Since there was seasonality data in the given data frame, ARIMA model failed to provide desired results.

**6. SARIMA Model building:**

Futhermore to the results obtained from ARIMA model, SARIMA model was fitted to the given data set after iterating the best value of p,d,q,P,Q,D,s.Further via above fetched order values, SARIMA model was fit/trained and validation sales value was predcited. Thereafter futher 12 month values was predicted. SARIMA Model was predicting the result with RMSE error of **0.14** which resulted in a clean smooth expected plot of sales w.r.t time. Hence the SARIMA model was finalised for predicting the future sales value forecast.
