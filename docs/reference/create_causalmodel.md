# Create a structural causal model from a graph or a set of response functions

Given either a graph or a set of response functions (i.e., either
`graph` or `respvars` may be provided), and a specification of what
conditional probabilities are observed, produce a causal model.

## Usage

``` r
create_causalmodel(
  graph = NULL,
  respvars = NULL,
  prob.form,
  p.vals,
  constraints = NULL,
  right.vars = NULL,
  redundant = FALSE
)
```

## Arguments

- graph:

  A graph with special edge and vertex attributes, as produced by
  [initialize_graph](https://sachsmc.github.io/causaloptim/reference/initialize_graph.md)

- respvars:

  List of response functions as produced by
  [create_response_function](https://sachsmc.github.io/causaloptim/reference/create_response_function.md)

- prob.form:

  A list with two named elements "out", "cond" where each element is a
  character vector of variable names that appear in p.vals

- p.vals:

  Data frame defining which probabilities are observable. The variable
  names of p.vals must all appear in prob.form. If missing, will assume
  that all combinations of the variables values are observed.

- constraints:

  A vector of character strings that represent the constraints on
  counterfactual quantities

- right.vars:

  A vector of character strings indicating which variables are on the
  right side of the graph. Only required when graph is NULL. See
  examples.

- redundant:

  If TRUE, removes any redundant constraints before deriving the
  observable constraints.

## Value

An object of class "causalmodel"

## Details

It is assumed that probabilities of the form p(out \| cond) are
observed, for each combination of values in p.vals. cond may be NULL in
which case nothing is conditioned on.

The constraints are specified in terms of potential outcomes to
constrain by writing the potential outcomes, values of their parents,
and operators that determine the constraint (equalities or
inequalities). For example, `X(Z = 1) >= X(Z = 0)`

## Examples

``` r
 ## regular IV case

graph <- initialize_graph(graph_from_literal(Z -+ X, X -+ Y, Ur -+ X, Ur -+ Y))

iv_model <- create_causalmodel(graph, prob.form = list(out = c("X", "Y"), cond = "Z"))
# with monotonicity
iv_model_mono <- create_causalmodel(graph, prob.form = list(out = c("X", "Y"), cond = "Z"),
                 constraints = list("X(Z = 1) >= X(Z = 0)"))
                 
#showing the use of right.vars
b <- initialize_graph(graph_from_literal(Ul -+ X -+ Y -+ Y2, Ur -+ Y, Ur -+ Y2))
V(b)$latent <- c(1, 0, 1, 0, 1)
respvars <- create_response_function(b)
create_causalmodel(graph = b, constraints = "Y2(Y = 1) >= Y2(Y = 0)",
                   p.vals = expand.grid(X = 0:1, Y2 = 0:1), 
                   prob.form = list(out = "Y2", cond = "X"))
#> This is a causal model represented by the set of response functions in the x$data$response_functions element, where it is assumed that we observe parameters (observables) of the form pa_b, which represents the probability P(Y2 = a | X = b). To sample a distribution from this model, use sample_distribution(x).
#> The observables relate to 12 unobservable variables which represent probabilities of particular response functions. The constraints are in the following equations and are available in numeric matrix form in the x$counterfactual_constraints$numeric$R element.
#> q0_0 + q0_2 + q0_3 + q1_0 + q1_2 + q1_3 + q2_0 + q2_2 + q2_3 + q3_0 + q3_2 + q3_3  = 1
#> p0_0 = q0_0 + q0_2 + q1_0 + q2_0 + q2_2 + q3_0
#> p0_1 = q0_0 + q0_2 + q1_0 + q1_2 + q2_0 + q3_0
#> p1_0 = q0_3 + q1_2 + q1_3 + q2_3 + q3_2 + q3_3
#> p1_1 = q0_3 + q1_3 + q2_2 + q2_3 + q3_2 + q3_3
#> The causal model implies the following observable constraints in addition to the standard probabilistic constraints, which are available in numeric form in the x$observable_constraints$numeric element. To test whether these constraints are violated, use check_constraints_violated(x)
#> No observable constraints other than the probabilistic constraints. To compute bounds, specify an effect of interest, and see the compute_bounds function.
 ## need to specify right.vars because it cannot be inferred from the response functions alone
create_causalmodel(graph = NULL, respvars = respvars, 
                   constraints = "Y2(Y = 1) >= Y2(Y = 0)",
                   p.vals = expand.grid(X = 0:1, Y2 = 0:1), 
                   prob.form = list(out = "Y2", cond = "X"), 
                   right.vars = c("Y", "Y2"))
#> This is a causal model represented by the set of response functions in the x$data$response_functions element, where it is assumed that we observe parameters (observables) of the form pa_b, which represents the probability P(Y2 = a | X = b). To sample a distribution from this model, use sample_distribution(x).
#> The observables relate to 12 unobservable variables which represent probabilities of particular response functions. The constraints are in the following equations and are available in numeric matrix form in the x$counterfactual_constraints$numeric$R element.
#> q0_0 + q0_2 + q0_3 + q1_0 + q1_2 + q1_3 + q2_0 + q2_2 + q2_3 + q3_0 + q3_2 + q3_3  = 1
#> p0_0 = q0_0 + q0_2 + q1_0 + q2_0 + q2_2 + q3_0
#> p0_1 = q0_0 + q0_2 + q1_0 + q1_2 + q2_0 + q3_0
#> p1_0 = q0_3 + q1_2 + q1_3 + q2_3 + q3_2 + q3_3
#> p1_1 = q0_3 + q1_3 + q2_2 + q2_3 + q3_2 + q3_3
#> The causal model implies the following observable constraints in addition to the standard probabilistic constraints, which are available in numeric form in the x$observable_constraints$numeric element. To test whether these constraints are violated, use check_constraints_violated(x)
#> No observable constraints other than the probabilistic constraints. To compute bounds, specify an effect of interest, and see the compute_bounds function.
```
