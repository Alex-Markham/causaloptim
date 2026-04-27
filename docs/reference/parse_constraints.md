# Parse text that defines a the constraints

Parse text that defines a the constraints

## Usage

``` r
parse_constraints(constraints, obsnames)
```

## Arguments

- constraints:

  A list of character strings

- obsnames:

  Vector of names of the observed variables in the graph

## Value

A data frame with columns indicating the variables being constrained,
what the values of their parents are for the constraints, and the
operator defining the constraint (equality or inequalities).

## Examples

``` r
constrainttext <- "X(Z = 1) >= X(Z = 0)"
obsnames <- c("Z", "X", "Y")
parse_constraints(constraints = constrainttext, obsnames = obsnames)
#>   leftout rightout operator leftcond rightcond
#> 1       X        X       >=      Z=1       Z=0
```
