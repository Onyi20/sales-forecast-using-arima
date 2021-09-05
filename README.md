# Forecasting Time Series using ARIMA model
THis is a Time series forecasting Project using ARIMA model. 
### Data
The data was compiles and stored in a Database "retail store" in Postgresql with PgAdmin4. 
The Database records the different transactions each customer makes in a retail store. There are three tables in the database.   
- **sales** table which records the Time each customer makes a trasaction. The sales table includes:-   
  - id (Primary key) and   
  - sales_date (Timestamp: the time the customer checks out their purchase)
- **sales_item** table records the the entire transaction refrencing both the sales and product tables to records all the items bought, the quantity of each item and the total price for each item. The sales_item table includes:-   
  - id (primary key)
  - sales_id (foreign key to sales.id)
  - product_id (foreign key to product.id)
  - quantity_sold (the amt of each item bought (integer))
  - total_sell_price (the total amout of money paid per item (integer))
- **product** table records the different product (names) in the retail store. The product table includes:-   
  - id (primary key)   
  - name (name of product (string))

##### Prep
Creating the tables in the database "retail_store", the data was used for the following insights:-   
- Know the revenue by week of all sales in 2020   
- Know the weeks where the retail store made less than a weekly target of 50   
- Know the months where the retail store made more than the yearly average (yr 2020)   
- and finally Forecast the salles for the retail store

### ARIMA model
ARIMA which means Auto Regressive Integrated Moving Average and is a way of modeling time-series data for forecasting and is specified by three order parameters (p,d,q) where:-   
- AR(p): order of autoregressive terms (AR order)   
- I (d): number of nonseasonal differencing (differencing order)   
- MA (q): number of moving average terms (MA order)   
Genrally, the time series data must be **stationary** before the ARIMA model can be fitted. The ARIMA model can only be fitted using the order of the AR, I and MA respectively. Therefore, the orders of each must be obtained after stationarity is obtained.   
#### Auto ARIMA model (Using pdarima)
Normally, the ACF (auto correlation function) and the PACF (partial auto correlation function) plots are used to obtain the AR, I and MA order(s). However, the pdarima package makes the selection of the ARIMA pdq order easier. By simulating the different ARIMA pdq orders and calculation the AIC of each simulation. The lowest AIC score, denotes the best ARIMA pdq order.
### Forecasting
This order is used to derive the ARIMA model and said model used to forecast the data.   
The dataset is 1st **split** into a train and test set to ensure that the model derived is functioning properly. The model is used on the train set and the test set is forecasted and compared to the actual test ser.   
Then the Forecasting of the unknown future is doen when the experiment is proven successful.
