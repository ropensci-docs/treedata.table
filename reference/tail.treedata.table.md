# Return the last part of an treedata.table object

Return the last part of an treedata.table object

## Usage

``` r
# S3 method for class 'treedata.table'
tail(x, ...)
```

## Arguments

- x:

  a treedata.table object

- ...:

  Additional arguments passed to head.data.table

## Value

Last part of an treedata.table object

## Examples

``` r
data(anolis)
td <- as.treedata.table(anolis$phy, anolis$dat)
#> Tip labels detected in column: X
#> Phylo object detected 
#> All tips from original tree/dataset were preserved
tail(td)
#>       tip.label      SVL   PCI_limbs  PCII_head PCIII_padwidth_vs_tail
#>          <char>    <num>       <num>      <num>                  <num>
#> 1:  darlingtoni 4.302036  4.06703170 -1.4937898             -0.2002259
#> 2:     aliniger 4.036557  0.12323898 -1.6746704              2.3871336
#> 3:   singularis 4.057997  0.36326789 -0.9542287              1.6562154
#> 4: chlorocyanus 4.275448  0.43906343  1.3540345              1.9531470
#> 5:  coelestinus 4.297965 -0.02721683  0.3687537              1.6364316
#> 6:     occultus 3.663049  7.92078444 -0.1901397              2.4922819
#>    PCIV_lamella_num  awesomeness  hostility   attitude ecomorph      island
#>               <num>        <num>      <num>      <num>   <char>      <char>
#> 1:       0.31138087  1.718720076 -1.6900790  1.0214567       TW  Hispaniola
#> 2:       0.58486431  0.006869282  0.1448154  0.2937643       TC  Hispaniola
#> 3:       1.00756926  1.592083294 -1.7010527  1.4531345       TC  Hispaniola
#> 4:       1.80512493 -1.065610146  0.9200977 -0.9372173       TC  Hispaniola
#> 5:       1.02571762  0.290926638 -0.6209660  1.2803335       TC  Hispaniola
#> 6:      -0.09577977 -1.191686980  1.2153014  0.0324486       TW Puerto Rico
```
