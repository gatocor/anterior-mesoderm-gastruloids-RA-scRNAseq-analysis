# Updates

 - 16/05/2025:
   - ADD to full analysis: Added UMAP plot with color code by condition. Highlight Wildtype+T_mutant and Wildtype+Eomes_mutant.
   - ADD projection analysis: Added projection to Susannes dataset

# Analysis by Batch

## Plots

### QC Metrics

1. **Total counts**: 
   - Histogram of total counts per cell.
   - Red vertical line indicates the minimum threshold.
   - Green vertical line indicates the maximum threshold.
   - Saved as `figures/{dataset_name}/qc_metrics.png`.

2. **Number of genes by counts**:
   - Histogram of the number of genes detected per cell.
   - Red vertical line indicates the minimum threshold.
   - Green vertical line indicates the maximum threshold.
   - Saved as `figures/{dataset_name}/qc_metrics.png`.

3. **Percent counts mitochondrial**:
   - Histogram of the percentage of mitochondrial counts per cell.
   - Red vertical line indicates the minimum threshold.
   - Green vertical line indicates the maximum threshold.
   - Saved as `figures/{dataset_name}/qc_metrics.png`.

4. **QC Metrics Scatterplot**:
   - Scatterplot of total counts vs. number of genes by counts, colored by the percentage of mitochondrial counts.
   - Saved as `figures/{dataset_name}/qc_metrics_scatterplot.png`.

### Doublets

1. **Doublet Score**:
   - UMAP plots showing doublet scores.
   - Saved as `figures/{dataset_name}/doublet_score.png`.

### Outliers

1. **Mean Neighbor Distance**:
   - Histogram of mean neighbor distances.
   - Red vertical line indicates the maximum threshold.
   - Saved as `figures/{dataset_name}/mean_neighbor_distance.png`.

2. **Mean Neighbor Distance Scatterplot**:
   - UMAP plots showing mean neighbor distances.
   - Saved as `figures/{dataset_name}/mean_neighbor_distance_scatterplot.png`.

### Dimensionality Reduction

1. **Highly Variable Genes**:
   - Scatterplots showing highly variable genes.
   - Saved as `figures/{dataset_name}/highly_variable_genes.png`.

2. **PCA Variance Ratio**:
   - Line plot of PCA variance ratios.
   - Red vertical line indicates the selected number of PCs.
   - Saved as `figures/{dataset_name}/pca_variance_ratio.png`.

3. **UMAP from PCA**:
   - UMAP plots from PCA.
   - Saved as `figures/{dataset_name}/umap_pca_vs_pca_phase.png`.

### Clustering

1. **Leiden Clustering**:
   - UMAP plots showing Leiden clustering at different resolutions.
   - Saved as `figures/{dataset_name}/leiden_{resolution}.png`.

## Tables

### Differential Expression

- Excel files containing differential expression results for each cluster at different resolutions.
- Saved as `tables/{dataset_name}/leiden_{resolution}.xlsx`.

## HTML

### Analysis Script

- HTML version of the analysis notebook.
- Saved as `script_versions/analysis_by_batch_{dataset[1]}_{dataset[2]}_{current_date}.html`.

## Adata Object

- Processed AnnData object.
- Saved as `data_processed/adata_{dataset_name}.h5ad`.

# Analysis by Condition

## Plots

### QC Metrics
- **qc_metrics.png**: Histograms showing the distribution of total counts, number of genes by counts, and percent counts mitochondrial. Vertical lines indicate the minimum and maximum thresholds for each metric.
- **qc_metrics_scatterplot.png**: Scatter plot of total counts vs. number of genes by counts, colored by percent counts mitochondrial.

### Doublets
- **doublet_score.png**: UMAP plots showing the doublet scores and a binary classification of doublets based on a threshold.

### Outliers
- **mean_neighbor_distance.png**: Histogram of mean neighbor distances with a vertical line indicating the maximum threshold.
- **mean_neighbor_distance_scatterplot.png**: UMAP plots showing the mean neighbor distances and a binary classification of outliers based on a threshold.

### Highly Variable Genes
- **highly_variable_genes.png**: Scatter plots showing the mean vs. dispersion and mean vs. normalized dispersion for highly variable genes.

### PCA
- **pca_variance_ratio.png**: Line plot showing the variance ratio explained by each principal component. A vertical line indicates the selected number of principal components.

### UMAP
- **umap_pca_vs_pca_phase.png**: UMAP plots comparing the original PCA and PCA corrected for cell cycle effects.

### Clustering
- **leiden_{resolution}.png**: UMAP plots showing the Leiden clustering results for different resolutions.

### Density by Sample
- **clustermap_leiden_{resolution}.png**: Scatter plots showing the number of cells per sample and Leiden cluster, normalized by sample and cluster.

### Analysis by Condition
- **violin_plots.png**: Violin plots showing the distribution of total counts, number of genes by counts, and percent counts mitochondrial for each sample.
- **umap_pca_vs_pca_sample.png**: UMAP plots comparing the original PCA and PCA corrected for batch effects.
- **umap_pca_vs_pca_phase.png**: UMAP plots comparing the original PCA and PCA corrected for cell cycle effects.

## Tables

### Differential Expression
- **leiden_{resolution}.xlsx**: Excel files containing the differential expression results for each Leiden cluster at different resolutions. Each sheet corresponds to a cluster and includes the gene names, scores, log fold changes, p-values, and adjusted p-values.

## HTML

### Analysis Script
- **script_versions/analysis_by_condition_{dataset_name}_{current_date}.html**: HTML version of the analysis script for condition analysis.

## Data

### Processed Data
- **data_processed/adata_{dataset_name}.h5ad**: Processed AnnData object saved in HDF5 format.

# Analysis Full

## Plots

### QC Metrics
- **qc_metrics.png**: Histograms showing the distribution of total counts, number of genes by counts, and percent counts mitochondrial. Vertical lines indicate the minimum and maximum thresholds for each metric.
- **qc_metrics_scatterplot.png**: Scatter plot of total counts vs. number of genes by counts, colored by percent counts mitochondrial.

### Doublets
- **doublet_score.png**: UMAP plots showing the doublet scores and a binary classification of doublets based on a threshold.

### Outliers
- **mean_neighbor_distance.png**: Histogram of mean neighbor distances with a vertical line indicating the maximum threshold.
- **mean_neighbor_distance_scatterplot.png**: UMAP plots showing the mean neighbor distances and a binary classification of outliers based on a threshold.

### Highly Variable Genes
- **highly_variable_genes.png**: Scatter plots showing the mean vs. dispersion and mean vs. normalized dispersion for highly variable genes.

### PCA
- **pca_variance_ratio.png**: Line plot showing the variance ratio explained by each principal component. A vertical line indicates the selected number of principal components.

### UMAP
- **umap_pca_vs_pca_phase.png**: UMAP plots comparing the original PCA and PCA corrected for cell cycle effects.

### Clustering
- **leiden_{resolution}.png**: UMAP plots showing the Leiden clustering results for different resolutions.

### Density by Sample
- **clustermap_leiden_{resolution}.png**: Scatter plots showing the number of cells per sample and Leiden cluster, normalized by sample and cluster.

### Density by Condition
- **clustermap_leiden_{resolution}.png**: Scatter plots showing the number of cells per condition and Leiden cluster, normalized by sample and cluster.

## Tables

### Differential Expression
- **leiden_{resolution}.xlsx**: Excel files containing the differential expression results for each Leiden cluster at different resolutions. Each sheet corresponds to a cluster and includes the gene names, scores, log fold changes, p-values, and adjusted p-values.

## HTML

### Analysis Script
- **script_versions/analysis_full_{current_date}.html**: HTML version of the analysis script for full dataset analysis.
