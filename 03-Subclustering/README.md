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
Gamma-Delta T cells are assembled and reclustered to identify subpopulations. This includes gdT cells that are present in CD8 CM, CD8 EM, and MAIT cells, which are retrieved from the subclustering notebooks for these 3 types as well as a group of gdT cells that form their own cluster in the T cell overview.

#### 11i-Python_T_cells_isg-high.ipynb
Interferon-stimulated gene-high T cells are assembled and reclustered to identify subpopulations.
