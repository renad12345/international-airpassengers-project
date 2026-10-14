# Final Project Report: Forecasting International Air Passengers

## 1. The Recommendation

We recommend selecting AutoARIMA as the preferred forecasting model based on its performance in rolling-origin validation. It reduces the Mean Absolute Scaled Error (MASE) by approximately 63% compared with the Seasonal Naive baseline.

- **Key Metric:** AutoARIMA achieved a mean MASE of **0.442** across 8 rolling-origin validation windows, each with a 12-month forecast horizon, compared with **1.194** for Seasonal Naive.

## 2. Prediction Intervals and Coverage

We evaluated prediction intervals at a target coverage level of **80%**.

- **AutoARIMA:** Achieved an empirical coverage of **69.79%**, below the target level.
- **Seasonal Naive:** Achieved an empirical coverage of **51.04%**, substantially below the target level.

These results indicate that both models' prediction intervals undercovered the observed values, with AutoARIMA performing better. Further calibration may be needed to bring empirical coverage closer to the nominal 80% level.

**Performance Spread (Min/Max MASE):**
- **Best Fold (Minimum MASE):** AutoARIMA achieved 0.330, compared with 0.412 for Seasonal Naive.
- **Worst Fold (Maximum MASE):** AutoARIMA achieved 1.594, compared with 1.959 for Seasonal Naive.

## 3. Residual Analysis

### Seasonal Naive Baseline

The in-sample residuals for the Seasonal Naive model can be calculated as:

\[
e_t = y_t - y_{t-12}
\]

An upward trend in these residuals and significant autocorrelation at early lags would suggest that the baseline does not adequately capture the series' growth pattern and temporal dependence. These patterns should be confirmed using residual plots and autocorrelation diagnostics.

### AutoARIMA Model

AutoARIMA is designed to capture temporal dependence and trends through its autoregressive, differencing, and moving-average components. Its residuals should be examined to determine whether substantial autocorrelation remains.

If the residuals have approximately zero mean and negligible autocorrelation, this would support the adequacy of the fitted model. However, these properties should be verified using residual diagnostics, such as the residual ACF and the Ljung-Box test, rather than assumed.

## 4. One Proposed Improvement

**Proposed Change:** Investigate the inclusion of relevant exogenous variables, such as jet fuel prices or global economic indicators, provided that reliable monthly data are available.

**Expected Impact:** International passenger traffic may respond to changes in economic conditions and airline operating costs. Incorporating relevant external predictors could improve forecast accuracy and help explain variations not captured by the historical passenger series alone.

The impact should be evaluated through rolling-origin validation against the current AutoARIMA model, using the same forecast horizons and evaluation metrics. The additional variables should be retained only if they produce consistent out-of-sample improvements.
