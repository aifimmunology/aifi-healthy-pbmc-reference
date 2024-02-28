# AIFI 10x 3' scRNA-seq PBMC Reference Generation

This repository stores the steps used to generate the AIFI PBMC Reference dataset based on 10x 3' scRNA-seq data. There are 5 major stages to this process:  
1. Sample selection and retrieval
2. Labeling with public references
3. Separating major classes and subclustering
4. Expert annotation of cell type identity of each cluster
5. Assembly of annotations and final reference dataset

The sections describe the notebooks utilized for each of these major steps.

These notebooks can be run sequentially based on their numeric prefix. They are also prefixed by the language/notebook kernel used in each (Python or R), as both languages are utilized in this analysis.

## Contributors

### Analysis
Qiuyu Gong: Analysis lead, composed most original notebook versions  
Lucas Graybuck: Review, documentation, linting, and reproducibility management  
Xiao-jun Li: Analysis oversight  
Mehul Sharma: Original version of 07a-Python_B_cells_without_IGHLCK.ipynb

### Annotation
Aishwarya Chander: Annotation contributor; Ontology lead    
Marla Glass: B cell annotation lead  
Claire Gustafson: Scientific lead; T cell annotation lead  
Emma Kuan: Myeloid cell annotation lead  
Tao Peng: NK cell annotation lead  
Mehul Sharma: B cell Annotation contributor  
Mansi Singh: Myeloid cell annotation contributor  

## Sample selection and retrieval

Notebooks related to sample selection and retrieval are stored in the `01-Sample_selection/` subdirectory.

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

Notebooks related to public reference labeling and doublet detection are stored in the `02-Reference_Labeling/` subdirectory.

### 03-Python_Label_Predictions_Celltypist.ipynb
We use publically available reference models for the CellTypist cell labeling package to label our cells as a starting point for our expert cell labeling work.

### 04-R_Label_Predictions_Seurat.ipynb
To complement Celltypist labels, we also label our cells using Seurat and the Azimuth PBMC reference dataset.

### 05-Python_Doublet_detection.ipynb
We utilize the `scrublet` package to assign doublet labels to our cells, which we'll assess and remove in downstream analysis steps.

## Separating major classes and subclustering

Notebooks related to subclustering within classes are stored in the `03-Subclustering/` subdirectory.

### 06-Python_Subclustering
Here, we load the assembled dataset, add the CMV and BMI information, cluster all of the cells, and assign major cell classes: B cells, Myeloid cells, NK cells, Others, and T cells. For each cell class, we generate a separate .h5ad that will be used for class-specific analysis.

### 07-Python_B_cells.ipynb
Subclustering, marker gene identification, and visualizations for B cells, including plasmablasts.

#### 07a-Python_B_cells_without_Igs.ipynb
B cells are also clustered without Immunoglobulins and subclustered within non-effector memory B cells. This reclustering is used for type assignment.

### 08-Python_Myeloid_cells.ipynb
Subclustering, marker gene identification, and visualizations for Myeloid cells, including Monocytes and Dendritic cells.

### 09-Python_NK_cells.ipynb
Subclustering, marker gene identification, and visualizations for NK cells, including ILCs.

### 10-Python_Others.ipynb
Subclustering, marker gene identification, and visualizations for Other cell types, including Platelets, Erythrocytes, and developmental progenitor populations.

### 11-Python_T_cells.ipynb
Subclustering, marker gene identification, and visualizations for T cells, including CD4, CD8, dpT, dnT, and gdT cells.

T cell subsets are iteratively clustered to increase resolution of cell types:

#### 11a-Python_T_cells_cd4-naive.ipynb
Naive CD4 T cells are assembled and reclustered to identify subpopulations.

#### 11b-Python_T_cells_cd8-mait.ipynb
MAIT cells are assembled and reclustered to identify subpopulations.

#### 11c-Python_T_cells_cd8-cm.ipynb
CD8 Central Memory are assembled and reclustered to identify subpopulations.

#### 11d-Python_T_cells_cd8-em.ipynb
CD8 Effector Memory cells are assembled and reclustered to identify subpopulations.

#### 11e-Python_T_cells_treg.ipynb
Treg cells are assembled and reclustered to identify subpopulations.

#### 11f-Python_T_cells_cd8-naive.ipynb
CD8 Naive cells are assembled and reclustered to identify subpopulations.

#### 11g-Python_T_cells_proliferating.ipynb
Proliferating T cells are assembled and reclustered to identify subpopulations.

#### 11h-Python_T_cells_gd.ipynb
Gamma-Delta T cells are assembled and reclustered to identify subpopulations.

#### 11i-Python_T_cells_isg-high.ipynb
Interferon-stimulated gene-high T cells are assembled and reclustered to identify subpopulations.


## Expert Annotation

Notebooks related to annotations of clustered cells are stored in the `04-Annotation/` subdirectory.

Expert annotations are based on the clusters, markers, and visualizations generated in the subclustering notebooks, above.

Annotation itself was performed by collaborative groups of AIFI researchers to generate 3 levels of labels for each of the major cell classes.

The set of notebooks for annotations connect CSV files generated by domain experts that assign an identity to each Leiden cluster for these cell classes:

### 12-Python_B_cell_annotations.ipynb
Annotations for B cells and non-effector memory B cell subclusters.

### 13-Python_Myeloid_cell_annotations.ipynb
Annotations for Myeloid cells and their subclusters.

### 14-Python_NK_cell_annotations.ipynb
Annotations for NK cell types.

### 15-Python_Other_annotations.ipynb
Annotations for Platelets, Erythrocytes, and developmental progenitor populations.

### 16-Python_T_cell_annotations.ipynb
Annotations for T cells and their subclusters.

## Label Assembly

Notebooks related to assembly of reference labels are stored in the `05-Assembly/` subdirectory.

To assemble final labels, we retrieve the cluster annotations generated by our domain experts, assign these to individual cell barcodes based on our clustering analysis, and assemble the entire set of labels for all of the cell barcodes in our reference.

### 17-Python_assign_B_cells.ipynb
Assignment of annotations to B cell barcodes

### 18-Python_assign_Myeloid_cells.ipynb
Assignment of annotations to Myeloid cell barcodes

### 19-Python_assign_NK_cells.ipynb
Assignment of annotations to NK cell barcodes

### 20-Python_assign_Other_cells.ipynb
Assignment of annotations to Other barcodes

### 21-Python_assign_T_cells.ipynb
Assignment of annotations to T cell barcodes

### 22-Python_assemble_final_labels
Assemble all barcode labels across all classes to generate a final set of labels.
