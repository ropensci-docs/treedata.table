# Working With multiPhylo Objects in treedata.table

## Working with multiphylo objects

`treedata.table` further allows the matching of multiple phylogenies
(`multiPhylo`) against a single dataset (`data.frame`). Below, we
modified the anole dataset to explain the extended functionality of
`treedata.table` with `multiPhylo` objects. Note that all the trees in
the `multiPhylo` must have exactly the same taxa.

We first load the sample dataset.

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

We then create a `multiPhylo` object including only two `phylo` objects.
Users can provide any number of `phylo` objects within the `multiPhylo`
object. However, trees can only differ in their topology. In other
words, all trees must have the same tip labels.

We also note that both the provided `multiPhylo` and `data.frame` should
partially overlap

``` r

trees<-list(anolis$phy,anolis$phy)
class(trees) <- "multiPhylo"
trees
```

    ## 2 phylogenetic trees

Now, we create our treedata.table object by combining the trait data
(`data.frame`) and the newly generated `multiPhylo` object. Note that
there is only a single character matrix.

``` r

td <- as.treedata.table(tree=trees, data=anolis$dat)
```

    ## Tip labels detected in column: X

    ## Multiphylo object detected

    ## All tips from original tree/dataset were preserved

The resulting `td` object now returns a `multiPhylo` object under `phy`.
This objectcontains only the overlapping taxa between the multiphylo
objects and the input dataset.

``` r

class(td$phy);td$phy
```

    ## [1] "multiPhylo"

    ## 2 phylogenetic trees

Please note that all the basic `treedata.table` functions highlighted
above for `phylo` objects are still functional when `treedata.table`
objects include `multiPhylo` objects.

``` r

td[, head(.SD, 1), by = "ecomorph"]
```

    ## $phy 
    ## 2 phylogenetic trees
    ## 
    ## $dat 
    ##    ecomorph   tip.label      SVL  PCI_limbs  PCII_head PCIII_padwidth_vs_tail
    ##      <char>      <char>    <num>      <num>      <num>                  <num>
    ## 1:       TG        ahli 4.039125 -3.2482860  0.3722519             -1.0422187
    ## 2:       GB  ophiolepis 3.637962  0.7915117  1.4585760             -1.3152005
    ## 3:       CG     garmani 4.769473 -0.7735264  0.9371249              0.2594994
    ## 4:       TC    opalinus 3.838376 -1.7794371 -0.3245381              1.5569939
    ## 5:       TW valencienni 4.321524  2.9424139 -0.8846007              1.8543308
    ## 6:        U  reconditus 4.482607 -2.7270416 -0.2104066             -2.3534242
    ##    PCIV_lamella_num awesomeness   hostility    attitude      island
    ##               <num>       <num>       <num>       <num>      <char>
    ## 1:       -2.4147423 -0.24165170 -0.17347691  0.64437708        Cuba
    ## 2:       -2.2377514  0.35441877  0.05366142 -0.09389530        Cuba
    ## 3:        0.1051149  0.16779131  0.67675600 -0.69460080 Puerto Rico
    ## 4:        0.9366501  1.48302162 -0.90826653  0.72613483     Jamaica
    ## 5:        0.1288233 -0.08837008  0.46528679 -0.56754896     Jamaica
    ## 6:       -0.7992905  0.26096544 -0.27169792  0.01367143     Jamaica

Functions can also be run on any `treedata.table` object with
`multiphylo` data. For instance, the following line will fit a phenogram
for `SVL` on each of the trees we provided in the `multiPhylo` object.

``` r

tdt(td, geiger::fitContinuous(phy, extractVector(td, 'SVL'), model="BM", ncores=1))
```

    ## Multiphylo object detected. Expect a list of function outputs

    ## [[1]]
    ## GEIGER-fitted comparative model of continuous data
    ##  fitted 'BM' model parameters:
    ##  sigsq = 0.136160
    ##  z0 = 4.065918
    ## 
    ##  model summary:
    ##  log-likelihood = -4.700404
    ##  AIC = 13.400807
    ##  AICc = 13.524519
    ##  free parameters = 2
    ## 
    ## Convergence diagnostics:
    ##  optimization iterations = 100
    ##  failed iterations = 0
    ##  number of iterations with same best fit = 100
    ##  frequency of best fit = 1.000
    ## 
    ##  object summary:
    ##  'lik' -- likelihood function
    ##  'bnd' -- bounds for likelihood search
    ##  'res' -- optimization iteration summary
    ##  'opt' -- maximum likelihood parameter estimates
    ## 
    ## [[2]]
    ## GEIGER-fitted comparative model of continuous data
    ##  fitted 'BM' model parameters:
    ##  sigsq = 0.136160
    ##  z0 = 4.065918
    ## 
    ##  model summary:
    ##  log-likelihood = -4.700404
    ##  AIC = 13.400807
    ##  AICc = 13.524519
    ##  free parameters = 2
    ## 
    ## Convergence diagnostics:
    ##  optimization iterations = 100
    ##  failed iterations = 0
    ##  number of iterations with same best fit = 100
    ##  frequency of best fit = 1.000
    ## 
    ##  object summary:
    ##  'lik' -- likelihood function
    ##  'bnd' -- bounds for likelihood search
    ##  'res' -- optimization iteration summary
    ##  'opt' -- maximum likelihood parameter estimates

The output is an object of class `list` with each element corresponding
to the output function of each tree in the provided `multiPhylo` object.
