# AIFI 10x 3' scRNA-seq PBMC Reference Generation

This repository stores the steps used to generate the AIFI PBMC Reference dataset based on 10x 3' scRNA-seq data. There are 5 major stages to this process:  
1. Sample selection and retrieval
2. Labeling with public references
3. Separating major classes and subclustering
4. Expert annotation of cell type identity of each cluster
5. Assembly of annotations and final reference dataset

The sections describe the notebooks utilized for each of these major steps.

These notebooks can be run sequentially based on their numeric prefix. They are also prefixed by the language/notebook kernel used in each (Python or R), as both languages are utilized in this analysis.

## Sample selection and retrieval

### 00-R_Sample_Selection.ipynb
In this notebook, we query the HISE database to identify samples from healthy subjects. We use only baseline samples from our flu vaccine treatment courses (usually labeled "Flu Year 1 Day 0") from 3 cohorts:  
UP1: Healthy pediatric samples from subjects 11-12 yr old; n = 16  
BR1: Healthy adult samples from subjects 25-35 yr old; n = 45  
BR2: Healthy adult samples from subjects 55-65 yr old; n = 47

After selection, we store the metadata for these samples in HISE for downstream steps.

### 01-Python_retrieve_cmv_bmi.ipynb
In this notebook, we retrieve CMV infection status and compute BMI for each subject based on clinical lab data stored in HISE (where available - no BMI for pediatric subjects). We then store this data in HISE for downstream steps.

### 02-Python_combine_data.ipynb
Here, we assemble all of the scRNA-seq data across the 108 samples into a single object, which we'll later label and split into separate cell classes. The resulting .h5ad file is stored in HISE for those downstream analysis steps.

## Labeling with public references

### 03-Python_Label_Predictions_Celltypist.ipynb
We use publically available reference models for the CellTypist cell labeling package to label our cells as a starting point for our expert cell labeling work.

### 04-R_Label_Predictions_Seurat.ipynb
To complement Celltypist labels, we also label our cells using Seurat and the Azimuth PBMC reference dataset.

### 05-Python_Doublet_detection.ipynb
We utilize the `scrublet` package to assign doublet labels to our cells, which we'll assess and remove in downstream analysis steps.

## Separating major classes and subclustering

### 06-Python_Subclustering
Here, we load the assembled dataset, add the CMV and BMI information, cluster all of the cells, and assign major cell classes: B cells, Myeloid cells, NK cells, Others, and T cells. For each cell class, we generate a separate .h5ad that will be used for class-specific analysis.

### 07-Python_B_cells.ipynb
Subclustering, marker gene identification, and visualizations for B cells, including plasmablasts.

### 08-Python_Myeloid_cells.ipynb
Subclustering, marker gene identification, and visualizations for Myeloid cells, including Monocytes and Dendritic cells.

### 09-Python_NK_cells.ipynb
Subclustering, marker gene identification, and visualizations for NK cells, including ILCs.

### 10-Python_Others.ipynb
Subclustering, marker gene identification, and visualizations for Other cell types, including Platelets, Erythrocytes, and developmental progenitor populations.

### 11-Python_T_cells.ipynb
Subclustering, marker gene identification, and visualizations for T cells, including CD4, CD8, dpT, dnT, and gdT cells.

## Expert Annotation

Expert annotations are based on the clusters, markers, and visualizations generated in the subclustering notebooks, above.

Annotation itself was performed by collaborative groups of AIFI researchers to generate 3 levels of labels for each of the major cell classes.

Tables of cluster annotations were then submitted to HISE, and will be retrieved by the assembly notebooks, below.

