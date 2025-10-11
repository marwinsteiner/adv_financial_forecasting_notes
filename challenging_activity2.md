# Challenging Activities Week 2

1. Prove that
   $$Cov(Y_tY_t) = Var(Y_t)$$
   Let $\mu_t = E[Y_t]$
   $$\begin{align}Cov(Y_tY_t) &= E[(Y_t - E[Y_t])(Y_t - E[Y_t])] \\
   (Y_t - E[Y_t])(Y_t - E[Y_t]) &= (Y_t - \mu_t)^2 \\
   Cov(Y_tY_t) &= E[(Y_t - \mu_t)^2] \\
   &= Var(Y_t)
   \end{align}$$

2. Read the paper _Forecasting crude oil and refined products volatilities and correlations: New evidence from
   fractionally integrated multivariate GARCH models_ (Marchese et al., 2020) and infer which other types of
   statistical tests can be used to compare the forecasting performances of different models. What is the difference
   between the SPA test and the MCS and the Diebold-Mariano test?

   Additional statistical tests which can be used:
    - Reality Check Test (White, 2000)
        - Similar to SPA, but uses bootstrapping to test whether any model in a set significantly outperforms a
          benchmark.
        - Controls for data snooping bias.
            - When multiple models are tested on the same data, some may appear to perform better purely by chance,
              increasing the chance of type I error.
            - How it works:
                - Choose a benchmark model; a simple autoregressive one, say.
                - Candidate models: evaluate a set of alternative models against your benchmark
                - Pick a performance metric
                    - Resample the data to simulate the distribution of performance under the null
                    - Calculate the test statistic for each bootstrap sample
                    - Compare the observed performance of the best model to the bootstrap distribution.
                    - If the best model's performance is significantly better than what would be expected under the
                      null, then we can be sure that there is no data snooping, thereby passing the Reality Check.
                    - If not, the model's success may be attributed to data snooping rather than predictive ability.
    - Giacomini-White Test
        - Focuses on conditional predictive ability rather than unconditional accuracy
        - Accounts for time-varying forecast performance and model misspecification.
        - Generalizes the Diebold-Mariano: While DM tests unconditional forecast accuracy, GW adapts to dynamic
          environments and model uncertainty.
            1. Loss Differential:
                - Compute the difference in forecast errors between two models using a loss function (e.g. squared
                  error).
                - $\Delta_{t+h} = L(y_{t+h}, f_{1,t}) - L(y_{t+h}, f_{2,t})$
            2. Regression Framework:
                - Regress the loss differential on lagged information: $\Delta_{t+h} = \phi' X_{t} + \varepsilon_{t+h}$
                - $X_t$ includes variables known at time $t$, such as lagged losses or economic indicators.
            3. Null Hypothesis:
                - $H_0: \space \phi = 0$ - no conditional predictive advantage.
                - Rejecting $H_0$ implies one model is conditionally superior.
            4. Asymptotic Distribution:
                - Uses a chi-squared test statistic.
                - Accounts for serial correlation and estimation uncertainty via HAC standard errors. (The corrected
                  standard errors)
        - Great for evaluating models working with regime-shifting time series.
        - Robust to model misspecifications.
    - Forecast Encompassing Tests
        - Tests whether one model's forecast contains all the relevant information of another.
        - Helps determine if combining forecasts could improve performance.
        - Useful when evaluating ensemble models
            1. Estimate regression using out of sample forecasts.
            2. Test significance of coefficients using standard t-tests or joint F-tests.
            3. Check residuals for autocorrelation and heteroskedasticity.
            4. Use HAC standard errors if you need to.
        - Performs model selection: identifies dominant models in a forecasting ensemble. 
    - Out-of-Sample Likelihood Ratio Tests
        - Compares models based on their likelihood scores on holdout data.
        - Particularly relevant for GARCH-type models where likelihood is well-defined.
            1. Model estimation: fit the model on in-sample data (e.g., time series up to time $T$).
            2. Out of sample likelihood: for each out-of-sample observation $y_{t+1}, y_{t+2}, \dots$, compute:
                $$\log L(y_{t+h} | \hat{\theta})$$
                where $\hat{\theta}$ are the estimated parameters from the in-sample fit.
            3. Sum or average log-likelihoods across the out-of-sample period:
                $$\text{OOS Log-Likelihood} = \sum_{h=1}^{H} \log L(y_{t+h} | \hat{\theta})$$
            4. Model comparison: Compare the out-of-sample likelihood across models. Higher values indicate better predictive fit. Can be formalized using likelihood ratio tests or information criteria like AIC or BIC on the out-of-sample. 
3. Use the EViews work-file on exponential smoothing and run a forecasting comparison of the simple linear regression
   model with the 2 smoothing forecasts we have obtained. Comment on the forecasting abilities of the simple linear
   regression model.
   [Ask about license]

4. How do you assess, using EViews, if the series Portfolio has non-linear dependence over time?
   [Ask about license]