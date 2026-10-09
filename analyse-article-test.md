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
    ## [76] "filtered"

``` r
data_metadonner <- read.csv("SraRunTable.csv", sep = ',' , header = TRUE)
```

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
    ## [76] "filtered"

``` r
# Forward and reverse fastq filenames have format: SAMPLENAME_R1_001.fastq and SAMPLENAME_R2_001.fastq
fnFs <- sort(list.files(path, pattern="_1.fastq", full.names = TRUE))
fnRs <- sort(list.files(path, pattern="_2.fastq", full.names = TRUE))
# Extract sample names, assuming filenames have format: SAMPLENAME_XXX.fastq
sample.names <- sapply(strsplit(basename(fnFs), "_"), `[`, 1)
```

``` r
plotQualityProfile(fnFs[1:2])
```

![](analyse-article-test_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

``` r
plotQualityProfile(fnRs[1:2])
```

![](analyse-article-test_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

``` r
# Place filtered files in filtered/ subdirectory
filtFs <- file.path(path, "filtered", paste0(sample.names, "_F_filt.fastq.gz"))
filtRs <- file.path(path, "filtered", paste0(sample.names, "_R_filt.fastq.gz"))
names(filtFs) <- sample.names
names(filtRs) <- sample.names
```

``` r
out <- filterAndTrim(fnFs, filtFs, fnRs, filtRs, truncLen=c(230,190),
              maxN=0, maxEE=c(2,2), truncQ=2, rm.phix=TRUE,
              compress=TRUE, multithread= FALSE) # On Windows set multithread=FALSE (only needed for filterAndTrim)
head(out)
```

    ##                       reads.in reads.out
    ## ERR7132482_1.fastq.gz    56404     43684
    ## ERR7132483_1.fastq.gz    49918     13945
    ## ERR7132484_1.fastq.gz    98794     56879
    ## ERR7132485_1.fastq.gz    82577     38464
    ## ERR7132486_1.fastq.gz   100421     59208
    ## ERR7132487_1.fastq.gz   104462     56207

``` r
errF <- learnErrors(filtFs, multithread=TRUE)
```

    ## 104991090 total bases in 456483 reads from 12 samples will be used for learning the error rates.

``` r
errR <- learnErrors(filtRs, multithread=TRUE)
```

    ## 103612320 total bases in 545328 reads from 16 samples will be used for learning the error rates.

``` r
plotErrors(errF, nominalQ=TRUE)
```

    ## Warning in scale_y_log10(): log-10 transformation introduced infinite values.

    ## Warning: Removed 164 rows containing missing values or values outside the scale range
    ## (`geom_line()`).
    ## Removed 164 rows containing missing values or values outside the scale range
    ## (`geom_line()`).

![](analyse-article-test_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

``` r
dadaFs <- dada(filtFs, err=errF, multithread=TRUE)
```

    ## Sample 1 - 43684 reads in 8296 unique sequences.
    ## Sample 2 - 13945 reads in 3778 unique sequences.
    ## Sample 3 - 56879 reads in 12031 unique sequences.
    ## Sample 4 - 38464 reads in 8942 unique sequences.
    ## Sample 5 - 59208 reads in 12358 unique sequences.
    ## Sample 6 - 56207 reads in 12775 unique sequences.
    ## Sample 7 - 16806 reads in 6411 unique sequences.
    ## Sample 8 - 11481 reads in 3488 unique sequences.
    ## Sample 9 - 50399 reads in 12085 unique sequences.
    ## Sample 10 - 59083 reads in 16050 unique sequences.
    ## Sample 11 - 22613 reads in 9463 unique sequences.
    ## Sample 12 - 27714 reads in 7812 unique sequences.
    ## Sample 13 - 28607 reads in 11249 unique sequences.
    ## Sample 14 - 15591 reads in 6643 unique sequences.
    ## Sample 15 - 15463 reads in 6864 unique sequences.
    ## Sample 16 - 29184 reads in 5813 unique sequences.
    ## Sample 17 - 32511 reads in 6398 unique sequences.
    ## Sample 18 - 48453 reads in 7459 unique sequences.
    ## Sample 19 - 37348 reads in 6478 unique sequences.
    ## Sample 20 - 29556 reads in 5497 unique sequences.
    ## Sample 21 - 44517 reads in 7568 unique sequences.
    ## Sample 22 - 44975 reads in 7744 unique sequences.
    ## Sample 23 - 26389 reads in 4629 unique sequences.
    ## Sample 24 - 20878 reads in 3324 unique sequences.
    ## Sample 25 - 32761 reads in 6894 unique sequences.
    ## Sample 26 - 33942 reads in 5715 unique sequences.
    ## Sample 27 - 31640 reads in 3467 unique sequences.
    ## Sample 28 - 26510 reads in 4998 unique sequences.
    ## Sample 29 - 27906 reads in 5012 unique sequences.
    ## Sample 30 - 38459 reads in 5904 unique sequences.
    ## Sample 31 - 38194 reads in 4253 unique sequences.
    ## Sample 32 - 26003 reads in 10247 unique sequences.
    ## Sample 33 - 32726 reads in 11417 unique sequences.
    ## Sample 34 - 21687 reads in 7650 unique sequences.
    ## Sample 35 - 21525 reads in 8132 unique sequences.
    ## Sample 36 - 20420 reads in 8526 unique sequences.
    ## Sample 37 - 19996 reads in 7174 unique sequences.

``` r
dadaRs <- dada(filtRs, err=errR, multithread=TRUE)
```

    ## Sample 1 - 43684 reads in 10199 unique sequences.
    ## Sample 2 - 13945 reads in 5297 unique sequences.
    ## Sample 3 - 56879 reads in 14940 unique sequences.
    ## Sample 4 - 38464 reads in 10571 unique sequences.
    ## Sample 5 - 59208 reads in 13587 unique sequences.
    ## Sample 6 - 56207 reads in 14714 unique sequences.
    ## Sample 7 - 16806 reads in 6906 unique sequences.
    ## Sample 8 - 11481 reads in 4105 unique sequences.
    ## Sample 9 - 50399 reads in 14122 unique sequences.
    ## Sample 10 - 59083 reads in 17622 unique sequences.
    ## Sample 11 - 22613 reads in 9958 unique sequences.
    ## Sample 12 - 27714 reads in 9333 unique sequences.
    ## Sample 13 - 28607 reads in 12797 unique sequences.
    ## Sample 14 - 15591 reads in 7597 unique sequences.
    ## Sample 15 - 15463 reads in 7526 unique sequences.
    ## Sample 16 - 29184 reads in 10079 unique sequences.
    ## Sample 17 - 32511 reads in 10322 unique sequences.
    ## Sample 18 - 48453 reads in 12426 unique sequences.
    ## Sample 19 - 37348 reads in 11597 unique sequences.
    ## Sample 20 - 29556 reads in 8714 unique sequences.
    ## Sample 21 - 44517 reads in 10227 unique sequences.
    ## Sample 22 - 44975 reads in 12566 unique sequences.
    ## Sample 23 - 26389 reads in 7640 unique sequences.
    ## Sample 24 - 20878 reads in 5826 unique sequences.
    ## Sample 25 - 32761 reads in 10418 unique sequences.
    ## Sample 26 - 33942 reads in 8276 unique sequences.
    ## Sample 27 - 31640 reads in 5989 unique sequences.
    ## Sample 28 - 26510 reads in 9360 unique sequences.
    ## Sample 29 - 27906 reads in 6820 unique sequences.
    ## Sample 30 - 38459 reads in 10501 unique sequences.
    ## Sample 31 - 38194 reads in 7655 unique sequences.
    ## Sample 32 - 26003 reads in 11771 unique sequences.
    ## Sample 33 - 32726 reads in 13478 unique sequences.
    ## Sample 34 - 21687 reads in 9128 unique sequences.
    ## Sample 35 - 21525 reads in 10318 unique sequences.
    ## Sample 36 - 20420 reads in 9674 unique sequences.
    ## Sample 37 - 19996 reads in 8822 unique sequences.

``` r
dadaFs[[1]]
```

    ## dada-class: object describing DADA2 denoising results
    ## 634 sequence variants were inferred from 8296 input unique sequences.
    ## Key parameters: OMEGA_A = 1e-40, OMEGA_C = 1e-40, BAND_SIZE = 16

``` r
mergers <- mergePairs(dadaFs, filtFs, dadaRs, filtRs, verbose=TRUE)
```

    ## 15009 paired-reads (in 443 unique pairings) successfully merged out of 42295 (in 1366 pairings) input.

    ## 5473 paired-reads (in 155 unique pairings) successfully merged out of 13644 (in 409 pairings) input.

    ## 20100 paired-reads (in 506 unique pairings) successfully merged out of 55717 (in 1465 pairings) input.

    ## 14769 paired-reads (in 379 unique pairings) successfully merged out of 37685 (in 931 pairings) input.

    ## 24502 paired-reads (in 595 unique pairings) successfully merged out of 57585 (in 1692 pairings) input.

    ## 24157 paired-reads (in 637 unique pairings) successfully merged out of 54360 (in 2084 pairings) input.

    ## 6706 paired-reads (in 170 unique pairings) successfully merged out of 15767 (in 560 pairings) input.

    ## 2406 paired-reads (in 70 unique pairings) successfully merged out of 10900 (in 212 pairings) input.

    ## 27176 paired-reads (in 667 unique pairings) successfully merged out of 48854 (in 1608 pairings) input.

    ## 25645 paired-reads (in 636 unique pairings) successfully merged out of 56418 (in 3058 pairings) input.

    ## 9219 paired-reads (in 272 unique pairings) successfully merged out of 21047 (in 1408 pairings) input.

    ## 7919 paired-reads (in 228 unique pairings) successfully merged out of 26116 (in 919 pairings) input.

    ## 15505 paired-reads (in 475 unique pairings) successfully merged out of 26732 (in 1591 pairings) input.

    ## 6730 paired-reads (in 201 unique pairings) successfully merged out of 14398 (in 822 pairings) input.

    ## 7643 paired-reads (in 241 unique pairings) successfully merged out of 14031 (in 864 pairings) input.

    ## 16490 paired-reads (in 348 unique pairings) successfully merged out of 27970 (in 942 pairings) input.

    ## 17951 paired-reads (in 439 unique pairings) successfully merged out of 31057 (in 1047 pairings) input.

    ## 26001 paired-reads (in 438 unique pairings) successfully merged out of 47071 (in 1098 pairings) input.

    ## 22809 paired-reads (in 405 unique pairings) successfully merged out of 36068 (in 953 pairings) input.

    ## 15328 paired-reads (in 295 unique pairings) successfully merged out of 28415 (in 756 pairings) input.

    ## 21916 paired-reads (in 325 unique pairings) successfully merged out of 43273 (in 857 pairings) input.

    ## 27260 paired-reads (in 488 unique pairings) successfully merged out of 43445 (in 1182 pairings) input.

    ## 12969 paired-reads (in 277 unique pairings) successfully merged out of 25445 (in 709 pairings) input.

    ## 10354 paired-reads (in 205 unique pairings) successfully merged out of 20018 (in 517 pairings) input.

    ## 18563 paired-reads (in 480 unique pairings) successfully merged out of 31261 (in 1112 pairings) input.

    ## 16180 paired-reads (in 312 unique pairings) successfully merged out of 32950 (in 796 pairings) input.

    ## 23494 paired-reads (in 157 unique pairings) successfully merged out of 30936 (in 472 pairings) input.

    ## 13698 paired-reads (in 306 unique pairings) successfully merged out of 25263 (in 832 pairings) input.

    ## 16699 paired-reads (in 265 unique pairings) successfully merged out of 26885 (in 650 pairings) input.

    ## 19565 paired-reads (in 377 unique pairings) successfully merged out of 37312 (in 903 pairings) input.

    ## 26444 paired-reads (in 234 unique pairings) successfully merged out of 37236 (in 590 pairings) input.

    ## 10152 paired-reads (in 293 unique pairings) successfully merged out of 24057 (in 1662 pairings) input.

    ## 11731 paired-reads (in 279 unique pairings) successfully merged out of 30837 (in 1779 pairings) input.

    ## 9558 paired-reads (in 213 unique pairings) successfully merged out of 20278 (in 1140 pairings) input.

    ## 8649 paired-reads (in 267 unique pairings) successfully merged out of 19770 (in 1182 pairings) input.

    ## 7980 paired-reads (in 233 unique pairings) successfully merged out of 18817 (in 1296 pairings) input.

    ## 8575 paired-reads (in 233 unique pairings) successfully merged out of 18687 (in 808 pairings) input.

``` r
# Inspect the merger data.frame from the first sample
head(mergers[[1]])
```

    ##                                                                                                                                                                                                                                                                                                                                                                                                              sequence
    ## 3  TGAGGAATATTGCACAATGGAGGAAACTCTGATGCAGCAACGCCGCGTGGAGGATGACGCATTTCGGTGTGTAAACTCCTTTTATAGGTCAAGAAAATGACGGTAGCCTATGAATAAGCACCGGCTAACTCCGTGCCAGCAGCCGCGGTAATACGGAGGGTGCAAGCGTTATTCGGAATCACTGGGCGTAAAGGACACGTAGGCGGGAAGCCAAGTCTGATGTGAAATCCTATGGCTCAACCATAGAACTGCATTGGAAACTGGTTACCTAGAGTATGGGAGGGGGAGATGGAATTAGTGGTGTAGGGGTAAAATCCGTAGATATCACTAGGAATACCTAAAGCGAAGGCGATCTCCTGGAACATTACTGACGCTAAGGTGTGAAAGCGTGGGGAGCAAACG
    ## 6  TGGGGAATATTGCACAATGGAGGAAACTCTGATGCAGCAATGTCGCGTGAGTGAAGAAGGCCCTTGGGTCGTAAAGCTCTTTTATGGGGGAAGATGATGACGGTACCCCAAGAATAAGCACCGGCTAACTATGTGCCAGCAGCCGCGGTAATACATAGGGTGCGAGCGTTGTTCGGAATTACTGGGCGTAAAGGGCGCGCAGGCGGAATAGTAAGTCGGAGGTGAAAGCCCGGGGCTCAACCCCGGAGGGTCTTTCGAAACTACTAATCTAGAGAGGGTCAGGGGCCGGCAGAATTCCTGGTGTAGAGGTGAAATTCGTAGATATCAGGAGGAATACCGGTGGCGAAGGCGGCCGGCTGGGGCCACTCTGACGCTGAGGCGCGAAAGCGTGGGGAGCAAACA
    ## 7  TGGGGAATATTGCACAATGGAGGCAACTCTGATGCAGCAATGTCGCGTGAGTGAAGAAGGCCCTTGGGTCGTAAAGCTCTTTTATGGGGGAAGATGATGACGGTACCCCAAGAATAAGCACCGGCTAACTATGTGCCAGCAGCCGCGGTAATACATAGGGTGCGAGCGTTGTTCGGAATTACTGGGCGTAAAGGGCGCGCAGGCGGAATAGTAAGTCGGAGGTGAAAGCCCGGGGCTCAACCCCGGAGGGTCTTTCGAAACTGCTAATCTAGAGAGGGTCAGGGGCCGGCAGAATTCCTGGTGTAGAGGTGAAATTCGTAGATATCAGGAGGAATACCGGTGGCGAAGGCGGCCGGCTGGGGCCACTCTGACGCTGAGGCGCGAAAGCGTGGGGAGCAAACA
    ## 8  TGGGGAATATTGCACAATGGAGGCAACTCTGATGCAGCAATGTCGCGTGAGTGAAGAAGGCCCTTGGGTCGTAAAGCTCTTTTATGGGGGAAGATGATGACGGTACCCCAGGAATAAGCACCGGCTAACTATGTGCCAGCAGCCGCGGTAATACATAGGGTGCGAGCGTTGTTCGGAATTACTGGGCGTAAAGGGCGCGCAGGCGGAATAGTAAGTCGGAGGTGAAAGCCCGGGGCTCAACCCCGGAGGGTCTTTCGAAACTGCTAATCTAGAGAGGGTCAGGGGCCGGCAGAATTCCTGGTGTAGAGGTGAAATTCGTAGATATCAGGAGGAATACCGGTGGCGAAGGCGGCCGGCTGGGGCCACTCTGACGCTGAGGCGCGAAAGCGTGGGGAGCAAACA
    ## 9  TAGGGAATCTTGCACAATGGAGGAAACTCTGATGCAGCGATGCCGCGTGAGTGAAGAAGGCCTTTGGGTTGTAAAGCTCTTTCGTCGGGGAAGAAAATGACTGTACCCGAATAAGAAGGTCCGGCTAACTTCGTGCCAGCAGCCGCGGTAATACGAAGGGACCTAGCGTAGTTCGGAATTACTGGGCTTAAAGAGTTCGTAGGTGGTTAAAAAAGTTGGTGGTGAAATCCCAGAGCTTAACTCTGGAACTGCCATCAAAACTTTTTAGCTAGAGTATGATAGAGGAAAGCAGAATTTCTAGTGTAGAGGTGAAATTCGTAGATATTAGAAAGAATACCAATTGCGAAGGCAGCTTTCTGGATCATTACTGACACTGAGGAACGAAAGCATGGGTAGCGAAGA
    ## 11 TGGGGAATATTGCACAATGGAGGAAACTCTGATGCAGCAATGTCGCGTGAGTGAAGAAGGCCCTTGGGTCGTAAAGCTCTTTTATGGGGGAAGATGATGACGGTACCCCAGGAATAAGCACCGGCTAACTATGTGCCAGCAGCCGCGGTAATACATAGGGTGCGAGCGTTGTTCGGAATTACTGGGCGTAAAGGGCGCGCAGGCGGAATAGTAAGTCGGAGGTGAAAGCCCGGGGCTCAACCCCGGAGGGTCTTTCGAAACTGCTAATCTAGAGAGGGTCAGGGGCCGGCAGAATTCCTGGTGTAGAGGTGAAATTCGTAGATATCAGGAGGAATACCGGTGGCGAAGGCGGCCGGCTGGGGCCACTCTGACGCTGAGGCGCGAAAGCGTGGGGAGCAAACA
    ##    abundance forward reverse nmatch nmismatch nindel prefer accept
    ## 3       1636       3       3     18         0      0      2   TRUE
    ## 6        657       4       7     18         0      0      1   TRUE
    ## 7        512       6       4     18         0      0      2   TRUE
    ## 8        512       9       4     18         0      0      2   TRUE
    ## 9        487      10      11     18         0      0      1   TRUE
    ## 11       433      13       4     18         0      0      2   TRUE

``` r
seqtab <- makeSequenceTable(mergers)
dim(seqtab)
```

    ## [1]   37 2819

``` r
# Inspect distribution of sequence lengths
table(nchar(getSequences(seqtab)))
```

    ## 
    ##  260  261  300  376  383  384  385  386  387  388  389  394  400  401  402  403 
    ##    4    1    1    1    7   21   30    9    8    3    2    1    2   53 1182  854 
    ##  404  405  406  407  408 
    ##  183  391   33   22   11

``` r
seqtab.nochim <- removeBimeraDenovo(seqtab, method="consensus", multithread=TRUE, verbose=TRUE)
```

    ## Identified 967 bimeras out of 2819 input sequences.

``` r
dim(seqtab.nochim)
```

    ## [1]   37 1852
