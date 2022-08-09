# CanineGliomaManuscript
This page provides the analysis code used for the paper entitled, "Tumor Microenvironment Modifying Immunotherapy Using Losartan and Propranolol with Vaccination Induces Objective Tumor Responses in a Canine Glioma Model."

### Data files (Input)

__220801_clinDataForR.csv__ - contains all the signalment and clinical outcomes for the 10 dogs enrolled in the study.

__220104_tp_titers_R.csv__ - contains the calculated endpoint titer for each patient in the study and jitter values for plotting the data. Raw endpoint titer data is available upon request to dyammons@colostate.edu or the corresponding authors.

__220120_amg_flow_data.csv__ - processed data obtained by flow cytometry used to evaluate cancer stem cell marker expression on various spheroid cell lines. Raw .lmd files available upon request to dyammons@colostate.edu or the corresponding authors.

__immuneInfiltrates_2_R.csv__ - calculated values in cells/mm^2 through analysis of IHC labeling of treated and untreated glioma tumors. Raw image data available upon request to dyammons@colostate.edu or the corresponding authors.

__meta.csv__ - metadata used for NanoString analysis. Patient signalment, batch, and sample names are listed for the 18 samples (n = 14 naive; n = 4 treated) used in the analysis.

__Normalized_n18_batched.csv__ - processed NanoString data obtained by running raw nSolver data through nCounter software. Values provided are normalized counts for each feature.

### Script

__analysisCode.Rmd__ - R markdown file that contains all the analysis code used in the generation of figures for the associated manuscript. Output will generate .png figures and an .html report of the knitted script.

### Output (Results)

__analysisCode.html__ - knitted html report generated from the analysisCode.Rmd file. This output contains all code used and the figures that were generated using the code.

__fig_2_A_B.png__ - Overall survival and progression free interval curves for all enrolled dogs. (A) overall survival and (B) progression free interval curves for all 10 dogs. One dog was censored due to not reaching an endpoint by the time of publication, while two additional dogs were censored from the overall survival data following deviation from treatment protocol. 

__fig_2_C.png__ - Plot represents tumor volume measurements, as determined by MRI, for all dogs enrolled in the trial. Tumor volume was evaluated every three months and volume was determined using transverse plane post-contrast T1-weighted images. 

__fig_3.png__ - Six of ten dogs exhibited detectable anti-glioma humoral responses. Humoral responses were quantified using flow cytometry-based endpoint titers with disaggregated J3T spheroids (A).

__fig_4.png__ - Dogs with detectable humoral responses have an increased overall survival rate. Depiction of (A) overall survival and (B) progression free interval curves stratified for vaccine responders (n = 6; blue) and non-responders (n = 4; red) for all 10 dogs.

__fig_5.png__ - Immunized dogs exhibit no detectable change in tumor infiltrating immune cells relative to untreated controls at the time of necropsy. Quantification of (A) T cell infiltrates (CD3+) and (B) macrophage infiltrates (MAC387+) at the time of necropsy.

__med_n.csv__ - output of the data (only median and n values; see test_data.csv for remaining values) used to create Supplemental Table 2 - Univariate analysis of key strata indicate humoral status is the only predictor of survival.

__output__ - log file generated from running analysisCode.Rmd on code ocean.

__sup_1.png__ - Spheroid culture enriches for CD44 on three canine cancer cell lines. Expression of key stem cell marker, CD44, as determined by flow cytometry for parental (blue) and spheroid (red) cells. The three cell lines depicted (Bliley, Jenny, and Gracie) were chosen to be used to make the allogenic vaccine. All other CSC markers (CD34, CD90, CD117, Sca1, CD133, CD24, and Oct3/4) were not expressed on either parental or spheroid cells. Values are reported in geometric mean florescence intensity and data was collected in singlet.

__sup_2.png__ - Patient serum has minimal reactivity to parental J3T cells and responders exhibit durable antibody responses. (A) depiction of antibody endpoint titers to parental J3T cells for a subset of patients enrolled in the trial (patients 2 & 4 = humoral non-responders; patients 3 & 5 = responders based on J3T spheroid titers). Endpoint titers for a subset of humoral responders (n=5) were conducted to evaluate durability of antibody responses (B).

__sup_5.png__ - Comparison of maximal response between humoral responders and non-responders. Evaluation of maximal tumor response by humoral status where each datapoint corresponds to a dog’s change in tumor volume from baseline (%). A Welch Two Sample t-test was conducted to evaluate statistical significance (p-val = 0.124).

__sup_6a.png & sup_6b.png__ - Differential gene expression analysis reveals enhanced immunoreactivity in high grade canine gliomas relative to low grade. (A) Volcano plot comparing high grade Nanostring data to low grade. Red indicates upregulated in high grade and blue indicates downregulated in high grade. P-value cutoff for adjusted p-values is 0.10 and log2(fold change) threshold is 0.58. (B) Dot plot of pathway enrichment analysis.

__sup_7.png__ - Tumor grade does not impact abundance of tumor infiltrating immune cells at the time of necropsy. Quantification of (A) T cell infiltrates (CD3+) and (B) macrophage infiltrates (MAC387+) at the time of necropsy from study and reference populations. Low = low grade gliomas; High = high grade gliomas.

__test_data.csv__ - output of the data (median survival time (ST), hazard ratio (HR) with confidence interval (CI), and p-value; see med_n.csv for remaining values) used to create Supplemental Table 2 - Univariate analysis of key strata indicate humoral status is the only predictor of survival.
