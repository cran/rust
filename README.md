
<!-- README.md is generated from README.Rmd. Please edit that file -->
rust: ratio-of-uniforms simulation with transformation
------------------------------------------------------

### What does rust do?

The `rust` package implements the multivariate generalized ratio-of-uniforms method of simulating random variates from a d-dimensional continuous distribution. The user specifies (the log of) a positive target function `f` that is proportional to the density function of the distribution.

### A simple example

we use the main function `ru` is used to simulate a sample of size 1000 from a two-dimensional standard normal distribution with strong positive correlation between the components. Of course, this particular example is purely illustrative: there are better ways to simulate from a multivariate normal distribution.

``` r
rho <- 0.9
covmat <- matrix(c(1, rho, rho, 1), 2, 2)
log_dmvnorm <- function(x, mean = rep(0, d), sigma = diag(d)) {
  x <- matrix(x, ncol = length(x))
  d <- ncol(x)
  - 0.5 * (x - mean) %*% solve(sigma) %*% t(x - mean)
}
x <- ru(logf = log_dmvnorm, sigma = covmat, d = 2, n = 1000, init = c(0, 0))
```

### Installation

To get the current released version from CRAN:

``` r
install.packages("rust")
```

### Vignette

See `vignette("rust-vignette", package = "rust")` for an overview of the package.
