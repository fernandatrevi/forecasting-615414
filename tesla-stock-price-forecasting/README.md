# Tesla Stock Price Forecasting with Time Series Models

An academic time series forecasting project comparing Holt-Winters exponential smoothing, additive and multiplicative decomposition, and ARIMA for Tesla (TSLA) closing prices.

## Project objective

Analyze historical daily trading-session closing prices from January 2020 through December 2022 and produce a seven-trading-session forecast. The study compares the predictive performance and bias of different time series methods.

## Models evaluated

- Holt-Winters: additive trend / additive seasonality
- Holt-Winters: additive trend / multiplicative seasonality
- Holt-Winters: multiplicative trend / additive seasonality
- Holt-Winters: multiplicative trend / multiplicative seasonality
- Additive seasonal decomposition with a trend extrapolation
- Multiplicative seasonal decomposition with a trend extrapolation
- Automatically selected ARIMA

A five-session seasonal period is used as an experimental assumption representing a trading week; it is **not evidence of statistically significant seasonality**.

## Evaluation

The original classroom evaluation uses a chronological 80% training / 20% test split (604 / 152 sessions). A separate seven-session holdout validation is used to examine the actual forecasting horizon. Metrics include RMSE, MAPE, and MPE.

### Original 152-session test results

| Model | RMSE | MAPE | MPE |
| --- | ---: | ---: | ---: |
| Holt-Winters (add, add) | 58.43 | 24.06% | -5.88% |
| Holt-Winters (add, mul) | 58.33 | 24.00% | -5.58% |
| Holt-Winters (mul, add) | 55.75 | 20.09% | 6.56% |
| Holt-Winters (mul, mul) | 55.59 | 20.06% | 6.40% |
| Additive decomposition | 183.02 | 84.10% | -84.10% |
| Multiplicative decomposition | 183.02 | 84.09% | -84.09% |
| ARIMA (0, 1, 0) | 55.52 | 20.21% | 5.82% |

ARIMA has the lowest RMSE in this particular 152-session evaluation, while multiplicative/multiplicative Holt-Winters has the lowest MAPE. These results do not establish superiority across all prediction horizons.

## Statistical analysis

The notebook examines the time series plot, autocorrelation function, periodogram, Augmented Dickey–Fuller (ADF), and KPSS tests. With `regression='ct'`, KPSS tests stationarity around a deterministic trend rather than testing whether a trend exists.

## Reproducibility

The original work was developed in Google Colab using Python, pandas, statsmodels, pmdarima, matplotlib, scipy and scikit-learn. The notebook is included in this folder with its code and explanations; saved notebook outputs have been cleared for public sharing.

To reproduce it, install the libraries from `requirements.txt`, open `TSLA_Pronostico_Modelos_TS.ipynb` in Google Colab, and upload the historical workbook as `TSLA_acciones.xlsx` to the Colab working directory. The workbook is not hosted here; without it, the notebook cannot execute from start to finish. Run all notebook cells in order.

## Limitations

- Historical results are based on data ending in December 2022, not current TSLA prices.
- The original 152-step evaluation is not identical to seven-step forecasting.
- The data do not show a clearly established five-session seasonal pattern.
- Decomposition forecasts extrapolate a historical trend and perform poorly in the test period.
- Model predictions are educational demonstrations, not financial advice.

## Project status

English documentation, requirements, and the cleaned Colab notebook are committed. The Excel source workbook must be provided separately to run the analysis.
