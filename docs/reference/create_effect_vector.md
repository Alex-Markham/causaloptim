# Translate target effect to vector of response variables

Translate target effect to vector of response variables

## Usage

``` r
create_effect_vector(causal_model, effect)
```

## Arguments

- causal_model:

  An object of class "causalmodel" as produced by
  [create_causalmodel](https://sachsmc.github.io/causaloptim/reference/create_causalmodel.md)

- effect:

  Effect list, as returned by
  [parse_effect](https://sachsmc.github.io/causaloptim/reference/parse_effect.md)

## Value

A list with the target effect in terms of qs

## Examples

``` r
graph <- initialize_graph(graph_from_literal(Z -+ X, X -+ Y, Ul -+ Z, Ur -+ X, Ur -+ Y))
constraints <- "X(Z = 1) >= X(Z = 0)"
effectt = "p{Y(X = 1) = 1} - p{Y(X = 0) = 1}"
p.vals <- expand.grid(Z = 0:1, X = 0:1, Y = 0:1)
prob.form <- list(out = c("X", "Y"), cond = "Z")
effect <- parse_effect(effectt)
ivmod <- create_causalmodel(graph, respvars = NULL, p.vals = p.vals, prob.form = prob.form, 
         constraints = constraints)
var.eff <- create_effect_vector(ivmod, effect)
```
