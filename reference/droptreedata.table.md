# Function dropping taxa from an object of class `treedata.table`

This function can be used to remove species from an object of class
`treedata.table`. The resulting `treedata.table` will include fully
matching `$dat` and `$phy` elements. The user should confirm the changes
before they are processed.

## Usage

``` r
droptreedata.table(tdObject, taxa)
```

## Arguments

- tdObject:

  An object of class `treedata.table`

- taxa:

  A vector class `character` containing all taxa that needs to be
  dropped from the original `treedata.table` object

## Value

An object of class `treedata.table` with matching `$dat` and `$phy`
elements based on whether `taxa` were dropped or not.

## Examples

``` r
data(anolis)
# With a multiphylo object in the treedata.table object
td <- as.treedata.table(anolis$phy, anolis$dat)
#> Tip labels detected in column: X
#> Phylo object detected 
#> All tips from original tree/dataset were preserved
droptreedata.table(
  tdObject = td, taxa =
    c("chamaeleonides", "eugenegrahami")
)
#> 2 taxa were dropped from the treedata.table object
#> $phy 
#> 
#> Phylogenetic tree with 98 tips and 97 internal nodes.
#> 
#> Tip labels:
#>   ahli, allogus, rubribarbus, imias, sagrei, bremeri, ...
#> 
#> Rooted; includes branch length(s).
#> 
#> $dat 
#>      tip.label      SVL PCI_limbs PCII_head PCIII_padwidth_vs_tail
#>         <char>    <num>     <num>     <num>                  <num>
#> 1:        ahli 4.039125 -3.248286 0.3722519             -1.0422187
#> 2:     allogus 4.040138 -2.845570 0.6001134             -1.0253056
#> 3: rubribarbus 4.078469 -2.238349 1.1199779             -1.1929572
#> 4:       imias 4.099687 -3.048917 2.3320349              0.1616442
#> 5:      sagrei 4.067162 -1.741055 2.0228243              0.1693635
#> 6:     bremeri 4.113371 -1.813611 2.6067501              0.6399320
#>    PCIV_lamella_num awesomeness  hostility   attitude ecomorph island
#>               <num>       <num>      <num>      <num>   <char> <char>
#> 1:        -2.414742  -0.2416517 -0.1734769  0.6443771       TG   Cuba
#> 2:        -2.463311   0.6244689 -0.5000962  0.7128910       TG   Cuba
#> 3:        -2.087433  -0.4277574  0.4800445 -0.9674263       TG   Cuba
#> 4:        -2.112606   0.1694260 -0.4108123  0.1963580       TG   Cuba
#> 5:        -1.375769  -0.6304338  0.7193130 -1.2228276       TG   Cuba
#> 6:        -1.626299  -1.7543006  1.4127184  0.1832345       TG   Cuba

# With a multiphylo object in the treedata.table object
treesFM <- list(anolis$phy, anolis$phy)
class(treesFM) <- "multiPhylo"
td <- as.treedata.table(treesFM, anolis$dat)
#> Tip labels detected in column: X
#> Multiphylo object detected 
#> All tips from original tree/dataset were preserved
droptreedata.table(
  tdObject = td, taxa =
    c("chamaeleonides", "eugenegrahami")
)
#> 2 taxa were dropped from the treedata.table object
#> $phy 
#> 2 phylogenetic trees
#> 
#> $dat 
#>      tip.label      SVL PCI_limbs PCII_head PCIII_padwidth_vs_tail
#>         <char>    <num>     <num>     <num>                  <num>
#> 1:        ahli 4.039125 -3.248286 0.3722519             -1.0422187
#> 2:     allogus 4.040138 -2.845570 0.6001134             -1.0253056
#> 3: rubribarbus 4.078469 -2.238349 1.1199779             -1.1929572
#> 4:       imias 4.099687 -3.048917 2.3320349              0.1616442
#> 5:      sagrei 4.067162 -1.741055 2.0228243              0.1693635
#> 6:     bremeri 4.113371 -1.813611 2.6067501              0.6399320
#>    PCIV_lamella_num awesomeness  hostility   attitude ecomorph island
#>               <num>       <num>      <num>      <num>   <char> <char>
#> 1:        -2.414742  -0.2416517 -0.1734769  0.6443771       TG   Cuba
#> 2:        -2.463311   0.6244689 -0.5000962  0.7128910       TG   Cuba
#> 3:        -2.087433  -0.4277574  0.4800445 -0.9674263       TG   Cuba
#> 4:        -2.112606   0.1694260 -0.4108123  0.1963580       TG   Cuba
#> 5:        -1.375769  -0.6304338  0.7193130 -1.2228276       TG   Cuba
#> 6:        -1.626299  -1.7543006  1.4127184  0.1832345       TG   Cuba
```
