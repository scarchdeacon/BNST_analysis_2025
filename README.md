## Description
This analysis was completed from February-November 2025 using single nucleus RNA-seq data collected in 2023 and 2024 by the Trainor lab in the UC Davis Department of Psychology. Analysis guidance was provided by the Nord lab at the UC Davis Center for Neuroscience. Findings were presented at the Society for Neuroscience meeting in San Diego, CA in November 2025.

BNST samples were collected from 24 California mice (*Peromyscus californicus*) (N = 12 males, 12 females). PVN samples (Step 6) were collected from 24 different California mice (N = 8 males, 16 females). For both datasets, sequencing was performed by the UC Davis Bioinformatics Core using the 10x Genomics Chromium Nuclei Isolation kit, yielding ~250,000 sequenced nuclei from the BNST and ~87,000 sequenced nuclei from the PVN. Raw data was processed with the 10X Genomics CellRanger pipeline before analysis in RStudio using Seurat v5.

## Summary of coding steps
**1. BNST Preprocessing** \
Seurat object creation \
Quality control/filtering \
Normalization (SCTransform) \
Principal components analysis (PCA) \
Clustering

**2. BNST Cell type assignment** \
Reference data Seurat object creation \
Reference data normalization, PCA, & clustering \
Reference-query data mapping \
By-cluster cell type voting \
Visualization

**3. Analysis of all BNST neurons** \
Quality control, filtering for non-BNST contamination \
Subset neurons \
Normalization, PCA, and clustering of neurons \
By-cluster differential expression (DE) analysis \
Cluster marker inspection \
Cluster labeling and visualization

**4. Analysis of BNST PVN-like neuron cluster (cluster 9)** \
Subset cluster 9 \
Normalization, PCA, and subclustering of cluster 9 neurons \
By-cluster DE analysis \
Cluster marker inspection \
Cluster labeling and visualization

**5. Analysis of BNST oxytocin neurons** \
Oxytocin (Oxt) expression inspection \
Subset Oxt-expressing neurons \
Normalization, PCA, and subclustering of Oxt neurons \
By-subcluster Oxt expression inspection

**6. Comparison of BNST and PVN oxytocin neurons** \
Reformat BNST and PVN Seurat object assays for compatibility

Normalization (SCT) and clustering of PVN Oxt neurons \
By-cluster DE analysis of PVN Oxt neurons \
Magnocellular/parvocellular marker inspection for PVN Oxt neurons

Normalization (SCT) and clustering of BNST Oxt neurons \
By-cluster DE analysis of BNST Oxt neurons \
Magnocellular/parvocellular marker inspection for BNST Oxt neurons

Integrate BNST and PVN Oxt neurons \
By-cluster DE analysis of all Oxt neurons \
Magnoceuular/parvocellular marker inspection for all Oxt neurons

*Note:* PVN data was preprocessed with a similar pipeline. Oxt neurons were identified 
through module-based marker expression comparison rather than label transfer. 

## Limitations
This analysis was exploratory and had limited sample sizes. Full reproducibility has not been verified in the 
current R environment, and results should be interpreted with caution. This workflow should serve as a reference
for analytical approaches rather than definitive conclusions. \
-BNST and PVN data were collected from different mice, so between-sample comparisons should be made with caution. \
-The data was not demultiplexed, so expression could not be compared at the level of biological replicates.

## Future directions / Things to change 
-SCTransform should be performed on individual samples rather than merged control and stress objects. \
-Cell typing could be performed on control and stress data together to streamline the workflow. \
-Module-based cell type scoring could be used instead of label transfer to streamline the worklow
 if only interested in identifying one cell type. \
-QC may have been too stringent (multiple rounds of filtering), could try using more lenient parameters and see if results are consistent.


 


