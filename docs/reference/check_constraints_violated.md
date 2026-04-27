# Check whether any of the observable constraints implied by the causal model are violated for a given distribution of observables

Check whether any of the observable constraints implied by the causal
model are violated for a given distribution of observables

## Usage

``` r
check_constraints_violated(obj, probs, tol = 1e-12)
```

## Arguments

- obj:

  An object of class "causalmodel"

- probs:

  A named vector of observable probabilities, in the same order as
  obj\$data\$parameters

- tol:

  Tolerance for checking (in)equalities

## Value

Either TRUE (violated) or FALSE (not violated) with messages indicating
what constraints are violated if any.

## Examples

``` r
graph <- initialize_graph(graph_from_literal(Z -+ X, X -+ Y, Ur -+ X, Ur -+ Y))

iv_model <- create_causalmodel(graph, prob.form = list(out = c("X", "Y"), cond = "Z"))
check_constraints_violated(iv_model, probs = sample_distribution(iv_model))
#> Constraints not violated
#> [1] FALSE
```
