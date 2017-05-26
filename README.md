# locket
A repository for useful slices of the LINCS dataset

The LINCS project has profiled the transcriptional effects of tens of thousands of perturbagens.  As you can imagine, the data files are large.  These large datafiles provide a phenomenal resource for translational research.  But their size makes reproducible research workflows unwieldy.  By this I mean that if I, for example, describe my research in an R markdown document to enable reproduction by any interesting party, reproduction of that work would require download of one or more data files that run in the 10s of gigabytes.  This may take hours and can be tedious if there are connection issues, etc.

However, if discreet chunks of such research involve a smallish subset of the LINCS data, the problem becomes more tractable.  But only if those data subsets are available separately.

This repository provides a number of logical subsets of the LINCS data as separate RDS files.  You can easily generate these files yourself with the provided code and the Level 3 data from LINCS (GSE92742_Broad_LINCS_Level3_INF_mlr12k_n1319138x12328.gctx).  The generation of these files is detailed in the vignette of the `slinky` R package, also on github.

I believe making this data available here complies with both the letter and the spirit of applicable rules governing distribution of the LINCS project.  If you are part of the LINCS project and feel differently, feel free to generate an issue on this repository to initiate discussion.

**NOTE ON x1000 FILES**

Storing floating point data takes more room than integer data.  I can make these files 3-4 times smaller by transforming floating point data to integer data.  I do this by multiplying floating point data by 1000 then converting to int.  To restore the data to its original floating point format, just divide by 1000.

Obviously, this only provides the data to 3 decimal places.  This is sufficient for my analytical workflows.  However I am open to increasing the precision if required.   

Alternatively, I could store the original data.  But Github only provide 1GB of free storage per repository so that would severely limit the number of files I could include in this repo without some type of fiscal support.


