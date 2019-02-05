# predictive-prior-density
If we know the posterior density, then we can derive the predictive prior dentsity (before any data are collected)

#### Background
In hospitalswith certain characteristics (e.g., average age of patients, socio-economic status of patients,
number of beds, etc.) it is possible to estimate the expected mortality rate within 30-days of
heart transplant surgery. We call those expected mortalities ei. If for a sample of hospitals
we observe the number of transplant patients that die within 30 days yi, the classical
likelihood estimate of the mortality rate per unit of exposure e is given by λ^ = y=e. The
underlying probability model is that the number of deaths y follows a Poisson distribution
with mean eλ.

The classical estimate fails when y is small. A better alternative is to incorporate information about mortality rate via a prior gamma distribution with parameters α; β. Suppose
that from an earlier sample of 10 hospitals, we know that reasonable values for α; β are 16
and 15174, respectively.

Consider a hospital where we observe y deaths and an exposure equal to e. The gamma
prior is conjugate to the Poisson likelihood, and therefore the posterior g(λjy; e) is also
gamma(α + y; β + e)

