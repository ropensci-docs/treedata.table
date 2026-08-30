# Combine tree (or set of trees) and data.frame into a single treedata.table object

This function takes as input a tree of class `phylo` or `multiPhylo` and
a `data.frame` and combines them into a treedata.table. If a
`multiPhylo` is provided, all trees must have the same tip.labels.
`treedata.table` object is sorted such that the rows in the data.table
are matched to the tip.labels of the phylogeny. Tip.labels on the tree
must match a column of tip names in the input data.frame. The output of
this function will be a treedata.table, which can be manipulated as a
data.table.

## Usage

``` r
as.treedata.table(tree, data, name_column = "detect")
```

## Arguments

- tree:

  A tree of class `phylo` or multiple trees of class `multiPhylo`

- data:

  A dataset in format `data.frame`

- name_column:

  A character indicating the name of taxa in `data.frame`. If set to
  `detect` (default) `as treedata.table` will auto-detect this column

## Value

An object of type `treedata.table` containing the tree and data.table

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
# A multiphylo object that fully matches the data
td <- as.treedata.table(tree = treesFM, data = anolis$dat)
#> Tip labels detected in column: X
#> Multiphylo object detected 
#> All tips from original tree/dataset were preserved
# A phylo object that partially matches the data
td <- as.treedata.table(tree = anolis1, data = anolis$dat)
#> Tip labels detected in column: X
#> Phylo object detected 
#> 1 tip(s) dropped from the original tree
#> 1 row(s) dropped from the original dataset
# A multiphylo object that partially matches the data
td <- as.treedata.table(tree = trees, data = anolis$dat)
#> Tip labels detected in column: X
#> Multiphylo object detected 
#> 1 tip(s) dropped from 2 trees
#> 1 row(s) dropped from the original dataset
```
