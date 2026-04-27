# Define default effect for a given graph

Define default effect for a given graph

## Usage

``` r
get_default_effect(graphres)
```

## Arguments

- graphres:

  The graph object, should have vertex attributes "outcome" and
  "exposure"

## Value

A string that can be passed to
[parse_effect](https://sachsmc.github.io/causaloptim/reference/parse_effect.md)

## Examples

``` r
graphres <- graph_from_literal(Z -+ X, X -+ Y, Ul -+ Z, Ur -+ X, Ur -+ Y)
V(graphres)$leftside <- c(1, 0, 0, 1, 0)
V(graphres)$latent <- c(0, 0, 0, 1, 1)
V(graphres)$nvals <- c(3, 2, 2, 2, 2)
V(graphres)$exposure <- c(0, 1, 0, 0, 0)
V(graphres)$outcome <- c(0, 0, 1, 0, 0)
E(graphres)$rlconnect <- c(0, 0, 0, 0, 0)
E(graphres)$edge.monotone <- c(0, 0, 0, 0, 0)
get_default_effect(graphres = graphres) == "p{Y(X = 1)=1} - p{Y(X = 0)=1}" # TRUE
#> [1] TRUE
```
