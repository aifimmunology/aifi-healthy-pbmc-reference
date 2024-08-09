### Generation of cell type labeling models

The notebooks below use a fork of the CellTypist package to generate  CellTypist labeling models in order to enable use of multi-class logistic regression, which was used to generate the model for high-resolution (L3) cell types. For more information, see [the MultiCellTypist repository](https://github.com/aifimmunology/multicelltypist).

Models for each resolution of cell types were generated in two versions: one utilizing all available features in the original dataset (generated with 10x Genomics 3' scRNA-seq), and a second version utilizing only the features that are available in the 10x Genomics Single Cell Gene Expression Flex Human Transcriptome Probe Set v1.0 to enhance labeling of 10x Flex datasets.

#### L1 models (Broad types)

- **30-Python_celltypist_L1_model.ipynb**  
Generation of a labeling model for L1 cell types.  
- **30a-Python_celltypist_L1_model_flex-features.ipynb**  
Generation of a labeling model for L1 cell types using the 10x Flex feature set.

#### L2 models (Intermediate resolution)

- **31-Python_celltypist_L2_model.ipynb**  
Generation of a labeling model for L2 cell types.  
- **31a-Python_celltypist_L2_model_flex-features.ipynb**  
Generation of a labeling model for L2 cell types using the 10x Flex feature set.

#### L3 models (High resolution)

- **32-Python_celltypist_L3_model.ipynb**  
Generation of a labeling model for L3 cell types.  
- **32a-Python_celltypist_L3_model_flex-features.ipynb**  
Generation of a labeling model for L3 cell types using the 10x Flex feature set.
