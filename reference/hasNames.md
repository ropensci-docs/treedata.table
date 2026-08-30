# Row and column name check

This function checks whether a given `data.frame` or `matrix` has column
names (`colnames`), row.names (`row.names`), or both.

## Usage

``` r
hasNames(dat, nameType = "row")
```

## Arguments

- dat:

  A vector of data

- nameType, :

  either:

  "row"

  :   Rows (default)

  "col"

  :   Columns

  "rowcol"

  :   Both rows and columns

## Value

`TRUE` or `FALSE` indicating if the object has names (`columns`, `rows`,
or `both`)

## Examples

``` r
data(anolis)
hasNames(anolis$dat, "row")
#>  row 
#> TRUE 
```
