# Simulated JP Morgan jobs
This repository has Python Jupyter Notebooks for four tasks in JP Morgan's job simulation.

# Task 1: estimate daily natural gas price using given 48 data points at the monthly level
Task one provides 48 data points at the monthly level for natural gas prices, and asks the quantitative researcher to estimate the prices in the past and into the future by one year at the daily level. I have explored three different approaches to tackle this problem.
- The decomposition of the time series to trend, seasonal and residual confirms that the residual is white noise. So I fit a model for the trend and seasonality first, and them combine them to construct a model for the original time series. This model has the least error (RMSE, root mean squared error), and the most flexibility to estimate prices at the daily level.
- Use statsmodels' SARIMAX model. This model uses some guesses on the orders of autoregressive, differences, and moving avarage processes and grid search to find the best hyper-parameters. The model's performance is slightly worse than the first approach, but very close. The issue is this model cannot estimate prices at the daily level straightaway.
- Use Facebook (Meta)'s open source package Prophet. This model is the easiest to use, but the performance is not as good as the first two. It cannot estimate prices at the daily level either.

# Task 2: Price a commodity storage contract for natural gas
Task two asks the quantitative researcher to create a contract pricing model based on the natural gas price obtained in task one so that the desk can begin trading with the client. The client wants to start trading as soon as possible. They believe the winter will be colder than expected, so they want to buy gas now to store and sell in winter in order to take advantage of the resulting increase in gas prices. The client may want to choose multiple dates to inject into and withdraw from the storage a set amount of gas. Therefore on top of the natural gas price, other factors / costs need to be taken into account for pricing. These include:
- Injection dates. 
- Withdrawal dates.
- The rate at which the gas can be injected/withdrawn, i.e., how much million MMBtu per day.
- Injection and withdrawal costs.
- The maximum volume that can be stored.
- Storage costs.
- Tranportation costs.