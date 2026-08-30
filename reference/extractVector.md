# Returning a named vector from a treedata.table object

Returning a named vector from a treedata.table object

## Usage

``` r
extractVector(tdObject, ...)
```

## Arguments

- tdObject:

  A treedata.table object

- ...:

  The name of the column or columns to select.

## Value

A named vector or a list of named vectors

## Examples

``` r

data(anolis)
td <- as.treedata.table(tree = anolis$phy, data = anolis$dat)
#> Tip labels detected in column: X
#> Phylo object detected 
#> All tips from original tree/dataset were preserved
# extracts the named vector for SVL from the td object
extractVector(td, "SVL")
#>            ahli         allogus     rubribarbus           imias          sagrei 
#>        4.039125        4.040138        4.078469        4.099687        4.067162 
#>         bremeri quadriocellifer      ophiolepis         mestrei           jubar 
#>        4.113371        3.901619        3.637962        3.987147        3.952605 
#>      homolechis        confusus           guafe         garmani        opalinus 
#>        4.032806        3.938442        3.877457        4.769473        3.838376 
#>         grahami     valencienni      lineatopus      reconditus       evermanni 
#>        4.154274        4.321524        4.128612        4.482607        4.165605 
#>       stratulus           krugi      pulchellus       gundlachi       poncensis 
#>        3.869881        3.886500        3.799022        4.188105        3.820378 
#>           cooki    cristatellus    brevirostris        caudalis          marron 
#>        4.091535        4.189820        3.874155        3.911743        3.831810 
#>        websteri       distichus        barbouri         alumina    semilineatus 
#>        3.916546        3.928796        3.663932        3.588941        3.696631 
#>         olssoni      etheridgei         fowleri       insolitus       whitemani 
#>        3.793899        3.657991        4.288780        3.800471        4.097479 
#>       haetianus        breslini         armouri         cybotes         shrevei 
#>        4.316542        4.051111        4.121684        4.210982        3.983003 
#>   longitibialis         strahmi        marcanoi        baleatus       barahonae 
#>        4.242103        4.274271        4.079485        5.053056        5.076958 
#>        ricordii   eugenegrahami     christophei         cuvieri        barbatus 
#>        5.013963        4.128504        3.884652        4.875012        5.003946 
#>          porcus  chamaeleonides       guamuhaya   altitudinalis        oporinus 
#>        5.038034        5.042349        5.036953        3.842994        3.845670 
#>        isolepis        allisoni        porcatus     argillaceus       centralis 
#>        3.657088        4.375390        4.258991        3.757869        3.697941 
#>         pumilis        loysiana         guazuma        placidus        sheplani 
#>        3.466860        3.701240        3.763884        3.773967        3.682924 
#>         alayoni     angusticeps        paternus       alutaceus    inexpectatus 
#>        3.815705        3.788595        3.802961        3.554891        3.537439 
#>       clivicola    cupeyalensis    cyanopleurus         alfaroi      macilentus 
#>        3.758726        3.462014        3.630161        3.526655        3.715765 
#>       vanidicus     argenteolus          lucius        bartschi    vermiculatus 
#>        3.626206        3.971307        4.198915        4.280547        4.802849 
#>        baracoae          noblei      smallwoodi    luteogularis       equestris 
#>        5.042780        5.083473        5.035096        5.101085        5.113994 
#>       monticola   bahorucoensis dolichocephalus      hendersoni     darlingtoni 
#>        3.770613        3.827445        3.908550        3.859835        4.302036 
#>        aliniger      singularis    chlorocyanus     coelestinus        occultus 
#>        4.036557        4.057997        4.275448        4.297965        3.663049 
# extracts the named vector for SVL and ecomorph from the td object
extractVector(td, "SVL", "ecomorph")
#> $SVL
#>            ahli         allogus     rubribarbus           imias          sagrei 
#>        4.039125        4.040138        4.078469        4.099687        4.067162 
#>         bremeri quadriocellifer      ophiolepis         mestrei           jubar 
#>        4.113371        3.901619        3.637962        3.987147        3.952605 
#>      homolechis        confusus           guafe         garmani        opalinus 
#>        4.032806        3.938442        3.877457        4.769473        3.838376 
#>         grahami     valencienni      lineatopus      reconditus       evermanni 
#>        4.154274        4.321524        4.128612        4.482607        4.165605 
#>       stratulus           krugi      pulchellus       gundlachi       poncensis 
#>        3.869881        3.886500        3.799022        4.188105        3.820378 
#>           cooki    cristatellus    brevirostris        caudalis          marron 
#>        4.091535        4.189820        3.874155        3.911743        3.831810 
#>        websteri       distichus        barbouri         alumina    semilineatus 
#>        3.916546        3.928796        3.663932        3.588941        3.696631 
#>         olssoni      etheridgei         fowleri       insolitus       whitemani 
#>        3.793899        3.657991        4.288780        3.800471        4.097479 
#>       haetianus        breslini         armouri         cybotes         shrevei 
#>        4.316542        4.051111        4.121684        4.210982        3.983003 
#>   longitibialis         strahmi        marcanoi        baleatus       barahonae 
#>        4.242103        4.274271        4.079485        5.053056        5.076958 
#>        ricordii   eugenegrahami     christophei         cuvieri        barbatus 
#>        5.013963        4.128504        3.884652        4.875012        5.003946 
#>          porcus  chamaeleonides       guamuhaya   altitudinalis        oporinus 
#>        5.038034        5.042349        5.036953        3.842994        3.845670 
#>        isolepis        allisoni        porcatus     argillaceus       centralis 
#>        3.657088        4.375390        4.258991        3.757869        3.697941 
#>         pumilis        loysiana         guazuma        placidus        sheplani 
#>        3.466860        3.701240        3.763884        3.773967        3.682924 
#>         alayoni     angusticeps        paternus       alutaceus    inexpectatus 
#>        3.815705        3.788595        3.802961        3.554891        3.537439 
#>       clivicola    cupeyalensis    cyanopleurus         alfaroi      macilentus 
#>        3.758726        3.462014        3.630161        3.526655        3.715765 
#>       vanidicus     argenteolus          lucius        bartschi    vermiculatus 
#>        3.626206        3.971307        4.198915        4.280547        4.802849 
#>        baracoae          noblei      smallwoodi    luteogularis       equestris 
#>        5.042780        5.083473        5.035096        5.101085        5.113994 
#>       monticola   bahorucoensis dolichocephalus      hendersoni     darlingtoni 
#>        3.770613        3.827445        3.908550        3.859835        4.302036 
#>        aliniger      singularis    chlorocyanus     coelestinus        occultus 
#>        4.036557        4.057997        4.275448        4.297965        3.663049 
#> 
#> $ecomorph
#>            ahli         allogus     rubribarbus           imias          sagrei 
#>            "TG"            "TG"            "TG"            "TG"            "TG" 
#>         bremeri quadriocellifer      ophiolepis         mestrei           jubar 
#>            "TG"            "TG"            "GB"            "TG"            "TG" 
#>      homolechis        confusus           guafe         garmani        opalinus 
#>            "TG"            "TG"            "TG"            "CG"            "TC" 
#>         grahami     valencienni      lineatopus      reconditus       evermanni 
#>            "TC"            "TW"            "TG"             "U"            "TC" 
#>       stratulus           krugi      pulchellus       gundlachi       poncensis 
#>            "TC"            "GB"            "GB"            "TG"            "GB" 
#>           cooki    cristatellus    brevirostris        caudalis          marron 
#>            "TG"            "TG"             "T"             "T"             "T" 
#>        websteri       distichus        barbouri         alumina    semilineatus 
#>             "T"             "T"             "U"            "GB"            "GB" 
#>         olssoni      etheridgei         fowleri       insolitus       whitemani 
#>            "GB"             "U"             "U"            "TW"            "TG" 
#>       haetianus        breslini         armouri         cybotes         shrevei 
#>            "TG"            "TG"            "TG"            "TG"            "TG" 
#>   longitibialis         strahmi        marcanoi        baleatus       barahonae 
#>            "TG"            "TG"            "TG"            "CG"            "CG" 
#>        ricordii   eugenegrahami     christophei         cuvieri        barbatus 
#>            "CG"             "U"             "U"            "CG"             "U" 
#>          porcus  chamaeleonides       guamuhaya   altitudinalis        oporinus 
#>             "U"             "U"             "U"            "TC"            "TC" 
#>        isolepis        allisoni        porcatus     argillaceus       centralis 
#>            "TC"            "TC"            "TC"             "U"             "U" 
#>         pumilis        loysiana         guazuma        placidus        sheplani 
#>             "U"             "T"            "TW"            "TW"            "TW" 
#>         alayoni     angusticeps        paternus       alutaceus    inexpectatus 
#>            "TW"            "TW"            "TW"            "GB"            "GB" 
#>       clivicola    cupeyalensis    cyanopleurus         alfaroi      macilentus 
#>            "GB"            "GB"            "GB"            "GB"            "GB" 
#>       vanidicus     argenteolus          lucius        bartschi    vermiculatus 
#>            "GB"             "U"             "U"             "U"             "U" 
#>        baracoae          noblei      smallwoodi    luteogularis       equestris 
#>            "CG"            "CG"            "CG"            "CG"            "CG" 
#>       monticola   bahorucoensis dolichocephalus      hendersoni     darlingtoni 
#>             "U"            "GB"            "GB"            "GB"            "TW" 
#>        aliniger      singularis    chlorocyanus     coelestinus        occultus 
#>            "TC"            "TC"            "TC"            "TC"            "TW" 
#> 
```
