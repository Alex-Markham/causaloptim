# Check conditions on causal problem

Check that a given causal problem (a causal DAG together with a causal
query) satisfies conditions that guarantee that the optimization problem
is linear.

## Usage

``` r
causalproblemcheck(digraph, query)
```

## Arguments

- digraph:

  An `igraph` object representing a digraph.

  Expected vertex attributes: `leftside`, `latent` and `nvals`.

  Optional vertex attributes: `exposure` and `outcome`.

  Expected edge attributes: `rlconnect` and `edge.monotone`.

- query:

  A string representing a causal query / effect.

## Value

`TRUE` if conditions are met; `FALSE` otherwise.

## Examples

``` r
b <- graph_from_literal(X - +Y, Ur - +X, Ur - +Y)
V(b)$leftside <- c(0, 0, 0)
V(b)$latent <- c(0, 0, 1)
V(b)$nvals <- c(2, 2, 2)
V(b)$exposure <- c(1, 0, 0)
V(b)$outcome <- c(0, 1, 0)
E(b)$rlconnect <- c(0, 0, 0)
E(b)$edge.monotone <- c(0, 0, 0)
effectt <- "p{Y(X=1)=1}-p{Y(X=0)=1}"
causalproblemcheck(digraph = b, query = effectt)
#> [1] TRUE
```
