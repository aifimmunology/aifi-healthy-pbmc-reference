# AIFI Immune Health Atlas Generation

This repository stores the steps used to generate the AIFI Immune Health Atlas dataset based on 10x 3' scRNA-seq data. There are 6 major stages to this process. Each stage is stored in a subdirectory in this repository:

- `01-Sample_selection`: Sample selection and retrieval
- `02-Reference_Labeling`: Labeling with public references
- `03-Subclustering`: Separating major classes and subclustering
- `04-Annotation`: Expert annotation of cell type identity of each cluster
- `05-Assembly`: Assembly of annotations and final reference dataset
- `06-Modeling`: Generation of cell type labeling models using CellTypist

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
<a id="legal_info"></a>

# Legal Information

<a id="license"></a>

## License

The license for this package is available on Github in the file LICENSE.txt in this repository.

<a id="support"></a>

## Level of Support

We are not currently supporting this code, but simply releasing it to the community AS IS but are not able to provide any guarantees of support. The community is welcome to submit issues, but you should not expect an active response.

<a id="contrib"></a>

## Contribution Agreement

If you contribute code to this repository through pull requests or other mechanisms, you are subject to the Allen Institute Contribution Agreement, which is available in the file CONTRIBUTING.md in this repository.
