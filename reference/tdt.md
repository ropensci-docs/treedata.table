# Run a function on a `treedata.table` object

Run a function on a `treedata.table` object

## Usage

``` r
tdt(tdObject, ...)
```

## Arguments

- tdObject:

  A treedata.table object

- ...:

  A function call.

## Value

Function output for a single tree (phylo) or a list of function outputs
(one per each tree in the MultiPhylo object)

## Details

This function allows R functions that use trees and data to be run
on`treedata.table` objects.

## Examples

``` r
data(anolis)
# \donttest{

# A treedata.table object with a phylo $phy
td <- as.treedata.table(anolis$phy, anolis$dat)
#> Tip labels detected in column: X
#> Phylo object detected 
#> All tips from original tree/dataset were preserved
tdt(td, geiger::fitContinuous(phy, extractVector(td, "SVL"),
  model = "BM", ncores = 1
))
#> Phylo object detected. Expect a single function output
#> GEIGER-fitted comparative model of continuous data
#>  fitted ‘BM’ model parameters:
#>  sigsq = 0.136160
#>  z0 = 4.065918
#> 
#>  model summary:
#>  log-likelihood = -4.700404
#>  AIC = 13.400807
#>  AICc = 13.524519
#>  free parameters = 2
#> 
#> Convergence diagnostics:
#>  optimization iterations = 100
#>  failed iterations = 0
#>  number of iterations with same best fit = 100
#>  frequency of best fit = 1.000
#> 
#>  object summary:
#>  'lik' -- likelihood function
#>  'bnd' -- bounds for likelihood search
#>  'res' -- optimization iteration summary
#>  'opt' -- maximum likelihood parameter estimates


# A treedata.table object with a multiPhylo $phy
treesFM <- list(anolis$phy, anolis$phy)
class(treesFM) <- "multiPhylo"
td <- as.treedata.table(treesFM, anolis$dat)
#> Tip labels detected in column: X
#> Multiphylo object detected 
#> All tips from original tree/dataset were preserved
tdt(td, geiger::fitContinuous(phy, extractVector(td, "SVL"),
  model = "BM",
  ncores = 1
))
#> Multiphylo object detected. Expect a list of function outputs
#> [[1]]
#> GEIGER-fitted comparative model of continuous data
#>  fitted ‘BM’ model parameters:
#>  sigsq = 0.136160
#>  z0 = 4.065918
#> 
#>  model summary:
#>  log-likelihood = -4.700404
#>  AIC = 13.400807
#>  AICc = 13.524519
#>  free parameters = 2
#> 
#> Convergence diagnostics:
#>  optimization iterations = 100
#>  failed iterations = 0
#>  number of iterations with same best fit = 100
#>  frequency of best fit = 1.000
#> 
#>  object summary:
#>  'lik' -- likelihood function
#>  'bnd' -- bounds for likelihood search
#>  'res' -- optimization iteration summary
#>  'opt' -- maximum likelihood parameter estimates
#> 
#> [[2]]
#> GEIGER-fitted comparative model of continuous data
#>  fitted ‘BM’ model parameters:
#>  sigsq = 0.136160
#>  z0 = 4.065918
#> 
#>  model summary:
#>  log-likelihood = -4.700404
#>  AIC = 13.400807
#>  AICc = 13.524519
#>  free parameters = 2
#> 
#> Convergence diagnostics:
#>  optimization iterations = 100
#>  failed iterations = 0
#>  number of iterations with same best fit = 100
#>  frequency of best fit = 1.000
#> 
#>  object summary:
#>  'lik' -- likelihood function
#>  'bnd' -- bounds for likelihood search
#>  'res' -- optimization iteration summary
#>  'opt' -- maximum likelihood parameter estimates
#> 
# }
```
