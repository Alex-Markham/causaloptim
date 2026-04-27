# Plot the analyzed graph object

Special plotting method for igraphs of this type

## Usage

``` r
plot_graphres(graphres)
```

## Arguments

- graphres:

  an igraph object

## Value

None

## See also

[plot.linearcausalproblem](https://sachsmc.github.io/causaloptim/reference/plot.linearcausalproblem.md)
which plots a graph with attributes

## Examples

``` r
b <- graph_from_literal(X -+ Y, Ur -+ X, Ur -+ Y)
V(b)$leftside <- c(0,0,0)
V(b)$latent <- c(0,0,1)
V(b)$nvals <- c(2,2,2)
V(b)$exposure <- c(1,0,0)
V(b)$outcome <- c(0,1,0)
E(b)$rlconnect <- c(0,0,0)
E(b)$edge.monotone <- c(0,0,0)
plot(b)
```
