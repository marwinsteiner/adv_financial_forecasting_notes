## Bits from the lecture

Models generally seek to serve the data, not the other way around.

The MA process always predicts covariance stationary outcomes.

The AR process doesn't necessarily do the same. We need to ensure that the absolute value of rho is smaller than 1,
implying rho is between -1 and 1. If and only if this is the case, AR will predict a covariance stationary series. If
the rho is exactly 1 or -1, we get a unit root, which is a tool frequently used in financial engineering.

We can only use AR for forecasting if rho is between -1 and 1. Practically, our rho will usually sit very close to (but
not exactly) 1.

ARFIMA models were invented to fix this shortcoming of the ARMA model, where the decay is hyperbolic instead of
exponential. Hyperbolic is different from exponential in that a hyperbolic increase starts from a defined point, whereas
an exponential increase has no defined point from which it starts.

User guide 2 EViews help: we get a command for the ARFIMA model.

ARFIMA belongs to the family of Fractionally Integrated Models, or long memory processes.

We can still look at the p values of the phi hat here to figure out if the ARFIMA does a good job of estimation.

To estimate an ARFIMA model, you just include the character "d" in your model specification and you get an ARFIMA. Then
you can look at your p-value of the d parameter and figure out if this is significant or not. If it isn't, then you can
conclude that the ARFIMA is not better than the alternative.

In an ARFIMA, the PACF is exponentially decaying.

ARFIMA model does not, by default, refer to a non-stationary process. It's more about how long it takes to get to the
long-run mean.

Information criteria are used to understand the level of parsimony of the model.

ICs are for time series models only, and let you choose between different models once they have successfully passed
model diagnostic tests.

In general, if we favor models with the AIC, we favor models which are heavily parametrized. However, in the SBIC, the
penalty dies off more slowly. The more slowly your penalty ties off, the stricter is your information criterion, so the
Hannan Quinn is the most strict whereas the AIC is the least strict. In general, it is ok to select based on the SBIC,
and generally all three move in the same direction. Generally, selecting on the basis of the HQIC requires a very large
sample indeed. You choose the model which has the smallest absolute value of the information criterion. Just take an
absolute value to be sure, because different software calculate it with different signs.

We can do automatic forecasting with ARIMA model, and enter an information criterion to measure by. HOWEVER, this
automatic forecasting does NOT do post estimation diagnostics, which we ABSOLUTELY need to do ourselves before we can do
this.

The MA proces dies off when you reach your number of lags in the specification. Beyond that, there is convergence to the
long term mean. In other words, you need as much data as you need to forecast, otherwise the model says the outcome is
the long run mean. That's all we can get out of the model. 

Find out how to open up range in EViews to predict portfolio using an AR(1) to January 2012.