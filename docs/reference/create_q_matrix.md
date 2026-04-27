# Translate response functions into matrix of counterfactuals

Translate response functions into matrix of counterfactuals

## Usage

``` r
create_q_matrix(respvars, right.vars, cond.vars, constraints)
```

## Arguments

- respvars:

  A list of functions as returned by
  [create_response_function](https://sachsmc.github.io/causaloptim/reference/create_response_function.md)

- right.vars:

  Vertices of graph on the right side

- cond.vars:

  Vertices of graph on the left side

- constraints:

  A vector of character strings that represent the constraints

## Value

A list of 3 data frames of counterfactuals and their associated labels

## Examples

``` r
graphres <- initialize_graph(graph_from_literal(Z -+ X, X -+ Y, Ul -+ Z, Ur -+ X, Ur -+ Y))
constraints <- "X(Z = 1) >= X(Z = 0)"
cond.vars <- V(graphres)[V(graphres)$leftside == 1 & names(V(graphres)) != "Ul"]
right.vars <- V(graphres)[V(graphres)$leftside == 0 & names(V(graphres)) != "Ur"] 
respvars <- create_response_function(graphres)
create_q_matrix(respvars, right.vars, cond.vars, constraints)
#> $q.vals
#>    X Y
#> 1  0 0
#> 2  2 0
#> 3  3 0
#> 4  0 1
#> 5  2 1
#> 6  3 1
#> 7  0 2
#> 8  2 2
#> 9  3 2
#> 10 0 3
#> 11 2 3
#> 12 3 3
#> 
#> $q.vals.all
#>    X Y Z
#> 1  0 0 0
#> 2  2 0 0
#> 3  3 0 0
#> 4  0 1 0
#> 5  2 1 0
#> 6  3 1 0
#> 7  0 2 0
#> 8  2 2 0
#> 9  3 2 0
#> 10 0 3 0
#> 11 2 3 0
#> 12 3 3 0
#> 13 0 0 1
#> 14 2 0 1
#> 15 3 0 1
#> 16 0 1 1
#> 17 2 1 1
#> 18 3 1 1
#> 19 0 2 1
#> 20 2 2 1
#> 21 3 2 1
#> 22 0 3 1
#> 23 2 3 1
#> 24 3 3 1
#> 
#> $q.vals.all.lookup
#> [1] Y   Z   X.x X.y
#> <0 rows> (or 0-length row.names)
#> 
```
