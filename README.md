# public_sc

This is a draft repo for the colloboration between Geneve and Rennes to analyse single cell transriptomics data from mice and humans.

Note, the notebook only performs basic analyses- deliberiately, further downstream analyses are not performed here.

The starting point here is the CellRanger filered/non-filtered matrix(s) and the end point is a `results.h5ad` file, which can be read by `scanpy` or `seurat`.
This output file contains the filtered and normalized matrix across datasets without batch correction or any other processing.

## Usage

Clone this repo:
```
git clone https://gitlab.unige.ch/nef_lab/public_scrnaseq;
cd public_scrnaseq
```

Install `miniconda` and then create and activate the conda environment:
```
conda env create -f environment.yml
conda activate public_sc
```

Install `nbview` and `nbstripout` (you only need to do this once)
```
nbdime config-git --enable
nbstripout --install --attributes .gitattributes
```

Disable hash randomization (for reproducibility):
```
export PYTHONHASHSEED=0
```

Launch the Jupyter notebook:
```
jupyter-notebook basic_workflow.ipynb
```

You may edit the paramter Values in the `params_lst`. Then save the notebook, restart the kernel and re-run the whole notebook.

To de-activate and remove the environment:
```
conda deactivate
conda remove --name public_sc --all
```

## Tests

You can restart the entire notebook without changing anything to run the test data and you should have the following output at the bottom of the notebook:
```
INFO:root:Total number of cells: 8966
INFO:root:Total number of genes: 27664
```

Note the exact `results.h5ad` and it's `md5` is not reproduced exactly, even on one platform, but the file is ~63Mb.

The `test_data/` is the CellRanger v3 `filtered_feature_bc_matrix/` from scRNA-seq data derived from adult mice testis [Ernst et al. 2019](https://www.nature.com/articles/s41467-019-09182-1)

## Notes on ignored files
The jupyter-notebook in this repo never contains the outputs generated because of the `nbstripout` hook. Similarly, the `results.h5ad` file is not commited.
This is to ensure that the repistory stays small in size without the generated figures etc.
