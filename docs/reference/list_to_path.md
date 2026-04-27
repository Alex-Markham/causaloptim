# Recursive function to translate an effect list to a path sequence

Recursive function to translate an effect list to a path sequence

## Usage

``` r
list_to_path(x, name = NULL)
```

## Arguments

- x:

  A list of vars as returned by
  [parse_effect](https://sachsmc.github.io/causaloptim/reference/parse_effect.md)

- name:

  The name of the outcome variable

## Value

a list of characters describing the path sequence

## Examples

``` r
nofill <- "p{Y(X = 1, M1 = 1, M2(X = 1, M1 = 1)) = 1}"
eff2 <- parse_effect(nofill)$vars[[1]][[1]]
list_to_path(eff2, "Y")
#> [[1]]
#> X -> Y 
#>      1 
#> 
#> [[2]]
#> M1 -> Y 
#>       1 
#> 
#> [[3]]
#>  X -> M2 -> Y M1 -> M2 -> Y 
#>             1             1 
#> 
```
