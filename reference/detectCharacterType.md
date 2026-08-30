# Function to detect whether a character is continuous or discrete

This function detects whether a given vector is a continuous (e.g., with
values 2.45, 9.35, and so on) or a discrete (e.g., with values blue,
red, yellow) character.

## Usage

``` r
detectCharacterType(dat, cutoff = 0.1)
```

## Arguments

- dat:

  A vector of data

- cutoff:

  Cutoff value for deciding if numeric data might actually be discrete:
  if nlev is the number of levels and n the length of dat, then nlev / n
  should exceed cutoff, or the data will be classified as discrete

## Value

Either "discrete" or "continuous"

## Examples

``` r
data(anolis)
detectCharacterType(anolis$dat[, 1])
#> [1] "discrete"
```
