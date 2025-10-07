# Measuring Forecasting Ability
- We have the following families of indicators, traditionally,
    - Statistical measures of accuracy
    - Statistical assessments of performance
    - Measures of the capability of predicting turning points
- Statistical measures of accuracy are the well-known ones, e.g. MSE, MAE and, perhaps, Theil's U (this one is seldom discussed)
$$MSE = \frac{1}{h}\sum_{j=1}^{h}(\hat{y}_{T+j} - y_{T+j})^2$$
$$MAE = \frac{1}{h}\sum_{j=1}^{h}|\hat{y}_{T+j} - y_{T+j}|^2$$
$$U = \sqrt{\frac{\sum_{j=1}^{h}(\hat{y}_{T+j} - y_{T+j})}{\sum_{j=1}^{h}{y_{T+j}}^2}}$$
- Clements and Hendry (1993): the RMSE is not invariant to isomorphic transformations of models
    - Can lead to contradictory results when applied to different (but isomorphic) representations of the same model
- Diebold and Lopez (1996): the RMSE depends only on the first two moments of the forecast distribution
    - It will suffer when such distributions are not adequately summarized by only two moments.
- The literature has criticized RMSE also on the grounds of economic considerations
    - Predictive performance should be evaluated via the losses that arise from forecasting errors when certain decisions are made -- Leitch and Tanner (1991), Granger and Pesaran (2000a, 2000b), and the review by Pesaran and Skouras (2002)
        - But other specifications could be considered -- Christoffersen and Diebold (1996) and Mariano (2002)
- Chiefly, the Diebold and Mariano (1995) test

$$\eta^{(1)}_{T+j} \equiv \hat{y}^{(1)}_{T+j} - y_{T+j} \; \text{error from predictor (1)}$$
$$\eta^{(2)}_{T+j} \equiv \hat{y}^{(2)}_{T+j} - y_{T+j} \; \text{error from predictor (2)}$$
$$\text{define } g[\eta^{(k)}_{T+j}] \; \text{a loss function -- e.g. } (\eta^{(k)}_{T+j})^2$$
$$d_{T+j} \equiv g[\eta^{(1)}_{T+j}] - g[\eta^{(2)}_{T+j}]$$
$$\bar{d}_{h} \equiv \frac{1}{h} \sum_{j=1}^{h} d_{T+j}$$
$$\sqrt{h} \, \bar{d}_{h} \xrightarrow{d} \mathcal{N}(0, \sigma_d^2), \quad \text{as } h \to \infty$$
$$\text{Under} \space H_0: E\!\left( g\!\left[ \hat{\varepsilon}^{(1)}_{T+j} \right] \right)
  = E\!\left( g\!\left[ \hat{\varepsilon}^{(2)}_{T+j} \right] \right)$$


The Diebold Mariano test is essentially a test for the null of equal expected loss (so one predictor is as good as the other)

Note the use of a generic loss function.

Required reading: _Forecasting crude oil and refined products volatilities and correlations: New evidence from fractionally integrated multivariate GARCH models_ (Marchese et. al. 2020) 
- **Long-term Models are Superior:** The paper demonstrates that multivariate GARCH models that account for long memory (i.e., the tendency of volatility shocks to persist for a long time) are better at forecasting the volatility and correlation of crude oil and refined products compared to traditional short-memory models.
- **Dynamic Correlations are Crucial:** The study finds that the correlation between crude oil and refined products is not constant but changes over time. Models that capture these dynamic correlations provide more accurate forecasts
- **Asymmetric Effects Matter:** The paper shows the presence of leverage effects, where negative shocks (price drops) have a larger impact on volatility than positive shocks (price increases)
- **Improved Risk Management:** The use of these more advanced models leads to more accurate Value-at-Risk (VaR) forecasts, which is a key tool for risk management. This helps refiners, traders, and other market participants to better manage their price risk exposure.
- **Robustness of Findings:** The paper's conclusions are robust across different market conditions (calm, turbulent, and failry volatile periods) and for various forecasting horizons (1, 5, and 20 days).