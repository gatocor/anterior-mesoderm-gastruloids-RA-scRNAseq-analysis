[![DOI](https://zenodo.org/badge/1017566638.svg)](https://doi.org/10.5281/zenodo.18045898)

# Anterior Mesoderm Gastruloids RA - Single Cell RNA-seq Analysis

This project contains single-cell RNA sequencing (scRNA-seq) analysis of mouse embryonic samples comparing wildtype, T-mutant, and Eomes-mutant conditions across multiple biological replicates.

## Project Structure

```
.
├── data/                              # Aligned Raw data files to be downloaded from the deposited source
│   ├── adata_Eomes_mutant_rep1.h5ad
│   ├── adata_Eomes_mutant_rep2.h5ad
│   ├── adata_T_mutant_rep1.h5ad
│   ├── adata_T_mutant_rep2.h5ad
│   ├── adata_wildtype_rep1.h5ad
│   ├── adata_wildtype_rep2.h5ad
│   └── adata_wildtype_rep3.h5ad
├── data_other_studies/                # External datasets for comparison
│   ├── pijuan/
│   ├── prisca/
│   └── susanne/
├── data_processed/                    # Processed h5ad objects
│   ├── adata_*.h5ad                   # Individual sample and merged datasets
├── figures/                           # Generated plots and visualizations
├── tables/                            # Differential expression results
├── script_versions/                   # Archived HTML versions of analysis scripts
├── analysis_*.ipynb                   # Analysis notebooks
├── annotations.csv                    # Cell type marker annotations
├── markers.csv                        # Marker gene list
├── gene_list*.csv                     # Gene lists for analysis
├── pathways.json                      # Pathway definitions
├── parameters_*.csv                   # Analysis parameters
├── environment_legacy.yml             # Conda environment specification with the full package set and specific versions used to run the code (only for legacy)
├── environment.yml.                   # Conda environment specification with only the explicitely installed packages (for any platform, RECOMENDED)
└── README.md                          # This file
```

## Experimental Design

The project analyzes three experimental conditions:
- **Wildtype**: Control samples (3 replicates)
- **T_mutant**: T gene mutant (2 replicates)
- **Eomes_mutant**: Eomes gene mutant (2 replicates)

## Analysis Workflows

### Main Analysis Notebooks

1. **`create_h5ad.ipynb`**: Initial data processing and h5ad object creation
2. **`analysis_full.ipynb`**: Comprehensive analysis of merged dataset
3. **`analysis_by_condition.ipynb`**: Condition-specific analysis
4. **`analysis_by_batch.ipynb`**: Batch-wise analysis
5. **`analysis_projection.ipynb`**: Data projection analysis
6. **`analysis_projection_time.ipynb`**: Temporal projection analysis
7. **`analysis_scenic.ipynb`**: Gene regulatory network analysis using SCENIC

### Setup Notebooks

- **`setup_external_datasets.ipynb`**: Import and process external datasets
- **`setup_priscas_data.ipynb`**: Process Prisca's dataset

## Analysis Pipeline

The standard analysis pipeline includes:

1. **Quality Control (QC)**
   - Cell filtering based on counts, genes detected, and mitochondrial content
   - Visualization of QC metrics

2. **Normalization**
   - Total count normalization
   - Log transformation

3. **Dimensionality Reduction**
   - Highly variable gene selection (top 2000 genes)
   - PCA (30 components)
   - UMAP visualization

4. **Batch Correction**
   - Harmony integration across samples
   - Cell cycle regression (optional)

5. **Clustering**
   - Leiden clustering at multiple resolutions (0.1, 0.2, 0.5, 1.0)
   - Cluster annotation using marker genes

6. **Differential Expression Analysis**
   - Wilcoxon rank-sum test
   - Results exported to Excel files

7. **Pathway Enrichment**
   - Decoupler ULM analysis
   - Pathway activity scores

8. **Comparative Analysis**
   - Cross-condition comparisons
   - Cluster composition analysis

## Key Parameters

Default parameters (from `parameters_full.csv`):
- **n_top_genes**: 2000
- **n_pcs**: 30
- **n_neighbors**: 15
- **cell_cycle_regression**: true
- **resolutions**: [0.1, 0.2, 0.5, 1]

## Dependencies

The project uses a conda environment specified in `environment.yml`. Key packages include:
- scanpy: Single-cell analysis
- anndata: Annotated data matrices
- matplotlib/seaborn: Visualization
- pandas/numpy: Data manipulation
- decoupler: Pathway enrichment analysis
- harmonypy: Batch correction

## Setup

1. Create the conda environment:
```bash
conda env create -f environment.yml
conda activate scrnaseq_vitamin_a
```

2. Launch Jupyter:
```bash
jupyter notebook
```

3. Run the analysis notebooks in order

## Outputs

### Figures
Generated visualizations are saved in `figures/` organized by dataset:
- UMAP plots
- QC plots
- Marker dotplots and heatmaps
- Differential expression visualizations
- Cluster composition plots

### Tables
Differential expression results in `tables/` as Excel files with one sheet per cluster

### Script Versions
HTML exports of executed notebooks with timestamps in `script_versions/`

## Helper Modules

- **`auxiliar.py`**: Custom helper functions for visualization and analysis
- **`scmap.py`**: Single-cell mapping utilities

## Configuration Files

- **`annotations.csv`**: Cell type marker gene definitions
- **`markers.csv`**: Curated marker gene list
- **`pathways.json`**: Pathway gene sets
- **`renumbering_leiden.json`**: Cluster renumbering map
- **`cell_cycle_G1_S.txt`**: G1/S phase genes
- **`cell_cycle_G2_M.txt`**: G2/M phase genes

## Notes

- All analysis scripts automatically create output directories if they don't exist
- Processed data objects (h5ad) are saved after major processing steps
- Analysis versions are archived with timestamps for reproducibility
