# Simulate bounds

Run a simple simulation based on the bounds. For each simulation, sample
the set of counterfactual probabilities from a uniform distribution,
translate into a multinomial distribution, and then compute the
objective and the bounds in terms of the observable variables.

## Usage

``` r
simulate_bounds(obj, bounds, nsim = 1000)
```

## Arguments

- obj:

  Object as returned by
  [analyze_graph](https://sachsmc.github.io/causaloptim/reference/analyze_graph.md)

- bounds:

  Object as returned by
  [optimize_effect_2](https://sachsmc.github.io/causaloptim/reference/optimize_effect_2.md)

- nsim:

  Number of simulation replicates

## Value

A data frame with columns: objective, bound.lower, bound.upper

## Examples

``` r
b <- initialize_graph(graph_from_literal(X -+ Y, Ur -+ X, Ur -+ Y))
obj <- analyze_graph(b, constraints = NULL, effectt = "p{Y(X = 1) = 1} - p{Y(X = 0) = 1}")
bounds <- optimize_effect_2(obj)
simulate_bounds(obj, bounds, nsim = 5)
#>     objective bound.lower bound.upper
#> 1  0.29136748  -0.3729966   0.6270034
#> 2 -0.06331950  -0.4469019   0.5530981
#> 3 -0.26156878  -0.6549510   0.3450490
#> 4 -0.15481633  -0.7029335   0.2970665
#> 5 -0.03916506  -0.4966841   0.5033159
```
