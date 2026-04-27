# Check constraints

Check that a user-provided constraint is parsable, has valid variables
and relations.

## Usage

``` r
constraintscheck(constrainttext, graphres)
```

## Arguments

- constrainttext:

  A string representing a constraint.

- graphres:

  An `igraph` object representing a DAG.

## Value

`TRUE` if all check pass; else `FALSE`.

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
constrainttext <- "X(Z = 1) >= X(Z = 0)"
constraintscheck(constrainttext = constrainttext, graphres = graphres) # TRUE
#> [1] TRUE
```
