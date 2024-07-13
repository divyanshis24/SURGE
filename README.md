# SURGE
# Introduction
Forecasting volatile stock return prices is challenging due to the complexity and unpredictability of financial time series data. Traditional models like Autoregressive Integrated Moving Average (ARIMA) and Generalised Autoregressive Conditional Heteroscedasticity (GARCH) are widely used but struggle with nonlinear patterns and long-term dependencies. Recent advancements in machine learning, particularly Long Short-Term Memory (LSTM) networks, show promise in handling complex time series data. LSTM networks capture long-term dependencies and nonlinear patterns, but their performance depends on careful selection of input lags. This study proposes a novel hybrid model that combines ARIMA and LSTM, using a random forest algorithm for selecting suitable input lags for LSTM.

# Methodology
## ARIMA Model
To ensure stationarity, the Augmented Dickey-Fuller (ADF) test was employed, confirming stationarity after log transformation. The ARIMA(2,1,2) model was constructed to capture the mean effect, with residuals showing normal distribution and constant variance confirmed by the Ljung-Box Q test.

## ARIMA-GARCH Model
The ARCH LM test detected volatility in ARIMA residuals. The ARIMA-GARCH model (p_garch: 3, q_garch: 0) was developed, confirmed by the Ljung-Box Q test. ARIMA-GARCH showed superior performance over ARIMA based on lower AIC values.

## LSTM Model
Training data were normalized using MinMaxScaler. TimeseriesGenerator transformed the data for the LSTM model. Hyperparameters (batch size, learning rate, dropout rate) were tuned using grid search. One-step cross-validation evaluated model performance.

## Proposed Model (ARIMA-LSTM with Random Forest)
ARIMA squared residuals were used to estimate input lags via ACF and random forest. Relevant input lags were selected, and the LSTM model was implemented for residual prediction. The random forest technique reduced the number of parameters and computational time.

## Gradient Tree Boosting
Gradient Boosting was applied using Oil Volatility Index, Volatility Index, and Indian Energy Exchange as independent variables, and Nifty50 closing prices as the dependent variable. The model achieved 98.7% accuracy, outperforming other models.

# Conclusion
We introduced a novel ARIMA-LSTM hybrid model using random forest for input lag selection. ARIMA-GARCH outperformed ARIMA in modeling volatility, with lower AIC values. LSTM models were compared with statistical models, showing superior results in capturing complex data relationships. Gradient Tree Boosting demonstrated excellent predictive performance, significantly improving accuracy. This hybrid model effectively handles volatile financial time series data, providing robust forecasting capabilities.
