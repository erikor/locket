# locket
A repository for useful slices of the LINCS dataset

The LINCS project has profiled the transcriptional effects of tens of thousands of perturbagens.  As you can imagine, the data files are large.  These large datafiles provide a phenomenal resource for translational research.  But their size makes reproducible research workflows unwieldy.  By this I mean that if I, for example, describe my research in an R markdown document to enable reproduction by any interesting party, reproduction of that work would require download of one or more data files that run in the 10s of gigabytes.  This may take hours and can be tedious if there are connection issues, etc.

However, if discreet chunks of such research involve a smallish subset of the LINCS data, the problem becomes more tractable.  But only if those data subsets are available separately.

This repository provides a number of logical subsets of the LINCS data as separate RDS files.  You can easily generate these files yourself with the provided code and the Level 3 data from LINCS (GSE92742_Broad_LINCS_Level3_INF_mlr12k_n1319138x12328.gctx).  The generation of these files is detailed in the vignette of the `slinky` R package, also on github.

I believe making this data available here complies with both the letter and the spirit of applicable rules governing distribution of the LINCS project.  If you are part of the LINCS project and feel differently, feel free to generate an issue on this repository to initiate discussion.
