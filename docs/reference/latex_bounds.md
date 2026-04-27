# Latex bounds equations

Latex bounds equations

## Usage

``` r
latex_bounds(bounds, parameters, prob.sym = "P", brackets = c("(", ")"))
```

## Arguments

- bounds:

  Vector of bounds as returned by
  [optimize_effect_2](https://sachsmc.github.io/causaloptim/reference/optimize_effect_2.md)

- parameters:

  The parameters object as returned by
  [analyze_graph](https://sachsmc.github.io/causaloptim/reference/analyze_graph.md)

- prob.sym:

  Symbol to use for probability statements in latex, usually "P" or "pr"

- brackets:

  Length 2 vector with opening and closing bracket, usually
  `c("(", ")")`, or `c(" \{", "\}")`

## Value

A character string with latex code for the bounds

## Examples

``` r
b <- graph_from_literal(X -+ Y, Ur -+ X, Ur -+ Y)
V(b)$leftside <- c(0,0,0)
V(b)$latent <- c(0,0,1)
V(b)$nvals <- c(2,2,2)
E(b)$rlconnect <- E(b)$edge.monotone <- c(0, 0, 0)
obj <- analyze_graph(b, constraints = NULL, effectt = "p{Y(X = 1) = 1} - p{Y(X = 0) = 1}")
bounds <- optimize_effect_2(obj)
latex_bounds(bounds$bounds, obj$parameters)
#> [1] "\\[ \n \\mbox{Lower bound} =   -P(X = 1, Y = 0) - P(X = 0, Y = 1) \n \\] \n \\[ \n \\mbox{Upper bound} =   1 - P(X = 1, Y = 0) - P(X = 0, Y = 1) \n \\] \n"
latex_bounds(bounds$bounds, obj$parameters, "Pr")
#> [1] "\\[ \n \\mbox{Lower bound} =   -Pr(X = 1, Y = 0) - Pr(X = 0, Y = 1) \n \\] \n \\[ \n \\mbox{Upper bound} =   1 - Pr(X = 1, Y = 0) - Pr(X = 0, Y = 1) \n \\] \n"
```
