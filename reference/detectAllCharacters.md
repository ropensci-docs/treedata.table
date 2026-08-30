# Apply detectCharacterType over an entire matrix

This function detects whether each column in a matrix is a continuous
(e.g., with values 2.45, 9.35, and so on) or a discrete character (e.g.,
with values blue, red, yellow).

## Usage

``` r
detectAllCharacters(mat, cutoff = 0.1)
```

## Arguments

- mat:

  A matrix of data

- cutoff:

  Cutoff value for deciding if numeric data might actually be discrete:
  if nlev is the number of levels and n the length of dat, then nlev / n
  should exceed cutoff, or the data will be classified as discrete

## Value

Vector of either "discrete" or "continuous" for each variable in matrix

## Examples

``` r
data(anolis)
detectAllCharacters(anolis$dat)
#>  [1] "discrete"   "continuous" "continuous" "continuous" "continuous"
#>  [6] "continuous" "continuous" "continuous" "continuous" "discrete"  
#> [11] "discrete"  
```
