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
* *Lưu ý: Việc tăng số lượng các reads để phục vụ cho việc giải trình tự, vì thiết bị có độ nhạy nhất định, tuy nhiên nó có thể gây ra amplification bias, hay lỗi sao chép do enzyme polymerase và làm mất đi tính đồng nhất do không phải đoạn nào cũng được khuếch đại giống các đoạn khác, để giảm thiểu sai lệch người ta sử dụng cell barcode và UMIs nhằm loại bỏ sự trùng lặp cũng như kiểm tra tính chính xác của đoạn đọc*
* **UMI (Unique Molecular Identifiers)**: which mRNA molecule the read comes from (help to detect PCR(Polymerase Chain Reaction) duplicates). UMIs are short random nucleotide sequences that are used to tag individual mRNA molecules before amplification in single-cell RNA sequencing (scRNA-seq) or other sequencing protocols.
* **Cell barcode** Cell type markers are genes or proteins with expression specific to a particular cell type. They act as flags that help researchers distinguish different cell types within the data. (examples: CD3, GFAP, Cytokeratin, etc.)

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

Để tìm số counts của các genes, cần sử dụng các chương trình mapping như **STAR** hay **HISAT2**. The output matrix is often stored in a compressed format such as **MEX** (Market Exchange Format), **HDF5** (Hierarchical Data Format)
#### CellRange HDF5
![image](https://github.com/trunghachi/RLearning/assets/45091486/c08ab23f-add5-4023-a7c2-b97bb1410c14)
- filtered_feature_bc_matrix.h5
- raw_feature_bc_matrix.h5
#### MEX (Market Exchange Format)
![image](https://github.com/trunghachi/RLearning/assets/45091486/7dd17d45-82b4-466a-b0c2-ac49b3eeb017)
- filtered_feature_bc_matrix
- raw_feature_bc_matrix

* **FASTA file** - File containing the full genome sequence for the reference of interest
```
>gene1
ATGCGTACGTAGCTAG
>gene2
GCTAGCTAGCATCGAT
```
* **FASTQ** - một định dạng tệp được sử dụng rộng rãi trong phân tích dữ liệu giải trình tự (sequencing), đặc biệt là trong các công nghệ như **Illumina, PacBio, Oxford Nanopore**.
```
@SEQ_ID
ATGCAGCTAG
+
IIIIIIIIII
```
* **GTF file** (Gene Transfer Format) - File containing the gene/transcript models for the reference of interest. Used to genome annotation, gtf file stores position, feature (exon) and meta-feature (transcript/gene) information.
```
chr1    HAVANA  gene    11869   14409   .   +   .   gene_id "ENSG00000223972"; gene_name "DDX11L1";
chr1    HAVANA  exon    11869   12227   .   +   .   gene_id "ENSG00000223972"; gene_name "DDX11L1";
```
* **SAM** file (Sequence Alignment Map) - lưu trữ thông tin về sự liên kết giữa các reads và trình tự tham chiếu
```
@SQ SN:chr1 LN:248956422
read1   0   chr1    100  60   50M  *   0   0   AGCTTAGCTAGCTACCTATATCTTGGTCTTGGCCG  *
```
* **BAM** file - alignments for all barcodes against the reference, là dạng nén của  sam

# single-cell RNA-seq analysis
## 1. Seurat and Bioconductor
![image](https://github.com/trunghachi/RLearning//assets/45091486/de9ce624-d4ac-4032-9332-fdf9de4e106c)
![image](https://github.com/trunghachi/RLearning/assets/45091486/912207ad-c1d0-4852-ad13-259348be684d)

The **Seurat object** is a hierarchical data **container**. When created from scratch, a Seurat object contains information in **slots**

**@ meta.data** : data frame ; contains metadata qualifiers for barcodes/cells
* @ assays : a list of containers for count data (assays), the default one named :
 * **💲** RNA : container of :
    * data matrices (feature **x** barcode) :
      * **@ counts** : contains raw counts (filled by default)
      * **@ data** : contains normalized counts (filled with raw counts by default !)
      * **@ scale.data** : contains scaled counts (empty by default)
    * **meta.features** : data.frame ; contains metadata qualifiers for features
    * **var.features** : vector ; contains the name of a selection of features (based on their high expression variability) 
 * **💲**...
* ** : a list of containers for dimension reduction spaces (PCA, etc). By example : 
 💲 pca (component x barcode)
 💲...
* **@ project.name** : character that defines the project name
* **@ commands** : a freeze of the different steps the object underwent, and their parameter values
![image](https://github.com/user-attachments/assets/d2a63e08-c69b-44df-9c2a-bed25b7f76ad)

### Gene Expression Matrixs Example:
A gene expression matrix contains numerical values that represent the expression levels of genes across different samples or conditions. Here's a breakdown of what these values mean and how they are typically represented:

1. **Rows (Genes):**
   - Each row corresponds to a specific gene. The row may be labeled with a gene identifier, such as a gene symbol (e.g., "TP53") or an Ensembl gene ID (e.g., "ENSG00000141510").

2. **Columns (Samples/Conditions):**
   - Each column corresponds to a sample or condition. Columns may be labeled with sample identifiers or names that indicate the experimental condition, such as "Sample_1" or "Control_1."

3. **Values (Expression Levels):**
   - The values in the matrix represent the expression level of each gene in each sample. These values can be in various forms, depending on how the data has been processed:

   - **Raw Counts:** The raw number of reads or fragments mapped to a gene. This is the initial output from RNA-seq data processing and reflects the abundance of RNA molecules.

   - **Normalized Counts:** Adjusted values that account for differences in sequencing depth and other technical biases. Common normalization methods include:
     - **Counts Per Million (CPM):** The number of reads per million total reads, which normalizes for sequencing depth.
     - **Fragments Per Kilobase of transcript per Million mapped reads (FPKM):** Normalizes for both sequencing depth and gene length.
     - **Transcripts Per Million (TPM):** Similar to FPKM but better suited for comparing expression levels between samples.

   - **Log-Transformed Values:** Logarithmic transformation of normalized counts to stabilize variance and make the data more suitable for statistical analysis.

#### Interpretation of Values:

- **Higher Values:** Indicate higher expression levels of a gene in a particular sample, suggesting that the gene is more active or abundant in that condition.
- **Lower Values:** Indicate lower expression levels, suggesting reduced activity or abundance.
- **Zero or Near-Zero Values:** May indicate that the gene is not expressed or is expressed at very low levels in the sample.

The gene expression matrix is a critical tool for analyzing gene activity, identifying differentially expressed genes, and understanding the molecular basis of phenotypic differences across samples or conditions.


### Original Gene Expression Matrix (Raw Counts)

| Gene ID | Sample_1 | Sample_2 | Sample_3 | Sample_4 |
|---------|----------|----------|----------|----------|
| GeneA   | 150      | 200      | 50       | 75       |
| GeneB   | 500      | 450      | 600      | 550      |
| GeneC   | 0        | 10       | 5        | 0        |
| GeneD   | 300      | 250      | 350      | 300      |

### Step-by-Step Normalization

#### 1. Calculate Geometric Means

For each gene, calculate the geometric mean of counts across all samples, excluding zeros:

- **GeneA:** $$\text{Geometric Mean} = \sqrt{150 \times 200 \times 50 \times 75} \approx 110.67$$
- **GeneB:** $$\text{Geometric Mean} = \sqrt{500 \times 450 \times 600\times 550} \approx 523.61$$
- **GeneC:** Ignore zeros for geometric mean calculation.
- **GeneD:** $$\text{Geometric Mean}=\sqrt{300\times 250\times 350\times 300}\approx 296.98 $$

#### 2. Calculate Size Factors

For each sample, divide each gene's count by the geometric mean of that gene, and compute the median of these ratios.


- **Sample_1 Ratios:**
   * GeneA: $\frac{150}{110.67}\approx 1.36$
   * GeneB: $\frac{500}{523.61}\approx 0.95$
   * GeneD: $\frac{300}{296.98}\approx 1.01$
   * Median: $\text{Median}(1.36, 0.95, 1.01)\approx 1.01$
- **Sample_2 Ratios:**
  - GeneA: $\frac{200}{110.67}\approx 1.81$
  - GeneB: $\frac{450}{523.61}\approx 0.86$
  - GeneD: $\frac{250}{296.98}\approx 0.84$
  - Median: $\text{Median}(1.81, 0.86, 0.84)\approx 0.86$

- **Sample_3 Ratios:**
  - GeneA: $$\frac{50}{110.67} \approx 0.45$$
  - GeneB: $$\frac{600}{523.61} \approx 1.15$$
  - GeneD: $$\frac{350}{296.98} \approx 1.18$$
  - Median: $$\text{Median}(0.45, 1.15, 1.18) \approx 1.15$$

- **Sample_4 Ratios:**
  - GeneA: $$\frac{75}{110.67} \approx 0.68$$
  - GeneB: $$\frac{550}{523.61} \approx 1.05$$
  - GeneD: $$\frac{300}{296.98} \approx 1.01$$
  - Median: $$\text{Median}(0.68, 1.05, 1.01) \approx 1.01$$

#### 3. Normalize Counts

Divide each raw count by its sample's size factor:

| Gene ID | Sample_1 (Norm) | Sample_2 (Norm) | Sample_3 (Norm) | Sample_4 (Norm) |
|---------|-----------------|-----------------|-----------------|-----------------|
| GeneA   | $$\frac{150}{1.01} \approx 148.51$$ | $$\frac{200}{0.86} \approx 232.56$$ | $$\frac{50}{1.15} \approx 43.48$$ | $$\frac{75}{1.01} \approx 74.26$$ |
| GeneB   | $$\frac{500}{1.01} \approx 495.05$$ | $$\frac{450}{0.86} \approx 523.26$$ | $$\frac{600}{1.15} \approx 521.74 $$ | $$\frac{550}{1.01} \approx 544.55$$ |
| GeneC   | $$\frac{0}{1.01} = 0$$ | $$\frac{10}{0.86} \approx 11.63$$ | $$\frac{5}{1.15} \approx 4.35$$ | $$\frac{0}{1.01} = 0$$ |
| GeneD   | $$\frac{300}{1.01} \approx 297.03$$ | $$\frac{250}{0.86} \approx 290.70$$ | $$\frac{350}{1.15} \approx 304.35$$ | $$\frac{300}{1.01} \approx 297.03$$ |

### Log-Transformed Values

To log-transform the normalized counts, add a pseudocount (e.g., 1) to each normalized count and then apply the log2 transformation:

| Gene ID | Sample_1 (Log2) | Sample_2 (Log2) | Sample_3 (Log2) | Sample_4 (Log2) |
|---------|-----------------|-----------------|-----------------|-----------------|
| GeneA   | $$\log_2(148.51 + 1) \approx 7.23$$ | $$\log_2(232.56 + 1) \approx 7.87$$ | $$\log_2(43.48 + 1) \approx 5.46$$ | $$\log_2(74.26 + 1) \approx 6.23$$ |
| GeneB   | $$\log_2(495.05 + 1) \approx 8.96$$ | $$\log_2(523.26 + 1) \approx 9.03$$ | $$\log_2(521.74 + 1) \approx 9.03$$ | $$\log_2(544.55 + 1) \approx 9.10$$ |
| GeneC   | $$\log_2(0 + 1) = 0$$ | $$\log_2(11.63 + 1) \approx 3.64$$ | $$\log_2(4.35 + 1) \approx 2.39$$ | $$\log_2(0 + 1) = 0$$ |
| GeneD   | $$\log_2(297.03 + 1) \approx 8.21$$ | $$\log_2(290.70 + 1) \approx 8.19$$ | $$\log_2(304.35 + 1) \approx 8.26$$ | $$\log_2(297.03 + 1) \approx 8.21$$ |

This process provides normalized and log-transformed values suitable for downstream analysis, such as differential expression analysis.



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

---
# Spatial Transcriptomic [Methods](https://www.mdpi.com/2073-4409/12/16/2042)
---
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

---
# Fluorescence In-Situ Hybridization (FISH)
---
Single-molecule FISH (Fluorescent In-Situ Hybridization) là một kỹ thuật quan trọng để hình dung và phân tích sự biểu hiện gene ở mức độ từng phân tử trong các tế bào hoặc mô. Nó sử dụng các đầu dò huỳnh quang liên kết với các trình tự RNA hoặc DNA cụ thể, cho phép xác định vị trí và số lượng của các phân tử này trong mẫu. Các biến thể của kỹ thuật này, như SeqFISH, SeqFISH+, và MERFISH, cải thiện độ phân giải không gian và khả năng đa dạng mục tiêu, giúp phân tích hàng trăm hoặc hàng nghìn gene cùng lúc. Dưới đây là mô tả các phương pháp phổ biến:

### 1. **SeqFISH (Sequential Fluorescence In-Situ Hybridization)**
   - **Nguyên lý**: SeqFISH sử dụng một chuỗi các bước hybrid hóa lặp lại để nhận diện nhiều gene trong cùng một mẫu. Trong mỗi vòng lặp, một bộ đầu dò huỳnh quang liên kết với một tập hợp con của các trình tự RNA đích. Các đầu dò sau đó được rửa sạch và chu kỳ hybrid hóa khác bắt đầu, sử dụng một bộ đầu dò mới.
   - **Ứng dụng**: SeqFISH cho phép nhận diện đồng thời hàng trăm đến hàng nghìn gene trong các mẫu đơn lẻ, giúp phân tích không gian biểu hiện gene và kiến trúc không gian của tế bào.

### 2. **SeqFISH+**
   - **Cải tiến từ SeqFISH**: SeqFISH+ là một phiên bản nâng cao của SeqFISH, với cải tiến về độ chính xác và số lượng gene có thể được phát hiện đồng thời. Nó sử dụng các chiến lược gắn nhãn phức tạp và thuật toán giải mã để nhận diện các gene mục tiêu với độ nhạy cao hơn.
   - **Đặc điểm nổi bật**: SeqFISH+ cho phép mã hóa hàng nghìn gene bằng cách sử dụng các vòng hybrid hóa được tối ưu hóa để tăng hiệu quả liên kết đầu dò và giảm nhiễu nền.
   - **Ứng dụng**: Đặc biệt hữu ích trong nghiên cứu sinh học tế bào và sinh học phát triển, nơi việc theo dõi sự thay đổi biểu hiện gene ở nhiều gene là rất quan trọng.

### 3. **MERFISH (Multiplexed Error-Robust Fluorescence In-Situ Hybridization)**
   - **Nguyên lý**: MERFISH sử dụng mã hóa nhị phân cho các gene mục tiêu, với các chuỗi đầu dò được thiết kế để gắn vào các phân tử RNA theo cách mã hóa lỗi chịu lỗi (error-robust). Điều này giúp nhận diện nhiều gene mà không bị nhiễu tín hiệu.
   - **Phương pháp giải mã**: Mỗi phân tử RNA được mã hóa bằng một tập hợp các lần bật/tắt tín hiệu huỳnh quang trong một loạt các chu kỳ, cho phép xác định các gene mục tiêu ngay cả khi có nhiễu hoặc mất tín hiệu.
   - **Ứng dụng**: MERFISH có thể xác định hàng nghìn gene trong các tế bào riêng lẻ, được sử dụng rộng rãi trong nghiên cứu biểu hiện gene và phân tích không gian của các hệ thống sinh học phức tạp, như mô não.

### 4. **smFISH (Single-Molecule FISH)**
   - **Nguyên lý**: Đây là phương pháp cơ bản của single-molecule FISH, sử dụng các đầu dò huỳnh quang để phát hiện RNA cụ thể với độ chính xác cao ở mức từng phân tử.
   - **Đặc điểm**: Mỗi phân tử RNA đích được gắn một số lượng lớn đầu dò để tạo ra tín hiệu huỳnh quang mạnh, giúp dễ dàng đếm số lượng phân tử.
   - **Ứng dụng**: smFISH được sử dụng để nghiên cứu sự phân bố RNA và động học phiên mã ở mức độ phân tử trong các tế bào đơn lẻ.

### 5. **Other Variations and Techniques**
   - **STARmap (Spatially Resolved Transcript Amplicon Readout Mapping)**: Sử dụng kỹ thuật mã hóa không gian và giải mã amplicon để phân tích biểu hiện gene không gian mà không cần lặp lại các chu kỳ huỳnh quang.
   - **osmFISH (Oligonucleotide-Sequential Multiplexed FISH)**: Giảm nhiễu và tăng số lượng gene có thể phân tích bằng cách sử dụng các đầu dò oligonucleotide kết hợp với các bước tuần tự hybrid hóa.

### 6. **Các yếu tố quan trọng trong các phương pháp Single-molecule FISH**
   - **Độ phân giải không gian và độ nhạy**: SeqFISH+ và MERFISH cải tiến độ phân giải và độ nhạy so với smFISH, cho phép nhận diện các thay đổi trong biểu hiện gene ngay cả ở mức độ phân tử thấp.
   - **Chiến lược mã hóa và giải mã**: Phương pháp mã hóa nhị phân của MERFISH giúp tăng độ chính xác khi giải mã hàng nghìn gene mục tiêu.
   - **Khả năng mở rộng**: Những phương pháp tiên tiến như SeqFISH+ và MERFISH có khả năng phát hiện đồng thời hàng nghìn gene, trong khi smFISH thường giới hạn ở một số lượng gene nhỏ hơn.

Những kỹ thuật này cung cấp những công cụ mạnh mẽ để phân tích không gian biểu hiện gene ở mức phân tử và hiểu rõ hơn về chức năng tế bào trong các hệ thống sinh học phức tạp.
