# Daily python
## usual python pakages

## input and output
### base
### numpy
### pandas

- get the duplicate rows
```
cellranger_outs_genes_1 = cellranger_outs_genes.drop_duplicates(subset=[1])
cellranger_outs_genes_2 = cellranger_outs_genes.drop_duplicates(subset=[1],keep=False)
cellranger_outs_genes_3 = pd.concat([cellranger_outs_genes_1, cellranger_outs_genes_2]).drop_duplicates(subset=[1],keep=False)
```
### scipy


# python in bio


# visualization
