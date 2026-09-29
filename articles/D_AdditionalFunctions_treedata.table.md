# Additional Functions for Manipulating Data in treedata.table

## Additional functions for manipulating data

`treedata.table` includes additional functions that allow the
identification of `discrete` and `continuous` characters in a given
dataset. We first load the dataset:

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

The
[`detectCharacterType()`](https://docs.ropensci.org/treedata.table/reference/detectCharacterType.md)
function can be used to examine whether `SVL` is `discrete` or
`continuous`:

``` r

detectCharacterType(anolis$dat$SVL)
```

    ## [1] "continuous"

We can further examine the type of characters we have in our dataset by
using the
[`detectAllCharacters()`](https://docs.ropensci.org/treedata.table/reference/detectAllCharacters.md)
function:

``` r

detectAllCharacters(anolis$dat)
```

    ##  [1] "discrete"   "continuous" "continuous" "continuous" "continuous"
    ##  [6] "continuous" "continuous" "continuous" "continuous" "discrete"  
    ## [11] "discrete"

Summarizing this information in a table, we get:

``` r

cbind.data.frame(character=colnames(anolis$dat),type=detectAllCharacters(anolis$dat))
```

    ##                 character       type
    ## 1                       X   discrete
    ## 2                     SVL continuous
    ## 3               PCI_limbs continuous
    ## 4               PCII_head continuous
    ## 5  PCIII_padwidth_vs_tail continuous
    ## 6        PCIV_lamella_num continuous
    ## 7             awesomeness continuous
    ## 8               hostility continuous
    ## 9                attitude continuous
    ## 10               ecomorph   discrete
    ## 11                 island   discrete

Finally, we can use the
[`filterMatrix()`](https://docs.ropensci.org/treedata.table/reference/filterMatrix.md)
function to subset our dataset to only a certain type of characters. For
instance, let’s extract all discrete characters in the *Anolis* dataset:

``` r

filterMatrix(anolis$dat, "discrete")
```

    ##                   X ecomorph      island
    ## 1              ahli       TG        Cuba
    ## 2           alayoni       TW        Cuba
    ## 3           alfaroi       GB        Cuba
    ## 4          aliniger       TC  Hispaniola
    ## 5          allisoni       TC        Cuba
    ## 6           allogus       TG        Cuba
    ## 7     altitudinalis       TC        Cuba
    ## 8           alumina       GB  Hispaniola
    ## 9         alutaceus       GB        Cuba
    ## 10      angusticeps       TW        Cuba
    ## 11      argenteolus        U        Cuba
    ## 12      argillaceus        U        Cuba
    ## 13          armouri       TG  Hispaniola
    ## 14    bahorucoensis       GB  Hispaniola
    ## 15         baleatus       CG  Hispaniola
    ## 16         baracoae       CG        Cuba
    ## 17        barahonae       CG  Hispaniola
    ## 18         barbatus        U        Cuba
    ## 19         barbouri        U  Hispaniola
    ## 20         bartschi        U        Cuba
    ## 21          bremeri       TG        Cuba
    ## 22         breslini       TG  Hispaniola
    ## 23     brevirostris        T  Hispaniola
    ## 24         caudalis        T  Hispaniola
    ## 25        centralis        U        Cuba
    ## 26   chamaeleonides        U        Cuba
    ## 27     chlorocyanus       TC  Hispaniola
    ## 28      christophei        U  Hispaniola
    ## 29        clivicola       GB        Cuba
    ## 30      coelestinus       TC  Hispaniola
    ## 31         confusus       TG        Cuba
    ## 32            cooki       TG Puerto Rico
    ## 33     cristatellus       TG Puerto Rico
    ## 34     cupeyalensis       GB        Cuba
    ## 35          cuvieri       CG Puerto Rico
    ## 36     cyanopleurus       GB        Cuba
    ## 37          cybotes       TG  Hispaniola
    ## 38      darlingtoni       TW  Hispaniola
    ## 39        distichus        T  Hispaniola
    ## 40  dolichocephalus       GB  Hispaniola
    ## 41        equestris       CG        Cuba
    ## 42       etheridgei        U  Hispaniola
    ## 43    eugenegrahami        U  Hispaniola
    ## 44        evermanni       TC Puerto Rico
    ## 45          fowleri        U  Hispaniola
    ## 46          garmani       CG Puerto Rico
    ## 47          grahami       TC Puerto Rico
    ## 48            guafe       TG        Cuba
    ## 49        guamuhaya        U        Cuba
    ## 50          guazuma       TW        Cuba
    ## 51        gundlachi       TG Puerto Rico
    ## 52        haetianus       TG  Hispaniola
    ## 53       hendersoni       GB  Hispaniola
    ## 54       homolechis       TG        Cuba
    ## 55            imias       TG        Cuba
    ## 56     inexpectatus       GB        Cuba
    ## 57        insolitus       TW  Hispaniola
    ## 58         isolepis       TC        Cuba
    ## 59            jubar       TG        Cuba
    ## 60            krugi       GB Puerto Rico
    ## 61       lineatopus       TG     Jamaica
    ## 62    longitibialis       TG  Hispaniola
    ## 63         loysiana        T        Cuba
    ## 64           lucius        U        Cuba
    ## 65     luteogularis       CG        Cuba
    ## 66       macilentus       GB        Cuba
    ## 67         marcanoi       TG  Hispaniola
    ## 68           marron        T  Hispaniola
    ## 69          mestrei       TG        Cuba
    ## 70        monticola        U  Hispaniola
    ## 71           noblei       CG        Cuba
    ## 72         occultus       TW Puerto Rico
    ## 73          olssoni       GB  Hispaniola
    ## 74         opalinus       TC     Jamaica
    ## 75       ophiolepis       GB        Cuba
    ## 76         oporinus       TC        Cuba
    ## 77         paternus       TW        Cuba
    ## 78         placidus       TW  Hispaniola
    ## 79        poncensis       GB Puerto Rico
    ## 80         porcatus       TC        Cuba
    ## 81           porcus        U        Cuba
    ## 82       pulchellus       GB Puerto Rico
    ## 83          pumilis        U        Cuba
    ## 84  quadriocellifer       TG        Cuba
    ## 85       reconditus        U     Jamaica
    ## 86         ricordii       CG  Hispaniola
    ## 87      rubribarbus       TG        Cuba
    ## 88           sagrei       TG        Cuba
    ## 89     semilineatus       GB  Hispaniola
    ## 90         sheplani       TW  Hispaniola
    ## 91          shrevei       TG  Hispaniola
    ## 92       singularis       TC  Hispaniola
    ## 93       smallwoodi       CG        Cuba
    ## 94          strahmi       TG  Hispaniola
    ## 95        stratulus       TC Puerto Rico
    ## 96      valencienni       TW     Jamaica
    ## 97        vanidicus       GB        Cuba
    ## 98     vermiculatus        U        Cuba
    ## 99         websteri        T  Hispaniola
    ## 100       whitemani       TG  Hispaniola

Two additional functions in `treedata.table` are designed to examine and
modify column and row names in any dataset. For instance, we can ask if
the *Anolis* dataset has column names:

``` r

hasNames(anolis$dat, "col")
```

    ##  col 
    ## TRUE

It does have column names. Let’s just remove the column names and check
if
[`hasNames()`](https://docs.ropensci.org/treedata.table/reference/hasNames.md)
can detect this change. Here’s our new dataset:

``` r

data=anolis$dat
colnames(data)<-NULL
head(data,2)
```

    ##                                                                        
    ## 1    ahli 4.039125 -3.248286  0.3722519 -1.042219 -2.4147423 -0.2416517
    ## 2 alayoni 3.815705  3.408886 -1.7833585  2.208451  0.9496969 -0.2590322
    ##                               
    ## 1 -0.1734769 0.6443771 TG Cuba
    ## 2  0.1273443 0.2959732 TW Cuba

Let’s run
[`hasNames()`](https://docs.ropensci.org/treedata.table/reference/hasNames.md)
on our new dataset:

``` r

hasNames(data, "col")
```

    ##   col 
    ## FALSE

Now, we can create new column names using the
[`forceNames()`](https://docs.ropensci.org/treedata.table/reference/forceNames.md)
function:

``` r

data <- forceNames(data, "col")
```

The new dataset, with column names (n1…), looks like this:

``` r

head(data,2)
```

    ##        n1       n2        n3         n4        n5         n6         n7
    ## 1    ahli 4.039125 -3.248286  0.3722519 -1.042219 -2.4147423 -0.2416517
    ## 2 alayoni 3.815705  3.408886 -1.7833585  2.208451  0.9496969 -0.2590322
    ##           n8        n9 n10  n11
    ## 1 -0.1734769 0.6443771  TG Cuba
    ## 2  0.1273443 0.2959732  TW Cuba

And we can finally ask whether our new dataset actually have column
names by running the
[`hasNames()`](https://docs.ropensci.org/treedata.table/reference/hasNames.md)
function again:

``` r

hasNames(data, "col")
```

    ##  col 
    ## TRUE

We can apply the same procedure for columns (`col`), rows (`row`) or
both (`rowcol`).
