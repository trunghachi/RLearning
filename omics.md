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
![image](./assets/45091486/de9ce624-d4ac-4032-9332-fdf9de4e106c)

## 2. AnnData and scanpy
![image](https://github.com/trunghachi/RLearning/assets/45091486/50db6ea5-906d-41f0-b30d-b35447a92742)
![AnnData](https://raw.githubusercontent.com/scverse/anndata/main/docs/_static/img/anndata_schema.svg)

[scRNAseq](https://rockefelleruniversity.github.io/scRNA-seq/)
