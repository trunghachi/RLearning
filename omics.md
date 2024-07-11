# scRNAseq

## A brief history of sequencing
### First generation sequencing
* 1969: DNA was already first isolated by Friedrich Miescher.
* 1953: Watson, Crick and Franklin discovered the structure of DNA
* 1965: Robert Holley sequenced the first tRNA
* 1972: Walter Fiers was the first to sequence a comlete gene (the coat protein of bacteriophage MS2); In parrallel, Friedrich Sanger developed a DNA sequencing method using radiolabeled;
* 1987: Leroy Hood and Michael Hunkapiller developed the ABI 370, automates the **Sanger Sequencing** process, automatically labeling of DNA fragment with fluorescent dyes instead of radioactive molecules.

### Second generation sequencing
* 1996: pyrosequencing (Mostafa Ronaghi, Mathias Uhlen, Pal Nyren) was primarily made possible by further automation in the lab, the usage of computers, and the miniaturization of reactions.
* 1998: **Solexa’s technology**, **Illumina's sequencer**
* 2005: Roche 454 sequencer was the first sequencer to fully automate the pyrosequencing process in a single, automated machine.
* 2007:  SOLiD systems’ “sequencing-by-ligation”
* 2011: Life Technologies’ Ion Torrent uses “sequencing-by-synthesis” to detect hydrogen ions when new DNA is synthesized.

### Third generation sequencing
long-read sequencing, which describes the ability to obtain nucleotide fragments of longer lengths than the usual Illumina short-read sequencers generate (order of 75 to 300 base pairs depending on the sequencer).
* 2010: **Pacific Biosciences (PacBio)** introduced zero-mode waveguide (ZMW) sequencing, which uses so-called nanoholes containing a single DNA polymerase. Reads obtained from PacBio sequencers are usually of 8 to 15 kilobases (kb), with possibilities for up to 70kb.
* 2012: **Oxford Nanopore Technologie**s introduced the GridION. The GridION and its successors MinION and Flongle are portable sequencers for DNA and RNA sequencing which produce reads of more than 2 Mb. Notably, such a sequencing device even fits into a single human hand. Oxford Nanopore sequencers observe changes in the electrical current that occur when nucleic acids pass through protein nanopores, to identify the nucleotide sequence

## Single-cell sequencing
* **scRNA-seq/snRNA-seq - Transcriptomics**
* scATAC-seq/snATAC-seq - Chromatin accessibility
* CITE-seq - Surface protein expression
* AIRR - TCR/BCR profiling
* Spatial-seq - Spatial profiling of gene expression.
## Single-cell platforms
* **10x Genomics (microfluidics)** (the most used technologies, 10x is 3' biased so will not provide full length transcript coverage.
As 10x is sequencing only the 3' of transcripts/genes, less sequencing depth is required per transcript/gene)
* Smart-seq3 (microfluidics)
* Drop-seq (microfluidics)
* VASA-seq (FANS)
* inDrop-seq (microfluidics)
* In-house solutions

## Terminology
* **PCR (Polymerase Chain Reaction)**: PCR is a technique used to amplify DNA or RNA sequences through repeated cycles of denaturation, annealing, and extension using specific primers and a DNA polymerase enzyme. In the context of single-cell sequencing, PCR is used to amplify nucleic acid molecules, including cDNA in scRNA-seq, and to generate sufficient material for downstream sequencing. PCR amplification is often performed after the introduction of cell barcodes and UMIs to amplify the genetic material tagged with these identifiers.
* **UMI (Unique Molecular Identifiers)**: which mRNA molecule the read comes from (help to detect PCR(Polymerase Chain Reaction) duplicates). UMIs are short random nucleotide sequences that are used to tag individual mRNA molecules before amplification in single-cell RNA sequencing (scRNA-seq) or other sequencing protocols.
* **Cell barcode**
* 
![image](https://github.com/trunghachi/RLearning/assets/45091486/e7766401-5fce-419a-8223-28c9532338f6)
![image](https://github.com/trunghachi/RLearning/assets/45091486/4720f706-e09c-453f-ba31-9adf2fa39269)
![image](https://github.com/trunghachi/RLearning/assets/45091486/aea85821-e999-4493-8252-953dabfb4c26)
![image](https://github.com/trunghachi/RLearning/assets/45091486/3a1966ed-4e2a-4ba2-bda0-b3dc82bbd9be)
![image](https://github.com/trunghachi/RLearning/assets/45091486/cf1711f3-204e-45a6-8152-7af75c51f23d)


### The 10x sequence reads
* Information on cell identity (10x barcode)
* Information on molecule identity (UMI)
* Information on sample identity (Index read)
* Information on the RNA molecule (transcriptome read)
![image](https://github.com/trunghachi/RLearning/assets/45091486/b3c77e0e-ebcb-464d-b1fc-b72bdf834aa0)

The output matrix is often stored in a compressed format such as **MEX** (Market Exchange Format), **HDF5** (Hierarchical Data Format)
#### CellRange HDF5
![image](https://github.com/trunghachi/RLearning/assets/45091486/c08ab23f-add5-4023-a7c2-b97bb1410c14)
- filtered_feature_bc_matrix.h5
- raw_feature_bc_matrix.h5
#### MEX (Market Exchange Format)
![image](https://github.com/trunghachi/RLearning/assets/45091486/7dd17d45-82b4-466a-b0c2-ac49b3eeb017)
- filtered_feature_bc_matrix
- raw_feature_bc_matrix

* **FASTA file** - File containing the full genome sequence for the reference of interest
* **GTF file** (Gene Transfer Format) - File containing the gene/transcript models for the reference of interest. Used to genome annotation, gtf file stores position, feature (exon) and meta-feature (transcript/gene) information.
* **BAM** file - alignments for all barcodes against the reference

# single-cell RNA-seq analysis
## 1. Seurat and Bioconductor
![image](https://github.com/trunghachi/RLearning//assets/45091486/de9ce624-d4ac-4032-9332-fdf9de4e106c)
![image](https://github.com/trunghachi/RLearning/assets/45091486/912207ad-c1d0-4852-ad13-259348be684d)


## 2. AnnData and scanpy
![image](https://github.com/trunghachi/RLearning/assets/45091486/50db6ea5-906d-41f0-b30d-b35447a92742)
![AnnData](https://raw.githubusercontent.com/scverse/anndata/main/docs/_static/img/anndata_schema.svg)

Core Components:
1. X (Expression Data): This is the heart of the AnnData object. It's typically a sparse matrix representing the gene expression data for all analyzed cells. Rows represent individual cells identified by unique barcodes, and columns represent genes. The matrix entries typically contain values indicating expression levels (e.g., counts, transcripts per million [TPM]).
2. Annotations:
a) obs (Cell Annotations): This is a pandas DataFrame associated with the observations (cells) in the data. It stores various annotations for each cell, such as:
 - Cell type labels: Categorical information about the cell type (e.g., T cell, B cell) based on gene expression patterns or prior knowledge.
 - Experimental conditions: Information about the experimental group or treatment each cell belongs to.
 - Doublet/singlet labels: Flags indicating if a cell is likely a single cell or a doublet (fusion of two cells).
 - Other relevant metadata: Any additional information specific to your experiment or analysis.
b) var (Gene Annotations): This is another pandas DataFrame associated with the variables (genes) in the data. It can store annotations for each gene, including: 
 - Gene names: Descriptive names for the genes represented in the expression matrix.
 - Gene symbols: Shorter, standardized identifiers for the genes.
 - Functional annotations: Information about the gene's function or pathway membership.
 - Other relevant metadata: Any additional information specific to your genes of interest.
3.Optional Components:
a) layers (Multidimensional Annotations): This dictionary can store additional data matrices with the same number of rows (cells) as the main expression matrix (X). These layers can represent various types of information, such as:
 - Reduced dimensionality data: Results from dimensionality reduction techniques like PCA, stored as a separate matrix.
 - Spliced vs. unspliced counts: Information about splicing events for specific genes.
 - Spatial coordinates: If spatial transcriptomics data is available, X and Y coordinates for each cell can be stored in a layer.
b) uns (Unstructured Annotations): This dictionary can hold various unstructured information related to the entire dataset, such as:
 - Sample information: Details about the sample source and preparation.
 - Processing steps: Information about the data normalization and filtering steps performed.
 - Software versions: Versions of the software used for data processing and analysis.
Relationships Between Components:
The components within an AnnData object are interconnected. The cell and gene annotations (obs and var) allow you to link specific expression values in the X matrix to individual cells and their characteristics. Similarly, layers and uns provide additional information that enriches the analysis of the core expression data

[scRNAseq](https://rockefelleruniversity.github.io/scRNA-seq/)

## Spatial Transcriptomic [Methods](https://www.mdpi.com/2073-4409/12/16/2042)
![image](https://github.com/trunghachi/RLearning/assets/45091486/f97c50aa-582a-4e81-95f6-730ec10b83de)
scRNAseq, GeoMx DSP, Xenium, Visium, CosMx, RNAscope, Opal Multiplex Polaris, CODEX

### 1. CosMx
CosMx is a spatial sequencing technology that provides detailed information about gene expression at the single-cell level.

- **Raw Data**:
  - **Images**: Spatial images of tissue sections.
  - **Expression Matrix**: Gene expression matrix (cells x genes).
  - **Spatial Coordinates**: Spatial coordinates of the cells or points within the sample.
- **Processed Data**:
  - **Cluster Information**: Data on cell clusters based on gene expression.
  - **Cell Types**: Classification of cells based on gene expression and spatial location.

### 2. Visium
Visium by 10x Genomics is a spatial sequencing technology that uses tissue sections to analyze gene expression spatially.
Visium offers medium-resolution spatial information. It captures gene expression at the level of tissue regions (spots), typically containing multiple cells (1-10 cells).

- **Raw Data**:
  - **H&E Images**: Hematoxylin and Eosin (H&E) stained images of tissue sections.
  - **Spatial Expression Matrix**: Gene expression matrix (spots x genes).
  - **Spatial Coordinates**: Spatial coordinates of the spots (locations).
- **Processed Data**:
  - **Cluster Information**: Information on clusters of cells or regions within the sample.
  - **Spot Annotations**: Annotations for spots, such as tissue type or disease state.

### 3. Xenium
Xenium is another spatial sequencing technology that provides spatial gene expression information in biological samples.
Xenium offers high-resolution data, enabling researchers to analyze gene expression at the level of single cells or even subcellular compartments.
- **Raw Data**:
  - **Images**: Spatial images of tissue sections.
  - **Expression Matrix**: Gene expression matrix (cells/spots x genes).
  - **Spatial Coordinates**: Spatial coordinates of the cells or spots within the sample.
- **Processed Data**:
  - **Cluster Information**: Information on clusters of cells or regions within the sample.
  - **Cell/Spot Types**: Classification of cells or spots based on gene expression and spatial location.

### 4. CODEX
CODEX (CO-Detection by indEXing) is a spatial imaging technology that uses labeled antibodies to co-detect multiple proteins within tissue sections.

- **Raw Data**:
  - **Multichannel Images**: Multichannel images of tissue sections, with each channel corresponding to a labeled antibody.
  - **Intensity Matrix**: Intensity matrix (cells x proteins).
  - **Spatial Coordinates**: Spatial coordinates of the cells or points within the sample.
- **Processed Data**:
  - **Cluster Information**: Information on clusters of cells based on protein expression.
  - **Cell Types**: Classification of cells based on protein expression and spatial location.

### scRNA-seq analysis pipeline
1. Preprocessing: expression matrix (genes*cells) -> filter cells/Quality control -> Normalization
2. Clustering: Identify variable genes -> Dimensionality Reduction -> Exploring Know Marker Genes -> Differentially Expressed Genes -> Assigning Cell Type -> Functional Annotation

### clustering cells and finding cluster marker genes pipeline
1. Check the quality of cells
2. Filter out low quality cells: empties, multiplets and broken cells. Empty: nFeature_RNA <200; doublet/multiplet: nFeature_RNA > 2500; Broken/dead cell in droplet: lot of mitochondrial transcrips(percent.mt >5%)
3. Normalize expression values: Global scaling normalization and SCTransform (normalization using **Pearson residuals**). scaling factor - a number, scale each cell to this total number of transcripts. SCTransform does 3 steps: 3-normalize; 4-identify highly variable genes; 5- scale data.
SCTransform does 3 steps: 3-normalize; 4-identify highly variable genes; 5- scale data
4. Identify highly variable genes: genes whose expression varies across the cells. Highly variable genes are used for PC. We cannot select genes base on their variance, because scRNAseq data has trong mean-variance relationship -> variance needs to be stabilized first with VST (variance stabilizing transformation) using log10, the fit a curve to predict the variance of each gene, compute standardized count and then for each gene compute the variance of the standardized values across all cells. 
Number of variable genes to return. Rank the genes base in their standardized variance and use the top 2000 genes for PCA and clustering.
5. Scale data, regress out unwanted variation: Standardize expression values for each gene across all cells prior to PCA; Z-score normalization in ScaleData function (shifts and scales the expression of each gene so mean=0, variance = 1; using option in ScaleData to regress out unwanted sources of variation (technical noise, batch effects, cell cycle stage, etc)
6. Reduce dimension PCA with variable genes: for clustering, for visualization
7. Determine significant PCs
8. Use the PCs to cluster cells with graph based clustering: **Louvain algorithm**
9. Visualize clusters with non-linear dimensional reduction (UMAP or tSNE) using the PCs
10. Detect and visualize marker genes for the clusters.

### Integrated Analysis
1. Check the quality of cells, filter out low quality cells
2. Normalize expression values
3. Identifying highly variable genes
4. Intergrate samples and perform CCA, align samples
5. Scale data, perform PCA
6. Cluster cells, visualize cluster with tSNE or UMAP
7. Find conserved biomarker for clusters
8. Find differentially expressed genes between samples, within clusters
9. Visualize interesting genes

