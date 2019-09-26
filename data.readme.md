## The Data
**This is an explanation of the data for the MMCS Hackathon 2019.**

There are two overarching datasets in this folder

1. **MMCS Dataset**: in the directory `mmcs`, contains the data that is the focus of this hackathon, including gene expression, protein expression, and TCR/BCR data from the 16 patients of interest with unknown phenotypes. The PBMCs from these patients and healthy controls were mixed in a single cell suspension and loaded onto 4 wells/lanes of the 10x Chromium instrument. 
2. **Flare Dataset**: in the `lupus.flare.tar.gz`, contains a gene and protein expression dataset from a study in the Ye Lab. This is a larger dataset (200k cells) that can be used for reference if you'd like to analyze in parallel to understand the single-cell manifestations of a cohort with flaring lupus. These patients have *known* phenotypes and these labels can be used for validation. The PBMCs from these patients and healthy controls were mixed in a single cell suspension and loaded onto the 10x Chromium instrument. These were run over the course of 4 experiments -- experiments 1 and 2 had 2 wells/lanes each, and experiments 3 and 4 had 4 wells/lanes each -- for a total of 12 wells/lanes.

In the `mmcs` directory, there are several files and directories

1. **`gex.and.fbc`**: This directory contains the aggregated feature-barcode matrices from the 4 lanes/wells, in both `.h5` and `.mtx` format, as well as the web summaries output by 10x's cellranger. Both the filtered matrix (i.e. filtered for legitimate cell barcodes, as deteremined by cellranger) and the raw matrix (i.e. all recognized barcodes, usually >700k) are present in these files. 

2. **2 tab-separated values (`.tsv`) files**: These files contain cell barcodes that have been demultiplexed according to their original donor using the SNPs present in the RNA transcripts. For every row in each of these files, there is the cell barcode (16-bp sequence), the number of SNPs that were observed, the droplet type that it was labeled -- either a single cell (singlet, SNG) or a two cells (doublet, DBL) -- and the anonymous ID that the cell barcode was assigned. In the demuxed.all.bcs.tsv, both singlets and doublets are present; in demuxed.sng.bcs.tsv, only singlets are present. <br /><br />Note that both the filtered and raw list of barcodes in the gex.and.fbc directory may contain doublets as determined from genetic demultiplexing, and that even after removing genetic doublets, there still may be other doublets (from the same individual) present in the data.

3. **`vdj.tar.gz`**: This tar archive contains the BCR and TCR data from all 4 wells of the experiment. These results have not been aggregated across the 4 wells of the experiment.

The lupus flare directory, if you choose to examine it, contains much of the same folder and files as the mmcs directory. Some differences are:

1. There were more wells/lanes done, so there is data from a larger number of cells. 

2. The protein expression data was processed separately and therefore is located in its own directory. This is labeled adts, for antibody-derived tags. 

3. Fewer proteins were analyzed in this experiment.

2. There is no VDJ (TCR and BCR) data.

*Note: to open `tar.gz` files, run `tar -xzvf` on the command line. For example, for the vdj dataset, run `tar -xzvf vdj.tar.gz`.*
