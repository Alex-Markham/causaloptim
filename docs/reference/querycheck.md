# Check conditions on query

Given an admissible causal DAG, check that given a causal query
satisfies conditions that guarantee the corresponding causal problem to
be a linear program. Throws error messages detailing any conditions
violated.

## Usage

``` r
querycheck(effecttext, graphres)
```

## Arguments

- effecttext:

  A string representing a causal query.

- graphres:

  An `igraph` object representing a digraph.

## Value

`TRUE` if `effecttext` is parsable, contains only variables in
`V(graphres)` and satisfies conditions for linearity; else `FALSE`.

## Examples

``` r
graphres <- graph_from_literal(X -+ Y, X -+ M, M -+ Y, Ul -+ X, Ur -+ M, Ur -+ Y)
V(graphres)$leftside <- c(1, 0, 0, 1, 0)
V(graphres)$latent <- c(0, 0, 0, 1, 1)
V(graphres)$nvals <- c(2, 2, 2, 2, 2)
V(graphres)$exposure <- c(0, 0, 0, 0, 0)
V(graphres)$outcome <- c(0, 0, 0, 0, 0)
E(graphres)$rlconnect <- c(0, 0, 0, 0, 0, 0)
E(graphres)$edge.monotone <- c(0, 0, 0, 0, 0, 0)
effecttext <- "p{Y(M(X = 0), X = 1) = 1} - p{Y(M(X = 0), X = 0) = 1}"
querycheck(effecttext = effecttext, graphres = graphres) # TRUE
#> [1] TRUE
```
