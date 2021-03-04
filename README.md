## Mean-VaR Portfolio Optimization via Probabilistic Emprical Return Distribution Estimation and Mixed-Integer Linear Programming

In the Jupyter notebook (.ipynb) in this repository, we provide an alternative to the popular modern portfolio theory (MPT) approach to optimizing asset allocations. In contrast to MPT, where financial risk is modelled by the volatility, i.e. standard errors, of the predicted returns, we choose to characterize this risk more explicitly by predicting an empirical joint distribution of returns and formulating the optimization problem with the objective to choose asset allocations to maximize the mean of this distribution and with the constraints that the choice of asset allocation ensures that certain values at risk (VaR) measured on this empirical distritbuion may not be violated. The main reason for this approach is to address one of the major drawbacks of MPT, namely not necessarily capturing the behvaior of the possibly heavy tails of the return distribution, thus underestimating the actual risk of an asset.

The overall approach can be summarized as follows:

We build a time series model based on historical asset returns, such that the residual errors of the model are independently and identically distributed (i.i.d.).
We use the model and the residual errors to generate bootstrapped predictions, i.e. predicting the next return value using the time series model and randomly sampling from the i.i.d. residual errors. In partciluar, making such predictions repetitively, we can generate a number of sample paths. The cumulative returns of each sample path can then be combined into an empirical distribution of predicted returns.
We formulate a mixed integer linear programming (MILP) problem that uses the empirical distribution of predicted returns to find the asset allocation that maximizes the mean of this distribution subject to one or several VaR constraints.
