# Check for paths from from to to

Check for paths from from to to

## Usage

``` r
check_parents(parent_lookup, from, to, prev = NULL)
```

## Arguments

- parent_lookup:

  A list of vectors

- from:

  character

- to:

  character

- prev:

  Should always be null when first called

## Value

A list of paths or null if no path is found

## Examples

``` r
parent_lookup <- list(M = "Am", Y = c("M", "Ay"), A = NULL, Am = "A", Ay = "A")
check_parents(parent_lookup, "A", "Y")
#> $M
#> $M$Am
#> [1] "A"  "Am" "M"  "Y" 
#> 
#> 
#> $Ay
#> [1] "A"  "Ay" "Y" 
#> 
```
