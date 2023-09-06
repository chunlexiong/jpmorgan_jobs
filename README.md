# Simulated JP Morgan jobs
This repository has Python Jupyter Notebooks for four tasks in JP Morgan's job simulation.

# Task 1: estimate daily natural gas price using given 48 data points at the monthly level
Task one provides 48 data points at the monthly level for natural gas prices, and asks the quantitative researcher to estimate the prices in the past and into the future by one year at the daily level. I have explored three different approaches to tackle this problem.
- The decomposition of the time series to trend, seasonal and residual confirms that the residual is white noise. So I fit a model for the trend and seasonality first, and them combine them to construct a model for the original time series. This model has the least error (RMSE, root mean squared error), and the most flexibility to estimate prices at the daily level.
- Use statsmodels' SARIMAX model. This model uses some guesses on the orders of autoregressive, differences, and moving avarage processes and grid search to find the best hyper-parameters. The model's performance is slightly worse than the first approach, but very close. The issue is this model cannot estimate prices at the daily level straightaway.
- Use Facebook (Meta)'s open source package Prophet. This model is the easiest to use, but the performance is not as good as the first two. It cannot estimate prices at the daily level either.