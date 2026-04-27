# Run the optimizer to obtain symbolic bounds

Given an object with the linear programming problem set up, compute the
bounds using rcdd. Bounds are returned as text but can be converted to R
functions using
[interpret_bounds](https://sachsmc.github.io/causaloptim/reference/interpret_bounds.md),
or latex code using
[latex_bounds](https://sachsmc.github.io/causaloptim/reference/latex_bounds.md).

## Usage

``` r
optimize_effect_2(obj, redundant = FALSE)
```

## Arguments

- obj:

  Object as returned by
  [analyze_graph](https://sachsmc.github.io/causaloptim/reference/analyze_graph.md)
  or
  [create_linearcausalproblem](https://sachsmc.github.io/causaloptim/reference/create_linearcausalproblem.md)

- redundant:

  If TRUE, removed redundant constraints as a preprocessing step. Can
  speed things up.

## Value

An object of class "balkebound" that is a list that contains the bounds
and logs as character strings, and a function to compute the bounds

## Examples

``` r
b <- initialize_graph(graph_from_literal(X -+ Y, Ur -+ X, Ur -+ Y))
obj <- analyze_graph(b, constraints = NULL, effectt = "p{Y(X = 1) = 1} - p{Y(X = 0) = 1}")
optimize_effect_2(obj)
#> lower bound =  
#> MAX {
#>   -p10_ - p01_
#> }
#> ----------------------------------------
#> upper bound =  
#> MIN {
#>   1 - p10_ - p01_
#> }
#> 
#> A function to compute the bounds for a given set of probabilities is available in the x$bounds_function element.
```
