# Filter a character matrix, returning either all continuous or all discrete characters

This function filters a character matrix based on continuous (e.g., with
values 2.45, 9.35, and so on) or discrete characters (e.g., with values
blue, red, yellow).

## Usage

``` r
filterMatrix(mat, returnType = "discrete")
```

## Arguments

- mat:

  A character matrix of class data.frame

- returnType:

  Either discrete or continuous

## Value

data.frame with only discrete (default) or continuous characters

## Examples

``` r
data(anolis)
filterMatrix(anolis$dat, "discrete")
#>                   X ecomorph      island
#> 1              ahli       TG        Cuba
#> 2           alayoni       TW        Cuba
#> 3           alfaroi       GB        Cuba
#> 4          aliniger       TC  Hispaniola
#> 5          allisoni       TC        Cuba
#> 6           allogus       TG        Cuba
#> 7     altitudinalis       TC        Cuba
#> 8           alumina       GB  Hispaniola
#> 9         alutaceus       GB        Cuba
#> 10      angusticeps       TW        Cuba
#> 11      argenteolus        U        Cuba
#> 12      argillaceus        U        Cuba
#> 13          armouri       TG  Hispaniola
#> 14    bahorucoensis       GB  Hispaniola
#> 15         baleatus       CG  Hispaniola
#> 16         baracoae       CG        Cuba
#> 17        barahonae       CG  Hispaniola
#> 18         barbatus        U        Cuba
#> 19         barbouri        U  Hispaniola
#> 20         bartschi        U        Cuba
#> 21          bremeri       TG        Cuba
#> 22         breslini       TG  Hispaniola
#> 23     brevirostris        T  Hispaniola
#> 24         caudalis        T  Hispaniola
#> 25        centralis        U        Cuba
#> 26   chamaeleonides        U        Cuba
#> 27     chlorocyanus       TC  Hispaniola
#> 28      christophei        U  Hispaniola
#> 29        clivicola       GB        Cuba
#> 30      coelestinus       TC  Hispaniola
#> 31         confusus       TG        Cuba
#> 32            cooki       TG Puerto Rico
#> 33     cristatellus       TG Puerto Rico
#> 34     cupeyalensis       GB        Cuba
#> 35          cuvieri       CG Puerto Rico
#> 36     cyanopleurus       GB        Cuba
#> 37          cybotes       TG  Hispaniola
#> 38      darlingtoni       TW  Hispaniola
#> 39        distichus        T  Hispaniola
#> 40  dolichocephalus       GB  Hispaniola
#> 41        equestris       CG        Cuba
#> 42       etheridgei        U  Hispaniola
#> 43    eugenegrahami        U  Hispaniola
#> 44        evermanni       TC Puerto Rico
#> 45          fowleri        U  Hispaniola
#> 46          garmani       CG Puerto Rico
#> 47          grahami       TC Puerto Rico
#> 48            guafe       TG        Cuba
#> 49        guamuhaya        U        Cuba
#> 50          guazuma       TW        Cuba
#> 51        gundlachi       TG Puerto Rico
#> 52        haetianus       TG  Hispaniola
#> 53       hendersoni       GB  Hispaniola
#> 54       homolechis       TG        Cuba
#> 55            imias       TG        Cuba
#> 56     inexpectatus       GB        Cuba
#> 57        insolitus       TW  Hispaniola
#> 58         isolepis       TC        Cuba
#> 59            jubar       TG        Cuba
#> 60            krugi       GB Puerto Rico
#> 61       lineatopus       TG     Jamaica
#> 62    longitibialis       TG  Hispaniola
#> 63         loysiana        T        Cuba
#> 64           lucius        U        Cuba
#> 65     luteogularis       CG        Cuba
#> 66       macilentus       GB        Cuba
#> 67         marcanoi       TG  Hispaniola
#> 68           marron        T  Hispaniola
#> 69          mestrei       TG        Cuba
#> 70        monticola        U  Hispaniola
#> 71           noblei       CG        Cuba
#> 72         occultus       TW Puerto Rico
#> 73          olssoni       GB  Hispaniola
#> 74         opalinus       TC     Jamaica
#> 75       ophiolepis       GB        Cuba
#> 76         oporinus       TC        Cuba
#> 77         paternus       TW        Cuba
#> 78         placidus       TW  Hispaniola
#> 79        poncensis       GB Puerto Rico
#> 80         porcatus       TC        Cuba
#> 81           porcus        U        Cuba
#> 82       pulchellus       GB Puerto Rico
#> 83          pumilis        U        Cuba
#> 84  quadriocellifer       TG        Cuba
#> 85       reconditus        U     Jamaica
#> 86         ricordii       CG  Hispaniola
#> 87      rubribarbus       TG        Cuba
#> 88           sagrei       TG        Cuba
#> 89     semilineatus       GB  Hispaniola
#> 90         sheplani       TW  Hispaniola
#> 91          shrevei       TG  Hispaniola
#> 92       singularis       TC  Hispaniola
#> 93       smallwoodi       CG        Cuba
#> 94          strahmi       TG  Hispaniola
#> 95        stratulus       TC Puerto Rico
#> 96      valencienni       TW     Jamaica
#> 97        vanidicus       GB        Cuba
#> 98     vermiculatus        U        Cuba
#> 99         websteri        T  Hispaniola
#> 100       whitemani       TG  Hispaniola
```
