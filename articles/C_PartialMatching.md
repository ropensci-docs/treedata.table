# Partially Matching of Trait Data and Tree(s) in treedata.table

## Partially matching trait data and tree(s)

The `as.treedata.table` function enables users to match a tree (or
multiple trees) against a single trait database. We first load the
sample dataset.

``` r

library(ape)
library(treedata.table)
```

    ##          Thank you for using the {treedata.table} R package!   
    ## 
    ##                         🙂Happy coding!!🙂

``` r

# Load example data
data(anolis)
#Create treedata.table object with as.treedata.table
td <- as.treedata.table(tree = anolis$phy, data = anolis$dat)
```

    ## Tip labels detected in column: X

    ## Phylo object detected

    ## All tips from original tree/dataset were preserved

Tips that are not common between the tree (or trees) and dataset are
dropped from the resulting `treedata.table` object. For instance, below
I have modified the original anole phylogeny such that *A. ahli*
(**ahli**) is replaced for a label that is not present in the dataset
(**NAA**).

``` r

anolis_newtip<-anolis$phy
anolis_newtip$tip.label[1]<-'NAA'
anolis_newtip
```

    ## 
    ## Phylogenetic tree with 100 tips and 99 internal nodes.
    ## 
    ## Tip labels:
    ##   NAA, allogus, rubribarbus, imias, sagrei, bremeri, ...
    ## 
    ## Rooted; includes branch length(s).

We then use this modified tree to fit a `treedata.table` object using
the `as.treedata.table` function:

``` r

td <- as.treedata.table(tree=anolis_newtip, data=anolis$dat)
```

    ## Tip labels detected in column: X

    ## Phylo object detected

    ## 1 tip(s) dropped from the original tree
    ## 1 row(s) dropped from the original dataset

Note that `as.treedata.table` drops all non-overlapping tips (**NAA**
\[present in the tree but not in the trait data\] and **ahi** \[present
in the database but not in tree\] in this case) and returns a
`treedata.table` object with fully matching `phy` and `data` objects.

``` r

td
```

    ## $phy 
    ## 
    ## Phylogenetic tree with 99 tips and 98 internal nodes.
    ## 
    ## Tip labels:
    ##   allogus, rubribarbus, imias, sagrei, bremeri, quadriocellifer, ...
    ## 
    ## Rooted; includes branch length(s).
    ## 
    ## $dat 
    ##          tip.label      SVL PCI_limbs PCII_head PCIII_padwidth_vs_tail
    ##             <char>    <num>     <num>     <num>                  <num>
    ## 1:         allogus 4.040138 -2.845570 0.6001134             -1.0253056
    ## 2:     rubribarbus 4.078469 -2.238349 1.1199779             -1.1929572
    ## 3:           imias 4.099687 -3.048917 2.3320349              0.1616442
    ## 4:          sagrei 4.067162 -1.741055 2.0228243              0.1693635
    ## 5:         bremeri 4.113371 -1.813611 2.6067501              0.6399320
    ## 6: quadriocellifer 3.901619 -2.267894 0.9909208              0.3553405
    ##    PCIV_lamella_num awesomeness  hostility   attitude ecomorph island
    ##               <num>       <num>      <num>      <num>   <char> <char>
    ## 1:        -2.463311   0.6244689 -0.5000962  0.7128910       TG   Cuba
    ## 2:        -2.087433  -0.4277574  0.4800445 -0.9674263       TG   Cuba
    ## 3:        -2.112606   0.1694260 -0.4108123  0.1963580       TG   Cuba
    ## 4:        -1.375769  -0.6304338  0.7193130 -1.2228276       TG   Cuba
    ## 5:        -1.626299  -1.7543006  1.4127184  0.1832345       TG   Cuba
    ## 6:        -2.105059  -0.2576389  0.4627081 -0.2712794       TG   Cuba

Fully-matching matrix and trees are also returned in `treedata.table`
objects with `multiPhylo` objects in their `phy` component. See the
example below.

We first construct a `multiPhylo` object that partially overlaps the
original trait database by using **NAA** instead of **ahi**.

``` r

anolis2<-anolis$phy
anolis2$tip.label[1]<-'NAA'
anolis1<-anolis$phy
anolis1$tip.label[1]<-'NAA'
trees<-list(anolis1,anolis2)
class(trees) <- "multiPhylo"
trees
```

    ## 2 phylogenetic trees

Next, we fit the `treedata.table` object using the relevant `multiPhylo`
object and the original trait database.

``` r

td <- as.treedata.table(tree=trees, data=anolis$dat)
```

    ## Tip labels detected in column: X

    ## Multiphylo object detected

    ## 1 tip(s) dropped from 2 trees
    ## 1 row(s) dropped from the original dataset

Note that 1 tip was dropped for all trees in the `multiPhylo` object and
a single row was deleted from the `data.table` object in the
`treedata.table` object.

``` r

td
```

    ## $phy 
    ## 2 phylogenetic trees
    ## 
    ## $dat 
    ##          tip.label      SVL PCI_limbs PCII_head PCIII_padwidth_vs_tail
    ##             <char>    <num>     <num>     <num>                  <num>
    ## 1:         allogus 4.040138 -2.845570 0.6001134             -1.0253056
    ## 2:     rubribarbus 4.078469 -2.238349 1.1199779             -1.1929572
    ## 3:           imias 4.099687 -3.048917 2.3320349              0.1616442
    ## 4:          sagrei 4.067162 -1.741055 2.0228243              0.1693635
    ## 5:         bremeri 4.113371 -1.813611 2.6067501              0.6399320
    ## 6: quadriocellifer 3.901619 -2.267894 0.9909208              0.3553405
    ##    PCIV_lamella_num awesomeness  hostility   attitude ecomorph island
    ##               <num>       <num>      <num>      <num>   <char> <char>
    ## 1:        -2.463311   0.6244689 -0.5000962  0.7128910       TG   Cuba
    ## 2:        -2.087433  -0.4277574  0.4800445 -0.9674263       TG   Cuba
    ## 3:        -2.112606   0.1694260 -0.4108123  0.1963580       TG   Cuba
    ## 4:        -1.375769  -0.6304338  0.7193130 -1.2228276       TG   Cuba
    ## 5:        -1.626299  -1.7543006  1.4127184  0.1832345       TG   Cuba
    ## 6:        -2.105059  -0.2576389  0.4627081 -0.2712794       TG   Cuba
