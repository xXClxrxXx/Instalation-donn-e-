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

``` r
path <- "/home/rstudio/Instalation-donn-e-/data" # CHANGE ME to the directory containing the fastq files after unzipping.
list.files(path)
```

    ##  [1] "ena-file-download-selected-files-20261007-0855.sh"
    ##  [2] "ERR7132482_1.fastq.gz"                            
    ##  [3] "ERR7132482_2.fastq.gz"                            
    ##  [4] "ERR7132483_1.fastq.gz"                            
    ##  [5] "ERR7132483_2.fastq.gz"                            
    ##  [6] "ERR7132484_1.fastq.gz"                            
    ##  [7] "ERR7132484_2.fastq.gz"                            
    ##  [8] "ERR7132485_1.fastq.gz"                            
    ##  [9] "ERR7132485_2.fastq.gz"                            
    ## [10] "ERR7132486_1.fastq.gz"                            
    ## [11] "ERR7132486_2.fastq.gz"                            
    ## [12] "ERR7132487_1.fastq.gz"                            
    ## [13] "ERR7132487_2.fastq.gz"                            
    ## [14] "ERR7132488_1.fastq.gz"                            
    ## [15] "ERR7132488_2.fastq.gz"                            
    ## [16] "ERR7132489_1.fastq.gz"                            
    ## [17] "ERR7132489_2.fastq.gz"                            
    ## [18] "ERR7132490_1.fastq.gz"                            
    ## [19] "ERR7132490_2.fastq.gz"                            
    ## [20] "ERR7132491_1.fastq.gz"                            
    ## [21] "ERR7132491_2.fastq.gz"                            
    ## [22] "ERR7132492_1.fastq.gz"                            
    ## [23] "ERR7132492_2.fastq.gz"                            
    ## [24] "ERR7132493_1.fastq.gz"                            
    ## [25] "ERR7132493_2.fastq.gz"                            
    ## [26] "ERR7132494_1.fastq.gz"                            
    ## [27] "ERR7132494_2.fastq.gz"                            
    ## [28] "ERR7132495_1.fastq.gz"                            
    ## [29] "ERR7132495_2.fastq.gz"                            
    ## [30] "ERR7132496_1.fastq.gz"                            
    ## [31] "ERR7132496_2.fastq.gz"                            
    ## [32] "ERR7132497_1.fastq.gz"                            
    ## [33] "ERR7132497_2.fastq.gz"                            
    ## [34] "ERR7132498_1.fastq.gz"                            
    ## [35] "ERR7132498_2.fastq.gz"                            
    ## [36] "ERR7132499_1.fastq.gz"                            
    ## [37] "ERR7132499_2.fastq.gz"                            
    ## [38] "ERR7132500_1.fastq.gz"                            
    ## [39] "ERR7132500_2.fastq.gz"                            
    ## [40] "ERR7132501_1.fastq.gz"                            
    ## [41] "ERR7132501_2.fastq.gz"                            
    ## [42] "ERR7132502_1.fastq.gz"                            
    ## [43] "ERR7132502_2.fastq.gz"                            
    ## [44] "ERR7132503_1.fastq.gz"                            
    ## [45] "ERR7132503_2.fastq.gz"                            
    ## [46] "ERR7132504_1.fastq.gz"                            
    ## [47] "ERR7132504_2.fastq.gz"                            
    ## [48] "ERR7132505_1.fastq.gz"                            
    ## [49] "ERR7132505_2.fastq.gz"                            
    ## [50] "ERR7132506_1.fastq.gz"                            
    ## [51] "ERR7132506_2.fastq.gz"                            
    ## [52] "ERR7132507_1.fastq.gz"                            
    ## [53] "ERR7132507_2.fastq.gz"                            
    ## [54] "ERR7132508_1.fastq.gz"                            
    ## [55] "ERR7132508_2.fastq.gz"                            
    ## [56] "ERR7132509_1.fastq.gz"                            
    ## [57] "ERR7132509_2.fastq.gz"                            
    ## [58] "ERR7132510_1.fastq.gz"                            
    ## [59] "ERR7132510_2.fastq.gz"                            
    ## [60] "ERR7132511_1.fastq.gz"                            
    ## [61] "ERR7132511_2.fastq.gz"                            
    ## [62] "ERR7132512_1.fastq.gz"                            
    ## [63] "ERR7132512_2.fastq.gz"                            
    ## [64] "ERR7132551_1.fastq.gz"                            
    ## [65] "ERR7132551_2.fastq.gz"                            
    ## [66] "ERR7132552_1.fastq.gz"                            
    ## [67] "ERR7132552_2.fastq.gz"                            
    ## [68] "ERR7132553_1.fastq.gz"                            
    ## [69] "ERR7132553_2.fastq.gz"                            
    ## [70] "ERR7132554_1.fastq.gz"                            
    ## [71] "ERR7132554_2.fastq.gz"                            
    ## [72] "ERR7132555_1.fastq.gz"                            
    ## [73] "ERR7132555_2.fastq.gz"                            
    ## [74] "ERR7132556_1.fastq.gz"                            
    ## [75] "ERR7132556_2.fastq.gz"

``` r
# Forward and reverse fastq filenames have format: SAMPLENAME_R1_001.fastq and SAMPLENAME_R2_001.fastq
fnFs <- sort(list.files(path, pattern="_1.fastq", full.names = TRUE))
fnRs <- sort(list.files(path, pattern="_2.fastq", full.names = TRUE))
# Extract sample names, assuming filenames have format: SAMPLENAME_XXX.fastq
sample.names <- sapply(strsplit(basename(fnFs), "_"), `[`, 1)
```
