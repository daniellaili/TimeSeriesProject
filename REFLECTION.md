# Reflection

## What Failed Or Was Limited

The main limitation was that the SARIMA forecast did not capture the sharp ILI peak near the end of the test period very well. The model learned the general seasonal pattern, but it underestimated the strongest outbreak weeks.

Another limitation was the residual normality. The Ljung-Box test did not show strong remaining autocorrelation, which suggested that the residuals were close to white noise in terms of dependence. However, the QQ plot and Shapiro-Wilk test showed that the residuals were not normally distributed. This means the confidence intervals should be interpreted carefully, especially during extreme outbreak periods.

## Technical Challenges

One of the main technical challenges was choosing the SARIMA orders manually. I had to connect the visual ACF/SACF and PACF plots to possible AR, MA, seasonal AR, and seasonal MA terms. This was not automatic, because several lags looked relevant, especially around the seasonal lags of 52 and 104 weeks.

Another challenge was deciding which candidate models were reasonable without testing every possible combination. I used the lecture rules for ARIMA/SARIMA identification, but I also had to avoid overfitting and over-differencing. This led me to compare a focused set of ARIMA and SARIMA models instead of depending on an automatic model-selection tool.

After fitting the candidate models, I also had to decide whether the lowest AIC model was really the best final model. A more complex model can improve AIC slightly while adding parameters that are harder to justify. Therefore, I compared the top models using AIC, BIC, coefficient confidence intervals, test-set errors, and model simplicity.

## What I Learned

I learned how the theoretical methods from the lectures connect to the practical implementation in Python. Concepts such as stationarity, differencing, ACF/SACF, PACF, AR terms, MA terms, seasonal orders, AIC/BIC, and residual diagnostics became much clearer when I had to apply them to a real dataset.

I also learned that the lecture workflow is not just a list of separate steps. Each step affects the next one: stationarity tests influence differencing choices, ACF/PACF plots influence model orders, model comparison influences final selection, and residual diagnostics show whether the model still missed important structure.

This project helped me understand the difference between knowing the theory and making modeling decisions in practice. In the notebook, I had to translate the course ideas into code, plots, tables, interpretation, and final decisions that I could explain.

## What Surprised Me

What surprised me most was that even after implementing the theoretical best practices I learned in class, the forecast still did not work very well for the sharp ILI peak. I followed the expected workflow but still, the final SARIMA model underestimated the strongest outbreak weeks.

This showed me that building the best prediction model usually requires more fine tuning beyond the basic theoretical workflow. A classical SARIMA model can be a good baseline, but real public-health data may need additional work.

## Future Improvements

In the future, I would improve the project by adding external explanatory variables, such as weather, vaccination rates, school calendar indicators, holidays, or public-health events. These variables may help explain sudden changes that a univariate SARIMA model cannot capture.

Finally, I would explore methods for handling outliers and extreme peaks more carefully. Since ILI data can have unusual outbreak weeks, robust modeling or transformations may improve forecast reliability and uncertainty intervals.