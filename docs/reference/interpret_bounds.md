# Convert bounds string to a function

Convert bounds string to a function

## Usage

``` r
interpret_bounds(bounds, parameters)
```

## Arguments

- bounds:

  The bounds element as returned by
  [optimize_effect](https://sachsmc.github.io/causaloptim/reference/optimize_effect_2.md)

- parameters:

  Character vector defining parameters, as returned by
  [analyze_graph](https://sachsmc.github.io/causaloptim/reference/analyze_graph.md)

## Value

A function that takes arguments for the parameters, i.e., the observed
probabilities and returns a vector of length 2: the lower bound and the
upper bound.

## Examples

``` r
b <- graph_from_literal(X -+ Y, Ur -+ X, Ur -+ Y)
V(b)$leftside <- c(0,0,0)
V(b)$latent <- c(0,0,1)
V(b)$nvals <- c(2,2,2)
E(b)$rlconnect <- E(b)$edge.monotone <- c(0, 0, 0)
obj <- analyze_graph(b, constraints = NULL, effectt = "p{Y(X = 1) = 1} - p{Y(X = 0) = 1}")
bounds <- optimize_effect_2(obj)
bounds_func <- interpret_bounds(bounds$bounds, obj$parameters)
bounds_func(.1, .1, .4, .3)
#>   lower upper
#> 1  -0.5   0.5
# vectorized
do.call(bounds_func, lapply(1:4, function(i) runif(5)))
#>       lower       upper
#> 1 -1.429489 -0.42948891
#> 2 -0.914107  0.08589296
#> 3 -1.157299 -0.15729874
#> 4 -1.186872 -0.18687167
#> 5 -1.082417 -0.08241683
```
