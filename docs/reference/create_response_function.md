# Translate regular DAG to response functions

Translate regular DAG to response functions

## Usage

``` r
create_response_function(graph)
```

## Arguments

- graph:

  An aaa-igraph-package object that represents a directed acyclic graph
  that contains certain edge attributes. The shiny app returns a graph
  in this format and
  [initialize_graph](https://sachsmc.github.io/causaloptim/reference/initialize_graph.md)
  will add them to a regular igraph object with sensible defaults.

## Value

A list of functions representing the response functions

## Examples

``` r
### confounded exposure and outcome
b <- initialize_graph(igraph::graph_from_literal(X -+ Y, Ur -+ X, Ur -+ Y))
create_response_function(b)
#> $X
#> $X$index
#> [1] 0 1
#> 
#> $X$values
#> $X$values[[1]]
#> function () 
#> 0
#> <environment: base>
#> 
#> $X$values[[2]]
#> function () 
#> 1
#> <environment: base>
#> 
#> 
#> $X$matrices
#> $X$matrices[[1]]
#>      X
#> [1,] 0
#> 
#> $X$matrices[[2]]
#>      X
#> [1,] 1
#> 
#> 
#> 
#> $Y
#> $Y$index
#> [1] 0 1 2 3
#> 
#> $Y$values
#> $Y$values[[1]]
#> function (X = NULL) 
#> switch(paste0(X), `0` = 0, `1` = 0)
#> <environment: base>
#> 
#> $Y$values[[2]]
#> function (X = NULL) 
#> switch(paste0(X), `0` = 1, `1` = 0)
#> <environment: base>
#> 
#> $Y$values[[3]]
#> function (X = NULL) 
#> switch(paste0(X), `0` = 0, `1` = 1)
#> <environment: base>
#> 
#> $Y$values[[4]]
#> function (X = NULL) 
#> switch(paste0(X), `0` = 1, `1` = 1)
#> <environment: base>
#> 
#> 
#> $Y$matrices
#> $Y$matrices[[1]]
#>   X Y
#> 1 0 0
#> 2 1 0
#> 
#> $Y$matrices[[2]]
#>   X Y
#> 1 0 1
#> 2 1 0
#> 
#> $Y$matrices[[3]]
#>   X Y
#> 1 0 0
#> 2 1 1
#> 
#> $Y$matrices[[4]]
#>   X Y
#> 1 0 1
#> 2 1 1
#> 
#> 
#> 
```
