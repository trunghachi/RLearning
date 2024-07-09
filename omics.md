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
#### MEX
![image](https://github.com/trunghachi/RLearning/assets/45091486/7dd17d45-82b4-466a-b0c2-ac49b3eeb017)


![image](https://github.com/trunghachi/RLearning/assets/45091486/ef8baeaf-e190-4703-9ea4-1a195346fe90)
[scRNAseq](https://rockefelleruniversity.github.io/scRNA-seq/)
