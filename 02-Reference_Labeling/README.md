## Labeling with public references

### 02-Python_combine_data.ipynb
Here, we assemble all of the scRNA-seq data across the 108 samples into a single object, which we'll later label and split into separate cell classes. The resulting .h5ad file is stored in HISE for those downstream analysis steps.

### 03-Python_Label_Predictions_Celltypist.ipynb
We use publically available reference models for the CellTypist cell labeling package to label our cells as a starting point for our expert cell labeling work.

### 04-R_Label_Predictions_Seurat.ipynb
To complement Celltypist labels, we also label our cells using Seurat and the Azimuth PBMC reference dataset.

### 05-Python_Doublet_detection.ipynb
We utilize the `scrublet` package to assign doublet labels to our cells, which we'll assess and remove in downstream analysis steps.
