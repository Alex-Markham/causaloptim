# Parse text that defines a causal effect

Parse text that defines a causal effect

## Usage

``` r
parse_effect(text)
```

## Arguments

- text:

  Character string

## Value

A nested list that contains the following components:

- vars:

  For each element of the causal query, this indicates potential
  outcomes as names of the list elements, the variables that they depend
  on, and the values that any variables are being fixed to.

- oper:

  The vector of operators (addition or subtraction) that combine the
  terms of the causal query.

- values:

  The values that the potential outcomes are set to in the query.

- pcheck:

  List of logicals for each element of the query that are TRUE if the
  element is a potential outcome and FALSE if it is an observational
  quantity.

## Examples

``` r
effectt <- "p{Y(X = 1) = 1} - p{Y(X = 0) = 1}"
parse_effect(text = effectt)
#> $vars
#> $vars[[1]]
#> $vars[[1]]$Y
#> $vars[[1]]$Y$X
#> [1] 1
#> 
#> 
#> 
#> $vars[[2]]
#> $vars[[2]]$Y
#> $vars[[2]]$Y$X
#> [1] 0
#> 
#> 
#> 
#> 
#> $oper
#> $oper[[1]]
#> [1] "-"
#> 
#> 
#> $values
#> $values[[1]]
#> $values[[1]]$Y
#> [1] 1
#> 
#> 
#> $values[[2]]
#> $values[[2]]$Y
#> [1] 1
#> 
#> 
#> 
#> $pcheck
#> $pcheck[[1]]
#> [1] TRUE
#> 
#> $pcheck[[2]]
#> [1] TRUE
#> 
#> 
```
