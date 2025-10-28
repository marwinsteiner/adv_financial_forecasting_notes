## Bits from the Lecture

Remember that $E(y_t)$ is the long ru mean, and $E(y_t | y_{t-1})$ is the long run mean. The existence of long run
moments does not imply the non-existence of breaks in the time series.

If the break lasts only for a few years, then the process reverts to the originial mean. We call this a regime-switch.
If the break is permanent, (for good), then the series can still be covariance stationary, but the long term mean will
no longer be the same.

Essentially it's important to distinguish between breaks and regime-switches. Breaks permanently change the level of the
series. It's a one-off event. In general, financial markets display regime switches. Meaning there is a dramatic event
which temporarily shifts away from the long run mean, but the short run mean reverts to the long run mean eventually.

If we are looking at a time series, we need to understand whether we have breaks or regime switches in our time series.
This is important, because sometimes the presence of breaks or regime switches are confuddled with non-stationarity.
This is not the case. Just because there are regime switches does not imply non-stationarity a priori.

Because most of the models we consider are for short-run forecasting, most of the time we have covariance stationarity.
But sometimes this idea breaks down.

The first one we really fear is a unit root process. It implies that one fo the lagged coefficients are exactly 1. (what
coeffs? ask.) This is essentially saying that our long run variance is not constant, which is very bad.

The second one we fear is a deterministic trend process. It violates the covariance stationarity condition, that the
long run mean does not depend on time. But in a deterministic trend process like the one below:
$$y = \alpha + \beta t + u_t$$
If we take the expectation,
$$E(y = \alpha + \beta t + u_t)$$
The expectation of a constant is the constant, and the expectation of a random variable is 0, so we get
$$y = \alpha + \beta t$$
Meaning the long run mean depends on time, which is a direct violation of the condition of covariance stationarity,
which does NOT depend on time.

A process is nonstationary if it violates any covariance stationarity conditions. Once we identify what causes the
violation, we can simply remove the time trend.

We can restore covariance stationarity by regressing our $y_t$ on whatever time trend we have, then extract the
residuals, because the residuals are what are all non-time-dependent components, and the residuals will be covariance
stationary, because the residuals do not depend on time.

This is how we can get back a covariance stationary process from a nonstationary process.

Students tend to think that if there is a nonstationary trend, that if you take logs you can make a stationary trend.
This is nonsense.

If you take logs of a nonstationarity, stationarity does not magically appear. The way to get rid of type 1
nonstatinonarity, the way you do it is to take the difference (residuals). Generally, we use log returns in finance but
this alone does not remove nonstationarity. It's the fact that we use the differences.

We use log returns because we are using financial data. But the fact that we are using log returns does not remove
nonstationarity. Simple returns also removes nonstationarity. It's the fact that we are taking differences, completely
irrespective of whether we do this in level or in log terms, which results in covariance stationarity. This is a
technical but crucial point.

Anything which is stationary, is called integrated of order zero, denoted $I(0)$. If you need to take the first
difference to get back to covariance stationarity, you call it $I(1)$ integrated of order 1. There are cases where you
need to integrate of order 2.

### Testing for Unit Roots

The early and pioneering work on testing for a unit root in time series was done by Dickey and Fuller in the 70s. The
basic objective of the test is to test the null hypothesis that $\phi = 1$ in:
$$y_t = \phi y_{t-1} + u_t$$
against the one sided alternative $\phi < 1$. So we have
$$\begin{align}
&H_0: \space \phi = 1 \\
&H_1: \space -1 \leq \phi \leq 1 \\
\end{align}
$$

We usually use the regression:
$$\Delta y_t = \psi y_{t - 1} + u_t$$
So that a test of $\phi=1$ is equivalent to a test of $\psi = 0$, since $\psi = \phi - 1$.

We get there by
[derivation goes here see flipchart]

Never ever, ever use a correlogram by eyeballing to determine whether series is stationary.

We can not ever trust that a time series is covariance stationary. We have to test for it. Generally speaking prices are
not covariance stationary, but it can happen. We can not assume they are not stationary a priori, we have to test for
it. The smart approach is to use returns and retroactively decide whether you can work with prices or not.

We use a very stringent level of significance if we test for a unit root. We have to be as sure as possible. We
generally know time series have a unit root, but we have to test for it!

We will find out how to test for unit root where under the alternative we have regime switches.