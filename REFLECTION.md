# Reflection And Technical Ownership

## Personal Implementation

We implemented an end-to-end univariate time series forecasting workflow for weekly influenza-like illness activity.

Main implemented parts:

- Loaded and cleaned the ILINet CSV export.
- Converted `YEAR` and `WEEK` into a continuous weekly date index.
- Selected `%UNWEIGHTED ILI` as the target variable.
- Plotted and decomposed the time series.
- Tested stationarity using ADF and Phillips-Perron.
- Inspected ACF and PACF before and after differencing.
- Fit and compared several SARIMA candidate models.
- Evaluated the selected SARIMA model on the final 52 weeks.
- Checked residual diagnostics using standardized residuals, residual ACF, Ljung-Box, QQ plot, and Shapiro-Wilk.
- Produced a final 52-week forecast with confidence intervals.

## What Failed Or Was Limited

The SARIMA model captured the general seasonal structure but did not forecast the sharp December 2025 ILI peak well. The model underestimated the largest outbreak weeks.

The residual diagnostics were mixed. Ljung-Box results did not show strong remaining autocorrelation, but the QQ plot and Shapiro-Wilk test showed that residuals were not normally distributed.

## Technical Challenges

One challenge was deciding whether to difference the series. ADF and Phillips-Perron indicated that the original series was already stationary, while the ACF still showed strong seasonality. This required separating stationarity from seasonality.

Another challenge was selecting SARIMA candidates manually without using auto-ARIMA. The final model was selected by lowest AIC among a small set of lecture-based candidates and then checked using test-set errors and diagnostics.

## What We Learned

We learned that a series can pass stationarity tests and still have strong seasonal dependence. We also learned that residual diagnostics are essential: a model can have reasonable autocorrelation diagnostics but still fail normality checks because of extreme outbreak behavior.

The project also showed that epidemiological time series are difficult to forecast with a univariate model because sudden outbreaks may depend on external factors not present in the dataset.

## Failure Log

1. Regular differencing was considered, but stationarity tests showed the original series already rejected a unit root. This raised the risk of overdifferencing.

2. Several SARIMA candidates were tested. Models with higher AIC or worse test-set errors were not selected.

3. The selected SARIMA model underestimated the December 2025 peak, showing that the model is limited during unusually sharp outbreaks.

## Future Improvements

Possible improvements:

- Add exogenous variables such as weather, vaccination rates, or school calendar indicators.
- Compare against additional models after the SARIMA baseline is finalized.
- Try transformations or robust error modeling to reduce the effect of extreme peaks.
- Use rolling-origin validation instead of a single 52-week holdout.

## Team Contribution Log

Fill this section before submission.

```text
Student 1:
- 

Student 2:
- 
```
