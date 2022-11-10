# CanineGliomaManuscript
This page provides the analysis code used for the paper entitled, "Reprogramming the Canine Glioma Microenvironment with Tumor Vaccination plus Oral Losartan and Propranolol Induces Objective Responses."

[![DOI](https://zenodo.org/badge/520531040.svg)](https://zenodo.org/badge/latestdoi/520531040)


### Data files (Input)

__220926_clinDataForR.csv__ - contains all the signalment and clinical outcomes for the 10 dogs enrolled in the study.

__220104_tp_titers_R.csv__ - contains the calculated endpoint titer for each patient in the study and jitter values for plotting the data. Raw endpoint titer data is available upon request to dyammons@colostate.edu or the corresponding authors.

__220120_amg_flow_data.csv__ - processed data obtained by flow cytometry used to evaluate cancer stem cell marker expression on various spheroid cell lines. Raw .lmd files available upon request to dyammons@colostate.edu or the corresponding authors.

__immuneInfiltrates_2_R.csv__ - calculated values in cells/mm^2 through analysis of IHC labeling of treated and untreated glioma tumors. Raw image data available upon request to dyammons@colostate.edu or the corresponding authors.

__meta.csv__ - metadata used for NanoString analysis. Patient signalment, batch, and sample names are listed for the 18 samples (n = 14 naive; n = 4 treated) used in the analysis.

__Normalized_n18_batched.csv__ - processed NanoString data obtained by running raw nSolver data through nCounter software. Values provided are normalized counts for each feature.

__geneList.csv__ - list of hgnc_symbol and description from ensembl database for the features identified as upregulated when comparing gene expression between high- and low-grade gliomas. This is loaded in as a .csv to avoid any potential connection errors with BioMart/Ensembl, but the code is provided in a noted-out section.

### Script

__analysisCode.Rmd__ - R markdown file that contains all the analysis code used in the generation of figures for the associated manuscript. Output will generate .png figures and an .html report of the knitted script.

### Output (Results)

__analysisCode.html__ - knitted html report generated from the analysisCode.Rmd file. This output contains all code used and the figures that were generated using the code.

__fig_2_A_B.png__ - Overall survival and progression free interval curves for all enrolled dogs. (A) overall survival and (B) progression free interval (PFI) curves for all 10 dogs are depicted. Two dogs were censored from the overall survival data following deviation from the treatment protocol (time of censorship is noted with a vertical hash mark). 

__fig_2_C.png__ - Plot (C) represents tumor volume measurements, as determined by MRI. Tumor volume was evaluated every three months and volume was determined using transverse plane post-contrast T1-weighted images. Measurements were recorded until death or withdrawal from study.

__fig_3.png__ - Six of ten dogs exhibited detectable anti-glioma humoral responses. Humoral responses to vaccination were quantified using flow cytometry-based endpoint titers with disaggregated J3T spheroids (A).

__fig_4.png__ - Dogs with detectable humoral responses have an increased overall survival rate. Depiction of (A) overall survival and (B) progression free interval curves stratified for vaccine responders (n = 6; red) and non-responders (n = 4; blue) for all 10 dogs.

__fig_5.png__ - Immunized dogs exhibit no detectable change in tumor infiltrating immune cells relative to untreated controls at the time of necropsy. Quantification of (A) T cell infiltrates (CD3+) and (B) macrophage infiltrates (MAC387+) at the time of necropsy in 4 study dogs and 14 untreated dogs with gliomas.

__med_n.csv__ - output of the data (only median and n values; see test_data.csv for remaining values) used to create Supplemental Table 2 - Univariate analysis of key strata indicate humoral status is the only predictor of survival.

__output__ - log file generated from running analysisCode.Rmd on code ocean.

__sup_1.png__ - Spheroid culture enriches for CD44 on three canine cancer cell lines. Expression of key stem cell marker, CD44, as determined by flow cytometry for parental (blue) and spheroid (red) cells. The three cell lines depicted (Bliley, Jenny, and Gracie) were chosen to be used in the allogenic vaccine. All other CSC markers (CD34, CD90, CD117, Sca1, CD133, CD24, and Oct3/4) were not expressed on either parental or spheroid cells. Values are reported in geometric mean florescence intensity and data was collected in singlet.

__sup_2.png__ - Patient serum has minimal reactivity to parental J3T. Depiction of antibody endpoint titers to parental J3T cells for a subset of patients enrolled in the trial (patients 2 & 4 = humoral non-responders; patients 3 & 5 = responders based on J3T spheroid titers).

__sup_5.png__ - Responders exhibit durable antibody responses. Endpoint titers for a subset of humoral responders (n = 5) were conducted to evaluate durability of antibody responses. Antibody binding to J3T spheroid cells was evaluated in this assay.

__sup_6.png__ - Comparison of maximal response between humoral responders and non-responders. Evaluation of maximal tumor response by humoral status where each datapoint corresponds to a dog’s change in tumor volume from baseline (%). A Wilcoxon two sample t-test was conducted to evaluate statistical significance (p-val = 0.11).

__sup_7a.png & sup_7b.png__ - Differential gene expression analysis reveals enhanced immunoreactivity in high-grade canine gliomas relative to low-grade. (A) Volcano plot comparing high-grade NanoString data to low-grade. Red indicates upregulated in high-grade, and blue indicates downregulated in high-grade (28 genes upregulated, 3 genes downregulated). P-value cutoff for adjusted p-values is 0.10 and log2(fold change) threshold is 0.58. (B) Dot plot of pathway enrichment analysis depicting upregulated pathways based on enriched genes in high-grade gliomas.

__sup_8.png__ - Tumor grade does not impact abundance of tumor infiltrating immune cells at the time of necropsy. Quantification of (A) T cell infiltrates (CD3+) and (B) macrophage infiltrates (MAC387+) at the time of necropsy from study and reference populations. Low = low-grade gliomas; High = high-grade gliomas. A Wilcoxon two sample t-test was conducted to evaluate statistical significance.

__test_data.csv__ - output of the data (median survival time (ST), hazard ratio (HR) with confidence interval (CI), and p-value; see med_n.csv for remaining values) used to create Supplemental Table 2 - Univariate analysis of key strata indicate humoral status is the only predictor of survival.

```r
> sessionInfo()
R version 4.0.3 (2020-10-10)
Platform: x86_64-w64-mingw32/x64 (64-bit)
Running under: Windows 10 x64 (build 19044)

Matrix products: default

locale:
[1] LC_COLLATE=English_United States.1252  LC_CTYPE=English_United States.1252    LC_MONETARY=English_United States.1252 LC_NUMERIC=C                          
[5] LC_TIME=English_United States.1252    

attached base packages:
[1] parallel  stats4    stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] org.Hs.eg.db_3.12.0         AnnotationDbi_1.52.0        broom_0.7.6                 biomaRt_2.46.3              ReactomePA_1.34.0          
 [6] ggrepel_0.9.1               DESeq2_1.30.1               SummarizedExperiment_1.20.0 Biobase_2.50.0              MatrixGenerics_1.2.1       
[11] matrixStats_0.58.0          GenomicRanges_1.42.0        GenomeInfoDb_1.26.7         IRanges_2.24.1              S4Vectors_0.28.1           
[16] BiocGenerics_0.36.0         cowplot_1.1.1               scales_1.1.1                RColorBrewer_1.1-2          reshape2_1.4.4             
[21] survminer_0.4.9             ggpubr_0.4.0                survival_3.2-11             lubridate_1.7.10            forcats_0.5.1              
[26] stringr_1.4.0               dplyr_1.0.5                 purrr_0.3.4                 readr_1.4.0                 tidyr_1.1.3                
[31] tibble_3.1.0                ggplot2_3.3.3               tidyverse_1.3.1            

loaded via a namespace (and not attached):
  [1] shadowtext_0.0.8       readxl_1.3.1           backports_1.2.1        fastmatch_1.1-0        BiocFileCache_1.14.0   plyr_1.8.6            
  [7] igraph_1.2.6           splines_4.0.3          BiocParallel_1.24.1    digest_0.6.27          htmltools_0.5.1.1      GOSemSim_2.16.1       
 [13] viridis_0.6.1          GO.db_3.12.1           fansi_0.4.2            checkmate_2.0.0        magrittr_2.0.1         memoise_2.0.0         
 [19] openxlsx_4.2.3         annotate_1.68.0        graphlayouts_0.7.1     modelr_0.1.8           askpass_1.1            prettyunits_1.1.1     
 [25] enrichplot_1.10.2      colorspace_2.0-0       rappdirs_0.3.3         blob_1.2.1             rvest_1.0.0            haven_2.4.1           
 [31] xfun_0.22              crayon_1.4.1           RCurl_1.98-1.3         jsonlite_1.7.2         graph_1.68.0           scatterpie_0.1.6      
 [37] genefilter_1.72.1      zoo_1.8-9              glue_1.4.2             polyclip_1.10-0        gtable_0.3.0           zlibbioc_1.36.0       
 [43] XVector_0.30.0         DelayedArray_0.16.3    graphite_1.36.0        car_3.0-10             abind_1.4-5            DOSE_3.16.0           
 [49] DBI_1.1.1              rstatix_0.7.0          Rcpp_1.0.6             progress_1.2.2         viridisLite_0.4.0      xtable_1.8-4          
 [55] reactome.db_1.74.0     foreign_0.8-81         bit_4.0.4              km.ci_0.5-2            httr_1.4.2             fgsea_1.16.0          
 [61] ellipsis_0.3.1         pkgconfig_2.0.3        XML_3.99-0.6           farver_2.1.0           dbplyr_2.1.1           locfit_1.5-9.4        
 [67] utf8_1.2.1             labeling_0.4.2         tidyselect_1.1.1       rlang_0.4.10           munsell_0.5.0          cellranger_1.1.0      
 [73] tools_4.0.3            cachem_1.0.4           cli_2.5.0              generics_0.1.0         RSQLite_2.2.7          evaluate_0.14         
 [79] fastmap_1.1.0          yaml_2.2.1             knitr_1.33             bit64_4.0.5            fs_1.5.0               tidygraph_1.2.0       
 [85] zip_2.1.1              survMisc_0.5.5         ggraph_2.0.5           DO.db_2.9              xml2_1.3.2             compiler_4.0.3        
 [91] rstudioapi_0.13        curl_4.3.1             ggsignif_0.6.1         reprex_2.0.0           tweenr_1.0.2           geneplotter_1.68.0    
 [97] stringi_1.5.3          lattice_0.20-44        Matrix_1.2-18          KMsurv_0.1-5           vctrs_0.3.7            pillar_1.6.0          
[103] lifecycle_1.0.0        BiocManager_1.30.15    data.table_1.14.0      bitops_1.0-7           qvalue_2.22.0          R6_2.5.0              
[109] gridExtra_2.3          rio_0.5.26             MASS_7.3-54            assertthat_0.2.1       openssl_1.4.4          withr_2.4.2           
[115] GenomeInfoDbData_1.2.4 hms_1.0.0              grid_4.0.3             rvcheck_0.1.8          rmarkdown_2.8          carData_3.0-4         
[121] ggforce_0.3.3          tinytex_0.31  
```
