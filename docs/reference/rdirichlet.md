# Sample from a Dirichlet distribution

Generate a random vector from the k-dimensional symmetric Dirichlet
distribution with concentration parameter alpha

## Usage

``` r
rdirichlet(k, alpha = 1)
```

## Arguments

- k:

  Length of the vector

- alpha:

  Concentration parameters

## Value

a numeric vector

## Examples

``` r
qvals <- rdirichlet(16, 1)
sum(qvals)
#> [1] 1
```
