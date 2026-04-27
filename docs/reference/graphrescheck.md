# Check conditions on digraph

Check that a given digraph satisfies the conditions of 'no left to right
edges', 'no cycles', 'valid number of categories' and 'valid variable
names'. Optionally returns the digraph if all checks are passed.

## Usage

``` r
graphrescheck(graphres, ret = FALSE)
```

## Arguments

- graphres:

  An `igraph` object representing a digraph.

- ret:

  A logical value. Default is `FALSE`. Set to `TRUE` to also return
  `graphres` if all checks are passed.

## Value

If `ret=FALSE` (default): `TRUE` if all checks pass; else `FALSE`. If
`ret=TRUE`: `graphres` if all checks pass; else `FALSE`.

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
graphrescheck(graphres = graphres) # TRUE
#> [1] TRUE
```
