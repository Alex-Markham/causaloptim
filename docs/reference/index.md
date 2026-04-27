# Package index

## Shiny interface

Most users will only need to use this function.

- [`specify_graph()`](https://sachsmc.github.io/causaloptim/reference/specify_graph.md)
  : Shiny interface to specify network structure and compute bounds
- [`causaloptim-package`](https://sachsmc.github.io/causaloptim/reference/causaloptim-package.md)
  [`causaloptim`](https://sachsmc.github.io/causaloptim/reference/causaloptim-package.md)
  : An Interface to Specify Causal Graphs and Compute Bounds on Causal
  Effects

## Direct interface

Functions for creating and interacting with the algorithm.

- [`analyze_graph()`](https://sachsmc.github.io/causaloptim/reference/analyze_graph.md)
  : Analyze the causal graph and effect to determine constraints and
  objective
- [`optimize_effect_2()`](https://sachsmc.github.io/causaloptim/reference/optimize_effect_2.md)
  : Run the optimizer to obtain symbolic bounds
- [`initialize_graph()`](https://sachsmc.github.io/causaloptim/reference/initialize_graph.md)
  : Initialize an igraph object for use with causaloptim
- [`create_causalmodel()`](https://sachsmc.github.io/causaloptim/reference/create_causalmodel.md)
  : Create a structural causal model from a graph or a set of response
  functions
- [`create_response_function()`](https://sachsmc.github.io/causaloptim/reference/create_response_function.md)
  : Translate regular DAG to response functions
- [`create_linearcausalproblem()`](https://sachsmc.github.io/causaloptim/reference/create_linearcausalproblem.md)
  : Create linear causal problem from causal model and effect
- [`latex_bounds()`](https://sachsmc.github.io/causaloptim/reference/latex_bounds.md)
  : Latex bounds equations
- [`sample_distribution()`](https://sachsmc.github.io/causaloptim/reference/sample_distribution.md)
  : Sample a distribution of observable probabilities that satisfy the
  causal model
- [`rdirichlet()`](https://sachsmc.github.io/causaloptim/reference/rdirichlet.md)
  : Sample from a Dirichlet distribution
- [`check_constraints_violated()`](https://sachsmc.github.io/causaloptim/reference/check_constraints_violated.md)
  : Check whether any of the observable constraints implied by the
  causal model are violated for a given distribution of observables
- [`check_linear_objective()`](https://sachsmc.github.io/causaloptim/reference/check_linear_objective.md)
  : Check linearity of objective function implied by a causal model and
  effect
- [`plot(`*`<linearcausalproblem>`*`)`](https://sachsmc.github.io/causaloptim/reference/plot.linearcausalproblem.md)
  : Plot the graph from the causal problem with a legend describing
  attributes
- [`print(`*`<linearcausalproblem>`*`)`](https://sachsmc.github.io/causaloptim/reference/print.linearcausalproblem.md)
  : Print the causal problem
- [`print(`*`<causalmodel>`*`)`](https://sachsmc.github.io/causaloptim/reference/print.causalmodel.md)
  : Print relevant information about the causal model

## Utilities

Internal functions and deprecated

- [`causalproblemcheck()`](https://sachsmc.github.io/causaloptim/reference/causalproblemcheck.md)
  : Check conditions on causal problem
- [`constraintscheck()`](https://sachsmc.github.io/causaloptim/reference/constraintscheck.md)
  : Check constraints
- [`create_effect_vector()`](https://sachsmc.github.io/causaloptim/reference/create_effect_vector.md)
  : Translate target effect to vector of response variables
- [`create_q_matrix()`](https://sachsmc.github.io/causaloptim/reference/create_q_matrix.md)
  : Translate response functions into matrix of counterfactuals
- [`create_response_function()`](https://sachsmc.github.io/causaloptim/reference/create_response_function.md)
  : Translate regular DAG to response functions
- [`graphrescheck()`](https://sachsmc.github.io/causaloptim/reference/graphrescheck.md)
  : Check conditions on digraph
- [`get_default_effect()`](https://sachsmc.github.io/causaloptim/reference/get_default_effect.md)
  : Define default effect for a given graph
- [`opt_effect()`](https://sachsmc.github.io/causaloptim/reference/opt_effect.md)
  : Compute a bound on the average causal effect
- [`parse_constraints()`](https://sachsmc.github.io/causaloptim/reference/parse_constraints.md)
  : Parse text that defines a the constraints
- [`parse_effect()`](https://sachsmc.github.io/causaloptim/reference/parse_effect.md)
  : Parse text that defines a causal effect
- [`plot_graphres()`](https://sachsmc.github.io/causaloptim/reference/plot_graphres.md)
  : Plot the analyzed graph object
- [`querycheck()`](https://sachsmc.github.io/causaloptim/reference/querycheck.md)
  : Check conditions on query
- [`simulate_bounds()`](https://sachsmc.github.io/causaloptim/reference/simulate_bounds.md)
  : Simulate bounds
- [`btm_var()`](https://sachsmc.github.io/causaloptim/reference/btm_var.md)
  : Recursive function to get the last name in a list
- [`check_parents()`](https://sachsmc.github.io/causaloptim/reference/check_parents.md)
  : Check for paths from from to to
- [`find_all_paths()`](https://sachsmc.github.io/causaloptim/reference/find_all_paths.md)
  : Find all paths in a causal model
- [`interpret_bounds()`](https://sachsmc.github.io/causaloptim/reference/interpret_bounds.md)
  : Convert bounds string to a function
- [`list_to_path()`](https://sachsmc.github.io/causaloptim/reference/list_to_path.md)
  : Recursive function to translate an effect list to a path sequence
- [`update_effect()`](https://sachsmc.github.io/causaloptim/reference/update_effect.md)
  : Update the effect in a linearcausalproblem object
