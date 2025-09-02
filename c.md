## List of Strategies

+ List of the strategies that will be attempted to be implemented for positive results
    + Combinations will also be used of several of these
    + Cointegration
    + Mean reversion
    + Momentum trending
    + PCA
    + Correlation
    + Note an overall filter of optimization can be used in all these situations for parameters

## Approach

+ Backtesting on roughly 500 data points of several frequencies, parameter optimization on roughly 200 data points, and testing on 100 data points
+ This will constitute one backtest and at least 4-5 such backtests will be done with the use of the walk-forward analysis by roughly 100 points.
+ Data extraction will be done by a custom function
    + `get_time_period(stock_list,custom_data=True,num_data_points=num_points,shift=r,freq='freq')` -> `pd.Dataframe`
    + `stock_list`
        + list of stocks to get the closing
    + `custom_data`
        + decides if the data is extracted live or from already stored data
    + `num_data_points`
        + number of data points to obtain
    + `shift`
        + shifts the data by a certain number of points to basically allow for extraction from various time periods
    + returns a Dataframe with the columns being the stocks and the indices being the datetimes

## Tools

+ Pandas Series/Dataframe
    + For labeled data and for organization purposes within the execution mostly
+ Optuna
    + For Bayesian optimization mostly of parameters
+ VectorBt
    + For simulation of day and intraday trading
+ Multiprocessing.pool
    + For parallel processing
+ Statsmodels
    + For simple execution of filters
+ Plotly
    + For easy data visualization