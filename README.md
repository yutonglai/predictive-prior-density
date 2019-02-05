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

From Bayes’ theorem, we know that
g(λ|y) = p(λ)f(y|λ)/p(y);
and therefore, the prior predictive density of y (before any data are collected) can be
obtained as
p(y) = p(λ)f(yjλ)/g(λjy)

Consider two hospitals:
• Hospital A is a small hospital that has one death y = 1 and an exposure equal to
e = 66.
• Hospital B is a large hospital with y = 4 and e = 1767.

Compare the prior and posterior distributions in a plot for the two hospitals.
In both hospitals, compute the prior predictive probabilities of observing y = 0; 1; 2; :::; 10
deaths given the respective exposures.

#### Hospital A with one death y=1 and e=66
    alpha = 16
    beta = 15174
    yobs.A = 1
    ex.A = 66
    num = 0:10
    lam.hosp = alpha/beta
    py.A = dpois(num,lam.hosp*ex.A)*dgamma(lam.hosp, shape=alpha, rate=beta)/dgamma(lam.hosp,shape=alpha+num,rate=beta+ex.A)
    round(cbind(num,py.A),3)
    
#### Output:
          num  py.A
     [1,]   0 0.933
     [2,]   1 0.065
     [3,]   2 0.002
     [4,]   3 0.000
     [5,]   4 0.000
     [6,]   5 0.000
     [7,]   6 0.000
     [8,]   7 0.000
     [9,]   8 0.000
    [10,]   9 0.000
    [11,]  10 0.000
    
#### Hospital B with one death y=4 and e=1767
    yobs.B = 4
    ex.B = 1767
    py.B = dpois(num,lam.hosp*ex.B)*dgamma(lam.hosp, shape=alpha, rate=beta)/dgamma(lam.hosp,shape=alpha+num,rate=beta+ex.B)
    round(cbind(num,py.B),3)
    
#### Output:
          num  py.B
     [1,]   0 0.172
     [2,]   1 0.286
     [3,]   2 0.254
     [4,]   3 0.159
     [5,]   4 0.079
     [6,]   5 0.033
     [7,]   6 0.012
     [8,]   7 0.004
     [9,]   8 0.001
    [10,]   9 0.000
    [11,]  10 0.000
    
#### Prior and post plots for Hospital A and B
    par(mfrow = c(2, 1))
    lam.A = rgamma(1000, shape = alpha + yobs.A, rate = beta + ex.A)
    plot(density(lam.A), main="HOSPITAL A",xlab="Lambda A", lwd=3)
    curve(dgamma(x, shape = alpha, rate = beta), add=TRUE)
    legend("topright",legend=c("prior","posterior"),lwd=c(1,3))
    lam.B = rgamma(1000, shape = alpha + yobs.B, rate = beta + ex.B)
    plot(density(lam.B), main="HOSPITAL B",xlab="Lambda B", lwd=3)
    curve(dgamma(x, shape = alpha, rate = beta), add=TRUE)
    legend("topright",legend=c("prior","posterior"),lwd=c(1,3))
    
    
