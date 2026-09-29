# Function for performing data.table operations on an object of class `treedata.table`

This function can be used to subset rows, select and compute on columns
[data.table](https://rdrr.io/pkg/data.table/man/data.table.html).

## Usage

``` r
# S3 method for class 'treedata.table'
x[...]
```

## Arguments

- x:

  An object of class `treedata.table`

- ...:

  Arguments in the structure of `data.table` used to perform changes on
  the `treedata.table` object

## Value

A new object of class `treedata.table` with `$dat` and `$phy`
corresponding with the changes set to `$dat` using
[data.table](https://rdrr.io/pkg/data.table/man/data.table.html)'s
structure.

## Examples

``` r

data(anolis)
anolis2 <- anolis$phy
anolis2$tip.label[1] <- "NAA"
anolis1 <- anolis$phy
anolis1$tip.label[1] <- "NAA"
trees <- list(anolis1, anolis2)
class(trees) <- "multiPhylo"
treesFM <- list(anolis$phy, anolis$phy)
class(treesFM) <- "multiPhylo"

# A phylo object that fully matches the data
td <- as.treedata.table(tree = anolis$phy, data = anolis$dat)
#> Tip labels detected in column: X
#> Phylo object detected 
#> All tips from original tree/dataset were preserved
td <- as.treedata.table(anolis$phy, anolis$dat)
#> Tip labels detected in column: X
#> Phylo object detected 
#> All tips from original tree/dataset were preserved
td[, SVL]
#> $phy 
#> 
#> Phylogenetic tree with 100 tips and 99 internal nodes.
#> 
#> Tip labels:
#>   ahli, allogus, rubribarbus, imias, sagrei, bremeri, ...
#> 
#> Rooted; includes branch length(s).
#> 
#> $dat 
#>         SVL
#>       <num>
#> 1: 4.039125
#> 2: 4.040138
#> 3: 4.078469
#> 4: 4.099687
#> 5: 4.067162
#> 6: 4.113371
td[island == "Cuba" & ecomorph == "TG", .(ecomorph, island, SVL)]
#> $phy 
#> 
#> Phylogenetic tree with 12 tips and 11 internal nodes.
#> 
#> Tip labels:
#>   ahli, allogus, rubribarbus, imias, sagrei, bremeri, ...
#> 
#> Rooted; includes branch length(s).
#> 
#> $dat 
#>    ecomorph island      SVL
#>      <char> <char>    <num>
#> 1:       TG   Cuba 4.039125
#> 2:       TG   Cuba 4.040138
#> 3:       TG   Cuba 4.078469
#> 4:       TG   Cuba 4.099687
#> 5:       TG   Cuba 4.067162
#> 6:       TG   Cuba 4.113371
td[, utils::head(.SD, 1), by = .(ecomorph, island)]
#> $phy 
#> 
#> Phylogenetic tree with 23 tips and 22 internal nodes.
#> 
#> Tip labels:
#>   ahli, ophiolepis, garmani, opalinus, grahami, valencienni, ...
#> 
#> Rooted; includes branch length(s).
#> 
#> $dat 
#>    ecomorph      island   tip.label      SVL  PCI_limbs  PCII_head
#>      <char>      <char>      <char>    <num>      <num>      <num>
#> 1:       TG        Cuba        ahli 4.039125 -3.2482860  0.3722519
#> 2:       GB        Cuba  ophiolepis 3.637962  0.7915117  1.4585760
#> 3:       CG Puerto Rico     garmani 4.769473 -0.7735264  0.9371249
#> 4:       TC     Jamaica    opalinus 3.838376 -1.7794371 -0.3245381
#> 5:       TC Puerto Rico     grahami 4.154274 -2.3056535 -1.9139369
#> 6:       TW     Jamaica valencienni 4.321524  2.9424139 -0.8846007
#>    PCIII_padwidth_vs_tail PCIV_lamella_num awesomeness   hostility   attitude
#>                     <num>            <num>       <num>       <num>      <num>
#> 1:             -1.0422187       -2.4147423 -0.24165170 -0.17347691  0.6443771
#> 2:             -1.3152005       -2.2377514  0.35441877  0.05366142 -0.0938953
#> 3:              0.2594994        0.1051149  0.16779131  0.67675600 -0.6946008
#> 4:              1.5569939        0.9366501  1.48302162 -0.90826653  0.7261348
#> 5:              1.6852579        1.0144193  0.41064280 -0.11746257  0.7022959
#> 6:              1.8543308        0.1288233 -0.08837008  0.46528679 -0.5675490

# A multiphylo object that fully matches the data
td <- as.treedata.table(tree = treesFM, data = anolis$dat)
#> Tip labels detected in column: X
#> Multiphylo object detected 
#> All tips from original tree/dataset were preserved
td <- as.treedata.table(treesFM, anolis$dat)
#> Tip labels detected in column: X
#> Multiphylo object detected 
#> All tips from original tree/dataset were preserved
td[, SVL]
#> $phy 
#> 2 phylogenetic trees
#> 
#> $dat 
#>         SVL
#>       <num>
#> 1: 4.039125
#> 2: 4.040138
#> 3: 4.078469
#> 4: 4.099687
#> 5: 4.067162
#> 6: 4.113371
td[island == "Cuba" & ecomorph == "TG", .(ecomorph, island, SVL)]
#> $phy 
#> 2 phylogenetic trees
#> 
#> $dat 
#>    ecomorph island      SVL
#>      <char> <char>    <num>
#> 1:       TG   Cuba 4.039125
#> 2:       TG   Cuba 4.040138
#> 3:       TG   Cuba 4.078469
#> 4:       TG   Cuba 4.099687
#> 5:       TG   Cuba 4.067162
#> 6:       TG   Cuba 4.113371
td[, utils::head(.SD, 1), by = .(ecomorph, island)]
#> $phy 
#> 2 phylogenetic trees
#> 
#> $dat 
#>    ecomorph      island   tip.label      SVL  PCI_limbs  PCII_head
#>      <char>      <char>      <char>    <num>      <num>      <num>
#> 1:       TG        Cuba        ahli 4.039125 -3.2482860  0.3722519
#> 2:       GB        Cuba  ophiolepis 3.637962  0.7915117  1.4585760
#> 3:       CG Puerto Rico     garmani 4.769473 -0.7735264  0.9371249
#> 4:       TC     Jamaica    opalinus 3.838376 -1.7794371 -0.3245381
#> 5:       TC Puerto Rico     grahami 4.154274 -2.3056535 -1.9139369
#> 6:       TW     Jamaica valencienni 4.321524  2.9424139 -0.8846007
#>    PCIII_padwidth_vs_tail PCIV_lamella_num awesomeness   hostility   attitude
#>                     <num>            <num>       <num>       <num>      <num>
#> 1:             -1.0422187       -2.4147423 -0.24165170 -0.17347691  0.6443771
#> 2:             -1.3152005       -2.2377514  0.35441877  0.05366142 -0.0938953
#> 3:              0.2594994        0.1051149  0.16779131  0.67675600 -0.6946008
#> 4:              1.5569939        0.9366501  1.48302162 -0.90826653  0.7261348
#> 5:              1.6852579        1.0144193  0.41064280 -0.11746257  0.7022959
#> 6:              1.8543308        0.1288233 -0.08837008  0.46528679 -0.5675490

# A phylo object that partially matches the data
td <- as.treedata.table(tree = anolis1, data = anolis$dat)
#> Tip labels detected in column: X
#> Phylo object detected 
#> 1 tip(s) dropped from the original tree
#> 1 row(s) dropped from the original dataset
td <- as.treedata.table(anolis1, anolis$dat)
#> Tip labels detected in column: X
#> Phylo object detected 
#> 1 tip(s) dropped from the original tree
#> 1 row(s) dropped from the original dataset
td[, SVL]
#> $phy 
#> 
#> Phylogenetic tree with 99 tips and 98 internal nodes.
#> 
#> Tip labels:
#>   allogus, rubribarbus, imias, sagrei, bremeri, quadriocellifer, ...
#> 
#> Rooted; includes branch length(s).
#> 
#> $dat 
#>         SVL
#>       <num>
#> 1: 4.040138
#> 2: 4.078469
#> 3: 4.099687
#> 4: 4.067162
#> 5: 4.113371
#> 6: 3.901619
td[island == "Cuba" & ecomorph == "TG", .(ecomorph, island, SVL)]
#> $phy 
#> 
#> Phylogenetic tree with 11 tips and 10 internal nodes.
#> 
#> Tip labels:
#>   allogus, rubribarbus, imias, sagrei, bremeri, quadriocellifer, ...
#> 
#> Rooted; includes branch length(s).
#> 
#> $dat 
#>    ecomorph island      SVL
#>      <char> <char>    <num>
#> 1:       TG   Cuba 4.040138
#> 2:       TG   Cuba 4.078469
#> 3:       TG   Cuba 4.099687
#> 4:       TG   Cuba 4.067162
#> 5:       TG   Cuba 4.113371
#> 6:       TG   Cuba 3.901619
td[, utils::head(.SD, 1), by = .(ecomorph, island)]
#> $phy 
#> 
#> Phylogenetic tree with 23 tips and 22 internal nodes.
#> 
#> Tip labels:
#>   allogus, ophiolepis, garmani, opalinus, grahami, valencienni, ...
#> 
#> Rooted; includes branch length(s).
#> 
#> $dat 
#>    ecomorph      island   tip.label      SVL  PCI_limbs  PCII_head
#>      <char>      <char>      <char>    <num>      <num>      <num>
#> 1:       TG        Cuba     allogus 4.040138 -2.8455702  0.6001134
#> 2:       GB        Cuba  ophiolepis 3.637962  0.7915117  1.4585760
#> 3:       CG Puerto Rico     garmani 4.769473 -0.7735264  0.9371249
#> 4:       TC     Jamaica    opalinus 3.838376 -1.7794371 -0.3245381
#> 5:       TC Puerto Rico     grahami 4.154274 -2.3056535 -1.9139369
#> 6:       TW     Jamaica valencienni 4.321524  2.9424139 -0.8846007
#>    PCIII_padwidth_vs_tail PCIV_lamella_num awesomeness   hostility   attitude
#>                     <num>            <num>       <num>       <num>      <num>
#> 1:             -1.0253056       -2.4633111  0.62446888 -0.50009622  0.7128910
#> 2:             -1.3152005       -2.2377514  0.35441877  0.05366142 -0.0938953
#> 3:              0.2594994        0.1051149  0.16779131  0.67675600 -0.6946008
#> 4:              1.5569939        0.9366501  1.48302162 -0.90826653  0.7261348
#> 5:              1.6852579        1.0144193  0.41064280 -0.11746257  0.7022959
#> 6:              1.8543308        0.1288233 -0.08837008  0.46528679 -0.5675490

# A multiphylo object that partially matches the data
td <- as.treedata.table(tree = trees, data = anolis$dat)
#> Tip labels detected in column: X
#> Multiphylo object detected 
#> 1 tip(s) dropped from 2 trees
#> 1 row(s) dropped from the original dataset
td <- as.treedata.table(trees, anolis$dat)
#> Tip labels detected in column: X
#> Multiphylo object detected 
#> 1 tip(s) dropped from 2 trees
#> 1 row(s) dropped from the original dataset
td[, SVL]
#> $phy 
#> 2 phylogenetic trees
#> 
#> $dat 
#>         SVL
#>       <num>
#> 1: 4.040138
#> 2: 4.078469
#> 3: 4.099687
#> 4: 4.067162
#> 5: 4.113371
#> 6: 3.901619
td[island == "Cuba" & ecomorph == "TG", .(ecomorph, island, SVL)]
#> $phy 
#> 2 phylogenetic trees
#> 
#> $dat 
#>    ecomorph island      SVL
#>      <char> <char>    <num>
#> 1:       TG   Cuba 4.040138
#> 2:       TG   Cuba 4.078469
#> 3:       TG   Cuba 4.099687
#> 4:       TG   Cuba 4.067162
#> 5:       TG   Cuba 4.113371
#> 6:       TG   Cuba 3.901619
td[, utils::head(.SD, 1), by = .(ecomorph, island)]
#> $phy 
#> 2 phylogenetic trees
#> 
#> $dat 
#>    ecomorph      island   tip.label      SVL  PCI_limbs  PCII_head
#>      <char>      <char>      <char>    <num>      <num>      <num>
#> 1:       TG        Cuba     allogus 4.040138 -2.8455702  0.6001134
#> 2:       GB        Cuba  ophiolepis 3.637962  0.7915117  1.4585760
#> 3:       CG Puerto Rico     garmani 4.769473 -0.7735264  0.9371249
#> 4:       TC     Jamaica    opalinus 3.838376 -1.7794371 -0.3245381
#> 5:       TC Puerto Rico     grahami 4.154274 -2.3056535 -1.9139369
#> 6:       TW     Jamaica valencienni 4.321524  2.9424139 -0.8846007
#>    PCIII_padwidth_vs_tail PCIV_lamella_num awesomeness   hostility   attitude
#>                     <num>            <num>       <num>       <num>      <num>
#> 1:             -1.0253056       -2.4633111  0.62446888 -0.50009622  0.7128910
#> 2:             -1.3152005       -2.2377514  0.35441877  0.05366142 -0.0938953
#> 3:              0.2594994        0.1051149  0.16779131  0.67675600 -0.6946008
#> 4:              1.5569939        0.9366501  1.48302162 -0.90826653  0.7261348
#> 5:              1.6852579        1.0144193  0.41064280 -0.11746257  0.7022959
#> 6:              1.8543308        0.1288233 -0.08837008  0.46528679 -0.5675490
```
