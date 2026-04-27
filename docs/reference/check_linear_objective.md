# Check linearity of objective function implied by a causal model and effect

Check linearity of objective function implied by a causal model and
effect

## Usage

``` r
check_linear_objective(causal_model, effectt)
```

## Arguments

- causal_model:

  An object of class "causalmodel" as produce by
  [create_causalmodel](https://sachsmc.github.io/causaloptim/reference/create_causalmodel.md)

- effectt:

  A character string that represents the causal effect of interest

## Value

A logical value that is TRUE if the objective function is linear

## Details

The effectt parameter describes your causal effect of interest. The
effectt parameter must be of the form

`p{V11(X=a)=a; V12(X=a)=b;...} op1 p{V21(X=b)=a; V22(X=c)=b;...} op2 ...`

where Vij are names of variables in the graph, a, b are numeric values
from 0:(nvals - 1), and op are either - or +. You can specify a single
probability statement (i.e., no operator). Note that the probability
statements begin with little p, and use curly braces, and items inside
the probability statements are separated by ;. The variables may be
potential outcomes which are denoted by parentheses. Variables may also
be nested inside potential outcomes.

All of the following are valid effect statements:

`p{Y(X = 1) = 1} - p{Y(X = 0) = 1}`

`p{X(Z = 1) = 1; X(Z = 0) = 0}`

`p{Y(M(X = 0), X = 1) = 1} - p{Y(M(X = 0), X = 0) = 1}`

The effect must be fully specified, that is, all parents of a variable
that is intervened upon need to be specified. The function cannot infer
missing values or marginalize over some parents but not others.

## Examples

``` r
 ## regular IV case

ivgraph <- initialize_graph(graph_from_literal(Z -+ X, X -+ Y, Ur -+ X, Ur -+ Y))
prob.form <- list(out = c("Y", "X"), cond = "Z")

iv_model <- create_causalmodel(graph = ivgraph,
            prob.form = prob.form)
check_linear_objective(iv_model, effectt = "p{Y(X = 1) = 1}")
#> [1] TRUE

#'  ## contaminated IV case

civgraph <- initialize_graph(graph_from_literal(Z -+ X, X -+ Y, Z-+ Y, Ur -+ X, Ur -+ Y))

cont_iv <- create_causalmodel(graph = civgraph, prob.form = prob.form)

check_linear_objective(cont_iv, effectt = "p{Y(X = 1) = 1}")
#> [1] FALSE
```
