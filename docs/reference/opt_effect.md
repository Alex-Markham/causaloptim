# Compute a bound on the average causal effect

This helper function does the heavy lifting for
[`optimize_effect_2`](https://sachsmc.github.io/causaloptim/reference/optimize_effect_2.md).
For a given casual query, it computes either a lower or an upper bound
on the corresponding causal effect.

## Usage

``` r
opt_effect(opt, obj, redundant)
```

## Arguments

- opt:

  A string. Either `"min"` or `"max"` for a lower or an upper bound,
  respectively.

- obj:

  An object as returned by the function
  [`analyze_graph`](https://sachsmc.github.io/causaloptim/reference/analyze_graph.md).
  Contains the casual query to be estimated.

- redundant:

  If TRUE, removed redundant constraints as a preprocessing step. Can
  speed things up.

## Value

An object of class `optbound`; a list with the following named
components:

- `expr` is the *main* output; an expression of the bound as a
  print-friendly string,

- `type` is either `"lower"` or `"upper"` according to the type of the
  bound,

- `dual_vertices` is a numeric matrix whose rows are the vertices of the
  convex polytope of the dual LP,

- `dual_vrep` is a V-representation of the dual convex polytope,
  including some extra data.
