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

# Task 3: Build a predictive model to predict the potential loss from loan borrowers
Task three asks the quantitative researcher to build a predictive model to predict the potential loss from loan borrowers. The risk manager has collected data on the loan borrowers. The data is in tabular format, with each row providing details of the borrower, including their income, total loans outstanding, and a few other metrics. There is also a column indicating if the borrower has previously defaulted on a loan. You must use this data to build a model that, given details for any loan described above, will predict the probability that the borrower will default (also known as PD: the probability of default). Use the provided data to train a function that will estimate the probability of default for a borrower. Assuming a recovery rate of 10%, this can be used to give the expected loss on a loan.

- We should produce a function that can take in the properties of a loan and output the expected loss.
- We can explore any technique ranging from a simple regression or a decision tree to something more advanced. We can also use multiple methods and provide a comparative analysis.

# Task 4: Quantize FICO data to predict defaults
From taks 3, we are familiar with the model to predict default probability and potential losses. The personal loans and risk team is using the model as a guide to loss provisions for the upcoming year. The team now wants to look at their mortgage book. They suspect that FICO scores will provide a good indication of how likely a customer is to default on their mortgage. The team wants to build a machine learning model that will predict the probability of default. The architecture they are using requires categorical data. As FICO ratings can take integer values in a large range, they will need to be mapped into buckets. They ask if we can find the best way of doing this to analyze the data.

A FICO score is a standardized credit score created by the Fair Isaac Corporation (FICO) that quantifies the creditworthiness of a borrower to a value between 300 to 850, based on various factors. FICO scores are used in 90% of mortgage application decisions in the United States. The risk manager provides FICO scores for the borrowers in the bank’s portfolio and wants the quantitative researcher to construct a technique for predicting the PD (probability of default) for the borrowers using these scores. 