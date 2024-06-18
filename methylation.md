# Human variation workflow
A human variation workflow refers to the systematic process of analyzing genetic variations in humans. This workflow typically involves several key steps:
1. **Data acquisition**:
* **DNA samples**: This is the starting point. DNA is extracted from human blood, saliva, or other tissues.
* **Reference genome**: A reference human genome sequence is used as a baseline for comparison.
2. **Data preparation**:
* **Sequencing**: The DNA samples are sequenced using high-throughput DNA sequencing technologies like **Illumina** or **Nanopore**. This generates raw sequencing data.
* **Alignment**: The raw sequencing reads are aligned to the reference genome. This process identifies where the reads map on the reference sequence.
* **Quality control (QC)**: The aligned reads are checked for quality issues like sequencing errors or adapter contamination. Low-quality reads are often filtered out.
3. **Variant calling**: This step identifies genetic variations between the sequenced sample and the reference genome. These variations can include:
* **Single nucleotide polymorphisms (SNPs)**: Changes in a single DNA base pair.
* **Insertions/Deletions (Indels)**: Insertion or deletion of a short DNA sequence.
* **Copy number variations (CNVs)**: Gains or losses of larger DNA segments.
* **Structural variations (SVs)**: Larger rearrangements in the genome, such as inversions or translocations.
4. **Variant annotation**: The identified variants are annotated with additional information to understand their potential functional impact. This may include:
* **Gene location**: Whether the variant falls within a known gene.
* **Predicted effect on protein function**: How the variant might affect the protein coded by the gene.
* **Frequency in the population**: How common the variant is in the general population.
5. **Downstream analysis**: Depending on the research question, further analysis may be performed:
* **Association studies**: Linking identified variants to specific diseases or traits.
* **Functional studies**: Investigating the biological effects of specific variants.
* **Population genetics**: Understanding the distribution and evolution of genetic variations in human populations.

## [Nanopore EPI2ME workflows](https://labs.epi2me.io/workflows/wf-human-variation/#miscellaneous-options)
1. [Remora, MinKNOW](https://github.com/nanoporetech/remora): For **gold-standard 5mC methylation calling** in the human genome, we recommend the algorithm Remora, which is integrated into MinKNOW — the software onboard nanopore sequencing devices.
2. [Clair3](https://github.com/HKU-BAL/Clair3):
* _clair3_SNP.vcf_: Variant Call Format (VCF) files contains information about SNPs identified by the Clair3 variant caller in the Nanopore data. Each line represents a potential **SNP** location, its reference and alternative alleles, and quality scores. ('/QRISdata/Q3570/Data/sequencing_data/NanoPore/old_analysis')
* Clair3 appears to be the best tool for calling SNP/Indels from NanoPore data (more detail at: https://www.biorxiv.org/content/10.1101/2024.03.15.585313v1.full.pdf) 
4. [CuteSV](https://github.com/tjiangHIT/cuteSV): https://link.springer.com/protocol/10.1007/978-1-0716-2293-3_9
* _cuteSV.vcf_: This file contains information about structural variants (SVs) like insertions, deletions, inversions, and translocations identified by cuteSV in the Nanopore data. Each line represents a potential **SV** location, its type, and other relevant details.

## [Pacbio Whole Genome Sequencing Workflow](https://github.com/PacificBiosciences/HiFI-human-WGS-WDL)
PacBio WGS Variant Pipeline performs read alignment, variant calling, and phasing. Joint-calling of small variants and structural variants for cohorts and optional variant filtering and annotation is also available for HiFi human WGS. The workflow can run using **Azure, AWS, GCP, and HPC backends**."
1. [ccsmeth](https://github.com/PengNi/ccsmeth): Detecting DNA methylation from PacBio CCS reads
2.  resource and a reference bundle for WGS: https://pbsharing.blob.core.windows.net/resources/reference.tar; https://pbsharing.blob.core.windows.net/resources/resources.tar;
3.  [Sniffles2](https://www.biorxiv.org/content/10.1101/2022.04.04.487055v1.full)
4.  Hifiasm
5.  [primrose](https://github.com/mattoslmp/primrose): Primrose predicts 5-Methylcytosine (5mC) of each CpG in PacBio HiFi reads, using a Convolutional Neural Network. Methylation is assumed to be symmetric between strands. The output is reported in the forward direction with respect to the HiFi read sequence.
6.  [PacBio Secondary Analysis](https://github.com/PacificBiosciences/pbbioconda) Tools on Bioconda
7.  [SMRT Link](https://www.pacb.com/support/software-downloads/): Single-Molecule Real-Time Sequencing, SMRT sequencing can read much longer stretches, often exceeding 30,000 bases in a single read. This provides a more comprehensive view of the entire DNA sequence.
8.  Extracting CpG methylation from PacBio HiFi whole genome sequencing: https://www.pacb.com/wp-content/uploads/AGBT-2022-extracting-CpG-methylation-Portik-poster.pdf
9. [Modbamtools](https://rrazaghi.github.io/modbamtools/) modbamtools is a set of tools to manipulate and visualize DNA/RNA base modification data that are stored in bam format
10.  **HiFi, Duplex, and ultra-long ONT (ULONT)**: Pacbio
* **HiFi (High Fidelity)**: This refers to a specific sequencing chemistry used in PacBio's Sequel II/SMRT sequencing systems to generate highly accurate long reads of DNA. HiFi reads offer significantly improved accuracy compared to earlier PacBio chemistries.
* **Duplex Reads**: This is a strategy used in conjunction with HiFi sequencing to further enhance accuracy. It involves generating two consensus reads from each DNA molecule, leveraging the information from both strands for more reliable base calling.
* **Ultra-long ONT (ULONT) Reads**: ONT (Oxford Nanopore Technologies): This is another company developing long-read DNA sequencing technologies. ONT sequencers use a different approach compared to PacBio. ULONT refers to reads generated by ONT sequencers that are exceptionally long, potentially exceeding even HiFi reads in length.


## Where are the data:
1. Our:
```
QRISdata/Q3570/Data/sequencing_data/NanoPore
/QRISdata/Q3570/Data/sequencing_data/NGUY-0032_PacBio/
```
2. Example datasets: https://www.pacb.com/connect/datasets/

## Cấu trúc cơ bản của một số định dạng dữ liệu:
### 1. .fasta files
```
">gi|12345678|gb|AC123456.1| Homo sapiens chromosome 1, GRCh38.p13 Primary Assembly
ACGTACGTACGTACGTACGTACGTACGTACGTACGTACGTACGTACGTACGT
>gi|12345679|gb|AC123457.1| Homo sapiens chromosome 2, GRCh38.p13 Primary Assembly
ATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGATCGAT"
```
"Tập tin FASTA (FASTA file) là định dạng văn bản được sử dụng để lưu trữ trình tự DNA, RNA hoặc protein. Tên gọi FASTA bắt nguồn từ ""FAST All"", một chương trình được sử dụng để so sánh trình tự DNA.

1. Dòng đầu tiên: Bắt đầu bằng dấu "">"" (ký hiệu greater than) và tiếp theo là tên trình tự. Tên này có thể bao gồm thông tin về nguồn gốc, chức năng hoặc các đặc điểm khác của trình tự.
2. Dòng tiếp theo: Chứa trình tự DNA, RNA hoặc protein. Các ký tự được sử dụng để biểu diễn các axit amin hoặc base nitơ.
3. Dòng tiếp theo: Có thể có thêm dòng comment (bắt đầu bằng dấu #) để cung cấp thông tin bổ sung về trình tự.
4. Kết thúc: Tập tin FASTA có thể chứa nhiều trình tự, mỗi trình tự được phân tách bởi dòng đầu tiên với tên mới.

### 2. raw .fastq files
```
@661c877d-cfda-487e-8b31-8d8266ff5623 runid=452d67d8b1ec1afdd73c02966d09c4c42c8f4dae read=111 ch=1579 start$
ATTACCTGTTACTCGTTCAGTTACGTATTGCTACCCAACAGCAATGAAAACATGTCCACACAAAAACCTGTACACAAGTGATTCACAGCAGCCTTATCCATCACAGC$
+
'(*(()*0/0)))))667666?@;877;>=><<<@@>?@BCCCDD<6888,,/AB@<=>E{GFCJPGA@?E;9=AAB>@??GGFFFDCCDBBA?B@A@<<<?A?:;2$
```
"FASTQ files (.fastq) là một định dạng tập tin văn bản được sử dụng để lưu trữ trình tự DNA hoặc RNA thô được tạo ra bởi các máy giải trình tự DNA thế hệ mới (NGS). So với FASTA files chỉ chứa trình tự, FASTQ files cung cấp thông tin bổ sung về chất lượng của mỗi base gọi (base call) trong trình tự. Mỗi đọc (read) trong FASTQ file được biểu diễn bằng bốn dòng:

1. Dòng header (tiêu đề): Bắt đầu bằng ký tự ""@"" (@), tiếp theo là một chuỗi ký tự nhận dạng duy nhất cho đọc (read ID). Thường chứa thông tin về nguồn, máy giải trình tự, và vị trí của đọc trên chip dòng chảy (flowcell).
2. Dòng trình tự: Chứa trình tự nucleotide của đọc (thường là DNA hoặc RNA). Các ký tự A, C, G, T (U) được sử dụng để đại diện cho các base nitơ.
3. Dòng dấu ""+"" (plus): Dòng này thường là dấu ""+"" (plus) và không chứa thông tin hữu ích.
4. Dòng chất lượng: Chứa các ký tự mã hóa chất lượng (quality scores) cho mỗi base tương ứng với dòng trình tự ở trên. Ký tự thường được sử dụng là Phred score (+33) hoặc Sanger score (+40). Giá trị chất lượng cao hơn biểu thị khả năng đọc base đó chính xác cao hơn.

### 3. .mmi files (minimap index files) from FASTA files
"Minimap is a popular tool used for aligning DNA or RNA sequences. To improve search speed, it creates index files in the .mmi format from reference sequences stored in FASTA files (.fasta). These .mmi files don't contain the actual sequences themselves, but rather a compressed representation to facilitate rapid searching during alignment.
The specific details of the internal structure of .mmi files are not publicly documented by the minimap developers.

### 4. .bam files
5mC BAM files: These files store the aligned reads from PacBio sequencing after methylation calling. They likely contain information about which regions of the genome are methylated with 5mC.
Unlike human-readable FASTA files, BAM files are stored in a binary format for compactness and faster processing by computers.
AM files (Binary Alignment Map) are the workhorses for storing alignments between DNA/RNA reads (short sequences) and a reference genome (a complete DNA sequence). They offer a compact and efficient way to represent this vital information for bioinformatics analyses.
Two Main Parts: BAM files consist of two key components:
1. **Header**: This section contains crucial information about the alignment process and the data itself. It includes details like:
* Reference genome information (name, length, etc.)
* Read group information (source of the reads)
* Alignment parameters used (software, settings)
* Dictionary for any custom tags used in the alignment
2. **Alignment Blocks**: This section stores the actual alignment data for each read against the reference genome. Each block (alignment) has details like:
- Query Name: The unique identifier for the read being aligned.
- Flags: Bitwise flags indicating properties of the alignment (e.g., mapped, unmapped, reverse strand).
- Reference ID & Position: The chromosome (or contig) and starting position in the reference genome where the read aligns.
- Mapping Quality (MAPQ): A score indicating the confidence of the alignment.
- CIGAR String: A compact string representing how well the read aligns to the reference (insertions, deletions, mismatches).
- Mate Information (optional): Details about the paired-end read (if applicable).
- Optional Tags: Additional information specific to the aligner software used (e.g., intron information).
  
**BAM Tags (C+m)**: These tags within the BAM file likely indicate the number of reads supporting cytosine (C) and methylated cytosine (m) at each position. You can use tools like samtools view or pysam to extract and analyze these tags. Plotting these values across the genome can reveal methylation patterns.

### 5. .pbmm2 files
.pbmm2 files likely play a role in the workflow using minimap2, a popular tool for aligning DNA or RNA sequences. Minimap2 is often used to align PacBio sequencing reads to a reference genome.

Possible Content: While the exact structure is not documented, we can make some educated guesses based on typical alignment file formats:

**Alignment data**: The file might contain information about how PacBio sequencing reads align to the reference genome. This could include details like:
- Start and end positions of the alignment for each read.
- Mismatches between the read and the reference.
- Insertions and deletions (gaps) in the alignment.
**Additional information**: The file might also hold metadata related to the alignment process, such as:
- Parameters used with minimap2.
- Information about the reference genome.
- Statistics about the alignment results.

## Methylation Analysis pipeline
1. **Sequencing**: PacBio sequencing offers the advantage of generating long reads, which can span regions with repetitive elements and complex structures. This is important for methylation analysis as it allows for more accurate base calling and detection of methylation patterns across these regions.  PacBio sequencers can even directly detect 5-methylcytosine (5mC) modifications during sequencing without requiring additional library preparation steps (unlike bisulfite sequencing).
2. **Alignment**: The long PacBio reads are aligned to a reference genome. This can be done using tools like pbmm2, which is a PacBio-compatible wrapper for minimap2, a popular alignment tool. The alignment process determines how well the reads match the reference genome and identifies any mismatches or insertions/deletions.
3. **Methylation Calling**: Here's where PacBio's ability to detect 5mC directly comes into play. Tools like pb-CpG-tools analyze the aligned reads and calculate the methylation probability for each CpG site (cytosine-guanine dinucleotide) in the genome. This provides a quantitative measure of methylation levels at specific locations.
4. **Data Analysis**: The methylation data is then analyzed to identify differentially methylated regions (DMRs). DMRs are areas in the genome where the methylation levels differ between samples or groups. These differences can be associated with various biological processes, such as gene expression regulation, development, and disease.
- **Small variant calling**: This identifies single nucleotide polymorphisms (SNPs) and other small insertions and deletions in the DNA. It uses Clair3, a tool specifically designed for calling variants from long-read sequencing data.
- **Structural variant calling (SV)**: This detects larger changes in the genome, such as insertions, deletions, inversions, and translocations.
- **Copy number variation (CNV) analysis**: This identifies regions of the genome that have been duplicated or deleted. (Note that the dedicated wf-cnv workflow is deprecated, but its functionality is included here).
- **Short tandem repeat (STR) expansion genotyping**: This identifies expansions in repetitive DNA sequences (typically 2-6 base pairs long, that are repeated in tandem one after another, for example, CACAACACAACACA), which can be associated with genetic diseases.

```
1. Sequencing: dataset on HPC
2. Alignment: 
    1) pbmm2 align -t 8 ref.fasta reads.fastq > aligned_reads.sam
    2) samtools view -bS aligned_reads.sam > aligned_reads.bam
    3) samtools sort aligned_reads.bam sorted_aligned_reads
        samtools index sorted_aligned_reads.bam
3. Methylation Calling: 
    pb-cpg-methylation sorted_aligned_reads.bam ref.fasta output_prefix
   # This will generate multiple files with methylation information, including:
   #   - output_prefix.cpg_report.txt: Summary report
   #   - output_prefix.cpg_ methylation_levels.bed: Methylation levels at CpG sites
4. Data Analysis:
* Visualization: Tools like UCSC Genome Browser ([https://genome.ucsc.edu/]) or Integrative Genomics Viewer (IGV) allow you to visualize methylation levels across the genome.
* Statistical Analysis: Packages like DiffBind ([https://bioconductor.org/packages/release/bioc/html/DiffBind.html]) or MethylKit offer functionalities specifically designed for methylation data analysis.
* Identifying Differentially Methylated Regions (DMRs): MethylSeekR ([https://bioconductor.org/packages/release/bioc/html/MethylSeekR.html]) or DSS ([https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3189540/])
* Functional Annotation of DMRs: GREAT or ChIPseeker ([https://bioconductor.org/packages/release/bioc/html/ChIPseeker.html])
* Integration with Other Data Sources.

### first I used f5c to index, command as below:
/pathtof5c/f5c-v1.3/f5c_x86_64_linux_cuda index -d /pathtorawfast5file/Run1 -d /pathtorawfast5file/Run2 /pathtofastqfile/Human0007_SUP_recall.fastq
### then, call methylation - remember to note that we used R10 flow cell
/pathtof5c/f5c-v1.3/f5c_x86_64_linux_cuda call-methylation -t 48 -r /pathtofastqfile/Human0007_SUP_recall.fastq -b /pathtobamfile/Human0007_SUP_recall.sorted.bam -g /pathtoreference/ GCF_000001405.40_GRCh38.p14_genomic.fna  --pore r10 -K 4000 -B 9.2M --iop 400 > Human0007_SUP_200bp_meth_r10.tsv
#### then, calculate the methylation frequencies
/pathtof5c/f5c-v1.3/f5c_x86_64_linux_cuda meth-freq -i  /pathtomethylationcallfile/Human0007_SUP_200bp_meth_r10.tsv > Human0007_SUP_r10_freq.tsv
```
```
I have finished running Nanopore best practice for sample VN0007 from EPI2ME including wf-basecalling for DNA modified basecalling and wf-human-variation for SNV, SV and CNV calling, modified base calling, and STR.
The code for workflow is stored here:
/scratch/project/stseq/Tien/test_scripts/run_basecalling.sh (run_human_variation.sh)
The results are in: /QRISdata/Q3570/Data/sequencing_data/NanoPore/raw_data/Human_0007_9Jan2023/20230109_1055_1G_PAG73001_61a0f010/human_variation_output
Results include information below:
Reports: Alignment, SNPs, SV, CNV and STR
Phased and clinvar annotated VCF files: SNP and SV
VCF files: CNV and STR
BEDmethyl file: Phased and ungrouped DNA modification counts for sample
```
