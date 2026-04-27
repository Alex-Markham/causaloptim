# Initialize an igraph object for use with causaloptim

Checks for required attributes and adds defaults if missing

## Usage

``` r
initialize_graph(graph)
```

## Arguments

- graph:

  An object of class igraph

## Value

An igraph with the vertex attributes leftside, latent, and nvals, and
edge attributes rlconnect and edge.monotone

## Examples

``` r
b <- igraph::graph_from_literal(X -+ Y)
b2 <- initialize_graph(b)
V(b2)$nvals
#> [1] 2 2
```
