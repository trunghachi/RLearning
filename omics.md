# scRNAseq
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
#### HDF5
![image](https://github.com/trunghachi/RLearning/assets/45091486/c08ab23f-add5-4023-a7c2-b97bb1410c14)
- filtered_feature_bc_matrix.h5
- raw_feature_bc_matrix.h5
#### MEX (Cell Ranger)
![image](https://github.com/trunghachi/RLearning/assets/45091486/7dd17d45-82b4-466a-b0c2-ac49b3eeb017)
- filtered_feature_bc_matrix
- raw_feature_bc_matrix

* **FASTA file** - File containing the full genome sequence for the reference of interest
* **GTF file** (Gene Transfer Format) - File containing the gene/transcript models for the reference of interest. Used to genome annotation, gtf file stores position, feature (exon) and meta-feature (transcript/gene) information.
* **BAM** file - alignments for all barcodes against the reference

# single-cell RNA-seq analysis
## 1. Seurat and Bioconductor
![image](https://github.com/trunghachi/RLearning//assets/45091486/de9ce624-d4ac-4032-9332-fdf9de4e106c)

## 2. AnnData and scanpy
![image](https://github.com/trunghachi/RLearning/assets/45091486/50db6ea5-906d-41f0-b30d-b35447a92742)
![AnnData](https://raw.githubusercontent.com/scverse/anndata/main/docs/_static/img/anndata_schema.svg)

[scRNAseq](https://rockefelleruniversity.github.io/scRNA-seq/)

## Spatial Transcriptomic [Methods](https://www.mdpi.com/2073-4409/12/16/2042)
![image](https://github.com/trunghachi/RLearning/assets/45091486/f97c50aa-582a-4e81-95f6-730ec10b83de)

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

- **Raw Data**:
  - **H&E Images**: Hematoxylin and Eosin (H&E) stained images of tissue sections.
  - **Spatial Expression Matrix**: Gene expression matrix (spots x genes).
  - **Spatial Coordinates**: Spatial coordinates of the spots (locations).
- **Processed Data**:
  - **Cluster Information**: Information on clusters of cells or regions within the sample.
  - **Spot Annotations**: Annotations for spots, such as tissue type or disease state.

### 3. Xenium
Xenium is another spatial sequencing technology that provides spatial gene expression information in biological samples.

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
