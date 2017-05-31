# locket
A repository for useful slices of the LINCS dataset

## Overview

The LINCS project has profiled the transcriptional effects of tens of thousands of perturbagens.  As you can imagine, the data files are large.  These large datafiles provide a phenomenal resource for translational research.  But their size makes reproducible research workflows unwieldy.  By this I mean that if I, for example, describe my research in an R markdown document to enable reproduction by any interesting party, reproduction of that work would require download of one or more data files that run in the 10s of gigabytes.  This may take hours and can be tedious if there are connection issues, etc.

However, if discreet chunks of such research involve a smallish subset of the LINCS data, the problem becomes more tractable.  But only if those data subsets are available separately.

This repository provides a number of logical subsets of the LINCS data as separate RDS files.  You can easily generate these files yourself with the provided code and the Level 3 data from LINCS (GSE92742_Broad_LINCS_Level3_INF_mlr12k_n1319138x12328.gctx).  The generation of these files is detailed in the vignette of the `slinky` R package, also on github.

I believe making this data available here complies with both the letter and the spirit of applicable rules governing distribution of the LINCS project.  If you are part of the LINCS project and feel differently, feel free to generate an issue on this repository to initiate discussion.

## Data Processing

For the CMAP data, the affymetrix data files were downloaded and processed by RMA.  Probe level annotations were updated to the latest genome build and mapped to Entrez Gene ID using the custom CDF files from http://brainarray.mbni.med.umich.edu (version 21).  Robust zscores were then calculated for each treated sample vs. the mean of vehicle control samples on the same plate (where robust z-score was calculated as x_i - median(x) / MAD(x)).

For the LINCS data, level 3 data was downloaded from GEO.  Sample metadata was obtained and highly consistent instances (`is_gold = true`) were identified using the `clue.io` REST API (facilitated by the `slinky` package, https://github.com/erikor/slinky).  Robust Z-scores vs. same plate vehicle control samples were then calculated.

**NOTE ON x1000 FILES**

Storing floating point data takes more room than integer data.  I can make these files 3-4 times smaller by transforming floating point data to integer data.  I do this by multiplying floating point data by 1000 then converting to int.  To restore the data to its original floating point format, just divide by 1000.

Obviously, this only provides the data to 3 decimal places.  This is sufficient for my analytical workflows.  However I am open to increasing the precision if required.   

Alternatively, I could store the original data.  But Github only provide 1GB of free storage per repository so that would severely limit the number of files I could include in this repo without some type of fiscal support.

## Available Files

**Available Files**

* **cmap_instances.txt** Details on the cmap instances (metadata)
* **cmap_zscores_vc_entrezg_x1000.rds** Data from the original CMAP project as robust z-scores (x1000) vs. vehicle controls from the same plate.
* **l1000_dmso.rds** 	LINCS expression values for the landmark genes in DMSO treated cells
* **l1000_fda.rds** 	LINCS expression values for samples treated with FDA approved compounds ("gold" instances only)
* **l1000_fda_zsvc_x1000.rds** Robust zscores (x1000) for the landmark genes for samples treated with FDA approved compounds relative to vehicle control samples from the same plate.
* **fda_zsvc_x1000.rds** Robust zscores (x1000) for the landmark genes for samples treated with FDA approved compounds relative to vehicle control samples from the same plate.
* **fda_inst_info.rds** Mapping from `distil_id` to `pert_desc` for l1000_fda and l1000_fda_zsvc files
* **test_inst_zsvc_x1000.rds** Small test dataset (50 instances, x1000 zscores vs. same plate controls)
* **test_inst_info.rds** Mapping from `distil_id` to `pert_desc` for test dataset (50 instances)
