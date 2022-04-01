# single-cell-studies

Notebook with example analysis and code for generating all figures in the manuscript `A curated database reveals trends in single cell transcriptomics`.

To obtain the data programatically, see instructions for different platforms below:

## With Python

```
In [1]: import pandas as pd

In [2]: data = pd.read_csv('http://nxn.se/single-cell-studies/data.tsv', sep='\t')

In [3]: data.head()
Out[3]:
                         Shorthand                            DOI                                            Authors  ... tSNE H5AD location                   Isolation
0             Tietjen et al Neuron  10.1016/S0896-6273(03)00229-0  Ian Tietjen, Jason M. Rihel, Yanxiang Cao, Geo...  ...  NaN           NaN                 Manual, LCM
1               Kurimoto et al NAR             10.1093/nar/gkl050                                        K. Kurimoto  ...  NaN           NaN                         NaN
2            Esumi et al NResearch   10.1016/j.neures.2007.12.011  Shigeyuki Esumi, Sheng-Xi Wu, Yuchio Yanagawa,...  ...   No           NaN                         NaN
3  Subkhankulova et al BMCGenomics        10.1186/1471-2164-9-268  Tatiana Subkhankulova, Michael J Gilchrist, Fr...  ...  NaN           NaN                         NaN
4                 Tang et al NMeth             10.1038/NMETH.1315  Fuchou Tang, Catalin Barbacioru, Yangzhou Wang...  ...   No           NaN  Pipetting (Manual picking)

[5 rows x 25 columns]
```

## With R

```
> library(tidyverse)

> data <- readr::read_delim('http://www.nxn.se/single-cell-studies/data.tsv', delim = '\t')
Parsed with column specification:
cols(
  .default = col_character(),
  Date = col_double(),
  `Reported cells total` = col_number(),
  `Panel size` = col_number(),
  `Number of reported cell types or clusters` = col_double()
)
See spec(...) for full column specifications.

> head(data)
# A tibble: 6 x 25
  Shorthand DOI   Authors Journal Title   Date `bioRxiv DOI` `Reported cells… Technique `Data location`
  <chr>     <chr> <chr>   <chr>   <chr>  <dbl> <chr>                    <dbl> <chr>     <chr>          
1 Tietjen … 10.1… Ian Ti… Neuron  Sing… 2.00e7 -                           37 PCR       NA             
2 Kurimoto… 10.1… K. Kur… Nuclei… An i… 2.01e7 -                           20 aRNA amp… GSE4309        
3 Esumi et… 10.1… Shigey… Neuros… Meth… 2.01e7 -                            8 Super SM… NA             
4 Subkhank… 10.1… Tatian… BMC Ge… Mode… 2.01e7 -                           12 PCR       NA             
5 Tang et … 10.1… Fuchou… Nat Me… mRNA… 2.01e7 -                            5 Tang      GSE14605       
6 Sul et a… 10.1… J.-Y. … Procee… Tran… 2.01e7 -                           48 aRNA amp… NA             
# … with 15 more variables: `Panel size` <dbl>, Measurement <chr>, Organism <chr>, Tissue <chr>, `Cell
#   source` <chr>, Contrasts <chr>, `Developmental stage` <chr>, `Number of reported cell types or
#   clusters` <dbl>, `Cell clustering` <chr>, Pseudotime <chr>, `RNA Velocity` <chr>, PCA <chr>,
#   tSNE <chr>, `H5AD location` <chr>, Isolation <chr>
``` 


## Accessing snapshots with gsutil

```
$ gsutil ls gs://single-cell-studies | tail
gs://single-cell-studies/data_snapshot_2019-08-06T08:00:00.tsv
gs://single-cell-studies/data_snapshot_2019-08-07T08:00:01.tsv
gs://single-cell-studies/data_snapshot_2019-08-10T08:00:04.tsv
gs://single-cell-studies/data_snapshot_2019-08-11T08:00:01.tsv
gs://single-cell-studies/data_snapshot_2019-08-12T08:00:06.tsv
gs://single-cell-studies/data_snapshot_2019-08-13T08:00:01.tsv
gs://single-cell-studies/data_snapshot_2019-08-14T08:00:06.tsv
gs://single-cell-studies/data_snapshot_2019-08-15T08:00:00.tsv
gs://single-cell-studies/data_snapshot_2019-08-16T08:00:01.tsv
gs://single-cell-studies/data_snapshot_2019-08-17T08:00:01.tsv

$ gsutil cp gs://single-cell-studies/data_snapshot_2019-08-17T08:00:01.tsv .
Copying gs://single-cell-studies/data_snapshot_2019-08-17T08:00:01.tsv...
/ [1 files][249.2 KiB/249.2 KiB]
Operation completed over 1 objects/249.2 KiB.

$ ls
data_snapshot_2019-08-17T08:00:01.tsv
```

