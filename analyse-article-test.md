R Notebook
================

# ls = list show

# ls \| wc (work cont) -l (pour ligne) \# permet de compter les lignes.

# telécharger les metadonée, aller sur sra run selctor, télécharger a table en cliquant sur metadata. Donne fichier excel.

# importer l’excel, read.cvs header = TRUE spe = “,”

# 3ème commande data2 changer ce qu’il y a entre “” pour qu eça corresponde à nos donner.

# retéléchrargement écrase fichier et prend des nouveau

``` r
meta_data_table <- read.csv("SraRunTable.csv", sep = ",", header = TRUE)
```

``` r
library(dada2); packageVersion("dada2")
```

    ## Loading required package: Rcpp

    ## Warning: multiple methods tables found for 'transform'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'Biostrings'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'IRanges'

    ## Warning: multiple methods tables found for 'transform'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'XVector'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'Seqinfo'

    ## Warning: multiple methods tables found for 'detail'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'ShortRead'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'GenomicRanges'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'GenomicAlignments'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'SummarizedExperiment'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'S4Arrays'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'DelayedArray'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'SparseArray'

    ## Warning: multiple methods tables found for 'scale'

    ## Warning: replacing previous import 'BiocGenerics::scale' by
    ## 'DelayedArray::scale' when loading 'SummarizedExperiment'

    ## Warning: replacing previous import 'BiocGenerics::detail' by
    ## 'Biostrings::detail' when loading 'GenomicAlignments'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'cigarillo'

    ## Warning: replacing previous import 'BiocGenerics::detail' by
    ## 'Biostrings::detail' when loading 'cigarillo'

    ## Warning: replacing previous import 'BiocGenerics::detail' by
    ## 'Biostrings::detail' when loading 'ShortRead'

    ## Warning: replacing previous import 'utils::data' by 'BiocGenerics::data' when
    ## loading 'pwalign'

    ## Warning: replacing previous import 'BiocGenerics::transform' by
    ## 'S4Vectors::transform' when loading 'pwalign'

    ## Warning: replacing previous import 'BiocGenerics::detail' by
    ## 'Biostrings::detail' when loading 'pwalign'

    ## [1] '1.40.0'
