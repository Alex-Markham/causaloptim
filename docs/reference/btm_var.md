# Recursive function to get the last name in a list

Recursive function to get the last name in a list

## Usage

``` r
btm_var(x, name = NULL)
```

## Arguments

- x:

  a list

- name:

  name of the top element of the list

## Value

The name of the deepest nested list element

## Examples

``` r
btm_var(list(X = list(Y = list(K = 1))))
#> [1] "K"
```
