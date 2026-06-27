# Ethical And Responsible Forecasting Statement

This project forecasts influenza-like illness activity in New York using historical ILINet data. Because the topic is public health, forecasts must be interpreted carefully.

## Possible Misuse

A forecast could be misused if it is treated as a precise prediction of future illness levels. SARIMA is a statistical model based on past values, not a clinical or epidemiological simulation.

## Consequences Of Forecast Errors

Underestimating ILI activity could lead to poor planning for clinics, staffing, testing, vaccination campaigns, or public communication.

Overestimating ILI activity could cause unnecessary concern or inefficient allocation of limited resources.

## Uncertainty And Confidence Intervals

The forecast intervals should not be interpreted as guaranteed bounds. The residual diagnostics show that residuals are not perfectly normally distributed, so uncertainty may be larger during unusual outbreak periods.

## Overfitting Risk

Trying many SARIMA specifications can lead to a model that fits historical data but does not generalize well. Model choice should consider AIC/BIC, test-set performance, residual diagnostics, and whether the parameters are interpretable.

## Data Quality

ILINet data depends on reporting by healthcare providers. Changes in provider participation, healthcare utilization, testing behavior, or reporting practices can affect the measured ILI rate.

## Model Limitations

The current model is univariate. It uses only historical `%UNWEIGHTED ILI` values and does not include external drivers such as vaccination rates, virus variants, school schedules, weather, policy changes, or healthcare access.

## Responsible Interpretation

The SARIMA forecast should be presented as a classical statistical baseline. It can describe recurring seasonal patterns, but it may fail during sudden or unusually strong outbreaks. Any practical decision should combine the forecast with current epidemiological information and expert judgment.
