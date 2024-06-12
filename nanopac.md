# 1. Công nghệ [Pacbio](https://www.pacb.com/)
## Bisulfite sequencing:
Tranditional methods. This is the current gold standard technique for detecting 5mC. However, it has limitations like requiring a lot of data and having a longer analysis time.

## Nanopore sequensing:
A technique that sequences DNA or RNA by passing the nucleic acids through a tiny pore and measuring changes in electrical current. This method allows for the direct sequencing of long strands of DNA or RNA. This is a newer method for DNA sequencing that seems to be promising for 5mC detection.

## MAS-seq method:
**MAS-Seq**, or Multiplexed Arrays Sequencing, is a method used in scRNA-seq to obtain full-length transcript information for each cell. This is important because traditional short-read RNA sequencing only captures the ends of transcripts, which can miss important information about how genes are spliced. MAS-Seq uses a process called concatenation to link together multiple cDNA molecules into longer fragments. These longer fragments can then be sequenced on PacBio sequencers, which can read much longer stretches of DNA than traditional sequencing machines.
Here's a simplified breakdown of the MAS-Seq method:

1. **Single-cell cDNA generation**:  This is typically done using a commercially available system like the 10x Chromium.
2. **TSO PCR and artifact removal**:  TSO (template-switching oligos) are used to add adapters to the cDNA molecules. These adapters are then used to amplify the cDNA molecules and remove any unwanted artifacts.
3. **MAS PCR and array formation**:  The cDNA molecules are concatenated into ordered arrays.
4. **Adapter ligation and enrichment**: Adapters are ligated to the ends of the MAS arrays, and then only full-length arrays are enriched for sequencing.
5. **Sequencing on PacBio sequencers**:  The enriched MAS arrays are sequenced on PacBio sequencers, which can read long stretches of DNA.
6. **Data analysis**:  The sequencing data is then analyzed to identify and quantify the different transcript isoforms that were present in each cell.

MAS-Seq has several **advantages** over traditional short-read RNA sequencing for single-cell studies. First, MAS-Seq can provide full-length transcript information, which can be important for understanding how genes are regulated. Second, MAS-Seq can be more sensitive than short-read RNA sequencing, which means that it can detect transcripts that are expressed at low levels. Finally, MAS-Seq can be used to identify novel transcript isoforms.

However, MAS-Seq also has some **limitations**. First, it is a more complex and expensive method than short-read RNA sequencing. Second, the data analysis can be more challenging.

Overall, MAS-Seq is a powerful new tool for single-cell RNA sequencing. It can provide researchers with a more complete understanding of how genes are expressed in individual cells.
# 2. Công nghệ Nanopore
## Reduced-representation bisulfite sequencing (RRBS)
Tranditional method.
## Reduced-Representation Methylation Sequencing (RRMS) with Oxford Nanopore
* More accurate identification of 5mC compared to bisulfite sequencing.
* Requires less sequencing data to achieve similar accuracy.
* Provides more even coverage across the genome, meaning all regions are analyzed more consistently.
* Significantly faster analysis time.
* More even genomic coverage with lower GC bias
* Higher number of CpG positions called at lower read depth
* Simplified haplotype phasing of methylated bases using long reads
* Greater experimental reproducibility

# 3. Một số khái niệm sinh học
* **demographic, anthropometric, biochemical, and clinical traits**:  đặc điểm dân số, đặc điểm hình thể, sinh hóa, và đặc điểm lâm sàng
* **Single-nucleotide resolution**:  The ability to detect changes at the level of individual nucleotides, which are the basic building blocks of DNA and RNA.
* **Basecalling algorithms**: Computational methods used to interpret the raw data from sequencing machines and translate it into the sequence of bases. These algorithms are essential for turning the electrical signals from nanopore sequencing into readable DNA or RNA sequences.
* **Epigenetic modifications**: Heritable changes in gene function that do not involve alterations in the DNA sequence. These can include *DNA methylation*, *histone modification*, and *RNA-associated* silencing (bất hoạt RNA)
* **DNA and RNA base modifications**: Chemical alterations to the standard bases (adenine, thymine, cytosine, guanine, and uracil) in the genetic material. These modifications can affect gene expression and are involved in various biological processes
* **5mC (5-methylcytosine)**: A modified form of the DNA base cytosine, where **a methyl group is added**. It’s often involved in gene regulation and is a common epigenetic marker. 5-methyl cytosine (5mC) most frequently occurs in mammalian cells in CpG dinucleotides and can alter gene expression by suppressing transcription.
* **5hmC (5-hydroxymethylcytosine)**: A further modification of 5mC, where **a hydroxymethyl group is added**. It’s thought to be an intermediate step in the process of DNA _demethylation_.
* **m6A (N6-methyladenosine)**: A common modification in RNA, particularly mRNA, where _a methyl group is added to the adenine base_. It plays a role in the regulation of mRNA stability and translation
* **BrdU (Bromodeoxyuridine)**: A synthetic nucleoside that can be incorporated into DNA during _replication_. It’s commonly used as a _marker_ to study _cell proliferation_ (tăng sinh).
* **CpG dinucleotides**: These are short DNA sequences where a cytosine (C) is followed by a guanine (G). 5mC modifications most commonly occur at these sites in humans.
* **GC bias (guanine-cytosine)**: the non-random distribution of guanine (G) and cytosine (C) nucleotides in a DNA sequence. Một số kỹ thuật có thể gặp khó khăn hơn trong việc đọc các vùng DNA nghèo GC, dẫn đến việc đánh giá thấp mức độ methylation trong những vùng này.
* **repetitive regions**: Repetitive regions in DNA are sequences that are repeated multiple times throughout the genome. Chúng chiếm một phần đáng kể bộ gen người. These regions can be classified based on the size and nature of the repeats: **Tandem Repeats** (_Satellite DNA_ - They are often found in centromeric and pericentromeric regions of chromosomes; _Alpha Satellite_: Found near the centromeres of human chromosomes; _Minisatellites_ - 10-60 base pairs in length; _Microsatellites_: 2-10 base pairs in length. They are highly polymorphic and widely used in genetic studies and forensic analysis). **Interspersed Repeats** (_DNA Transposons_: Move directly from one location to another through a "cut and paste" mechanism. _Retrotransposons_)
* **Retrotransposons**: Move by being transcribed into RNA and then back into DNA before being inserted at a new location. They can be further divided into:
  * _Long Interspersed Nuclear Elements (LINEs)_: Autonomous elements capable of self-transposition. LINE-1 (L1) is a common example in the human genome.
  * _Short Interspersed Nuclear Elements (SINEs)_: Non-autonomous elements that rely on LINEs for transposition. Alu elements are a common example in humans.
  * _Long Terminal Repeat (LTR) Retrotransposons_: Contain LTR sequences at both ends. They are similar to retroviruses but lack the ability to form infectious particles.
* **Satellite Chromosomes**: These are chromosomes with a small, secondary constriction on one arm. This constriction is attached to the main body of the chromosome by a thin strand of chromatin and often appears like a small satellite orbiting a planet.  These are found in humans on chromosomes 13, 14, 15, 21, and 22, and the Y chromosome in some cases. They don't contain genes themselves but may play a role in chromosome stability and function.
* **Satellite DNA**: This refers to repetitive, non-coding DNA sequences found in the human genome.  These sequences are thought to be leftover DNA that doesn't code for proteins and may not have a specific function. There are different families of satellite DNA, with Human Satellite 1 (**HSat1**) being the most AT-rich (high Adenine and Thymine content) fraction; **HSat2**: Less AT-rich than HSat1; **HSat3**: The least AT-rich satellite family.  While the function of these sequences is not fully understood, recent research suggests they might play a role in regulating gene expression.
* **HOR array (Higher-Order Repeat array)**:
* ****:
* ****:
* ****:
* ****:
* ****:
* ****:
* ****:
* ****:
* ****:
* ****:
* ****:
* ****:
* ****:
* ****:
  

# 1. Một số khái niệm cơ bản lắp ráp pha (phased assembly): 

1. **Transposon**:
Transposon(còn được gọi là **phần tử di động**) là một chuỗi **ADN** có khả năng tự di chuyển hoặc tự chèn chính nó vào một vị trí mới trong **genome** (genome là tập hợp toàn bộ thông tin di truyền - bao gồm cả DNA, genes, và nhiễm sắc thể, 
trong khi nhiễm sắc thể là các đơn vị cấu tạo của genome chứa các gen cụ thể). Chúng có thể gây ra các hiệu ứng như tạo hoặc đảo ngược đột biến và thay đổi kích thước của genôm.

Có hai loại transposon chính:
   * **Cut-and-Paste Transposons**:
      - Chúng di chuyển bằng cách cắt chuỗi transposon từ một vị trí trong genôm và chèn nó vào một vị trí khác trong genôm.
      - Quá trình này được thực hiện bởi một protein gọi là **transposase**.
      - Ví dụ về loại transposon này là các phần tử **IS** (Insertion Sequences) và **P-elements** trong ngô.
   
   * **Replicative Transposons**:
      - Chúng di chuyển bằng cách sao chép chuỗi transposon và chèn bản sao của nó vào vị trí đích trong genôm.
      - Trong loại transposition này, có một bản sao mới của transposon và cả donor lẫn recipient DNA đều có một chuỗi transposon sau khi di chuyển.
   
* **Transposase**  là một enzyme quan trọng trong quá trình di chuyển của transposon. Nó giúp thực hiện việc cắt và chèn chuỗi transposon vào genome.
  
1. **depth of 20x** : Trong ngữ cảnh của việc giải trình tự gen, “độ sâu tối thiểu 20x” nghĩa là mỗi vị trí trên bộ gen được đọc trung bình 20 lần. Điều này giúp tăng độ tin cậy của việc xác định các nucleotide tại mỗi vị trí và giảm thiểu sai sót. Độ sâu giải trình tự càng cao, khả năng phát hiện biến thể gen càng chính xác
2. **Basecalling**  là quá trình chuyển đổi các tín hiệu điện tử thô thu được từ thiết bị giải trình tự thành chuỗi nucleotide (DNA hoặc RNA). Đây giống như quá trình nhận dạng giọng nói, nơi ngôn ngữ nói được chuyển thành văn bản viết. Trong giải trình tự gen, basecalling là bước quan trọng để từ các tín hiệu điện tử, xác định được trình tự các nucleotide tạo nên DNA hoặc RNA
3. **25–35 kilobase reads** có nghĩa là các đoạn DNA được giải trình tự có chiều dài từ 25.000 đến 35.000 base (cặp nucleotide).


Xem thêm các nội dung khác tại [Heng Li's blog](https://lh3.github.io/)
1. **Contig** - contiguous sequence: dùng để chỉ một đoạn trình tự DNA liên tục được lắp ráp từ các đoạn đọc nhỏ hơn ("reads"). Đây là thành phần quan trọng của lắp ráp de novo. Một contig không chứa các đoạn dài của trình tự không xác định (còn gọi là _khoảng trống lắp ráp - gaps_).
1. **Scaffolds** (đôi khi gọi là _supercontig_): Được tạo ra bằng cách ghép nối các contigs lại với nhau bởi các _gaps có kích thước không chính xác_ (thông tin overlap giữa chúng) hoặc thông tin từ các kỹ thuật bổ sung như _mate-pair sequencing_. Scaffolds cung cấp một ước lượng về cấu trúc và khoảng cách giữa các contigs trong genome.
1. **Assembly**: một tập hợp các contig hoặc scaffold. Một lắp ráp là hoàn chỉnh haploid hoặc đơn giản là hoàn chỉnh nếu nó đại diện cho một bộ gen haploid đầy đủ.
1. **Haplotig**: một contig đến từ cùng một haplotype. Trong một lắp ráp chưa phân pha, một contig có thể kết hợp các alen từ các haplotype khác nhau của bố mẹ trong một bộ gen diploid hoặc polyploid.
1. **Unitig**: là một chuỗi liên tục của các đoạn DNA không bị gián đoạn bởi các khe hoặc lỗ. Nó được tạo ra bằng cách kết hợp các đoạn đọc (reads) từ dữ liệu ngắn hoặc dài thành một chuỗi duy nhất. Unitig thường là một phần của một **contig** hoặc **scaffold** trong quá trình lắp ráp genome.
1. **Haplotigs**: là các contig đại diện cho các biến thể hợp tử (haplotype) trong một bộ gen lưỡng bội. Khi xây dựng các bộ gen từ dữ liệu đọc dài thế hệ thứ ba (third-gen sequencing), việc phân loại các contig theo haplotype có thể gặp khó khăn, đặc biệt khi độ đa dạng di truyền cao đến mức không thể nhận ra sự tương đồng giữa các haplotype trong quá trình lắp ráp. Kết quả là việc lặp lại khu vực thay vì kết hợp thành các biến thể hợp tử, và điều này có thể gây ra vấn đề trong phân tích tiếp theo, ví dụ như phát hiện biến thể hoặc xây dựng lại haplotype từ bộ gen lưỡng bội với các contig hợp tử không ghép cặp.
1. **switch error** - Lỗi chuyển đổi: sự thay đổi từ alen của một bố mẹ sang alen của bố mẹ khác trên một contig (xem hình bên dưới). Thuật ngữ này đã được sử dụng để đo độ chính xác phân pha dựa trên tham chiếu trong hai thập kỷ. Một haplotig được cho là không có lỗi chuyển đổi.
1. **Lỗi yak hamming**: một alen không nằm trên haplotype được hỗ trợ nhiều nhất của một contig (xem hình bên dưới). Mục đích chính của nó là để kiểm tra mức độ gần gũi của một contig với một haplotig. Định nghĩa này khá phức tạp. Thuật ngữ này có lẽ được sử dụng lần đầu tiên bởi Porubsky et al (2017) trong bối cảnh phân pha dựa trên tham chiếu. Tuy nhiên, áp dụng nó cho các contig không phải là dễ dàng. Định nghĩa yak không được chấp nhận rộng rãi. Tỷ lệ lỗi hamming có lẽ ít quan trọng hơn trong thực tế (Richard Durbin, giao tiếp cá nhân).

## Các loại lắp ráp pha.
1. **Collapsed assembly - Lắp ráp nén**: một lắp ráp hoàn chỉnh với các alen của bố mẹ chuyển ngẫu nhiên trong một contig. Hầu hết các trình lắp ráp thông thường tạo ra các lắp ráp bị nén. Một lắp ráp bị nén cũng được gọi là lắp ráp squashed hoặc lắp ráp conensus.
1. **Primary assembly - Lắp ráp chính**: một lắp ráp hoàn chỉnh với các đoạn dài của khối pha. Khái niệm này đã được GRC sử dụng. Các lắp ráp BAC-to-BAC đều có thể được coi là các lắp ráp chính. Falcon-unzip có lẽ là trình đầu tiên tạo ra các lắp ráp như vậy cho dữ liệu whole-genome shotgun.
1. **Alternate assembly - Lắp ráp thay thế**: một lắp ráp không hoàn chỉnh gồm các haplotig trong các vùng dị hợp tử. Một lắp ráp thay thế luôn đi kèm với một lắp ráp chính. Nó không hữu ích một mình vì nó bị phân mảnh và không hoàn chỉnh.
1. **Partially phased assembly - Lắp ráp phân pha một phần**: các bộ lắp ráp hoàn chỉnh với các đoạn dài của khối pha, đại diện cho toàn bộ bộ gen diploid/polyploid.
1. **Haplotype-resolved assembly**: các bộ lắp ráp hoàn chỉnh gồm các haplotig, đại diện cho toàn bộ bộ gen diploid/polyploid. Khái niệm này đã được sử dụng không nhất quán trong các ấn phẩm mà không có định nghĩa rõ ràng.
8. **Telomere-to-telomere assembly**: t2t hay tổng hợp từ telomere đến telomere, là quá trình tạo ra một bản tổng hợp của bộ gen không có khoảng trống, bao gồm toàn bộ các nhiễm sắc thể từ điểm bắt đầu (telomere) đến điểm kết thúc (telomere) của chúng. Trước đây, các bộ gen thường được tổng hợp thành các đoạn có độ dài vài megabase tốt nhất, nhưng nhờ vào tiến bộ công nghệ trong việc đọc trình tự gen dài, ngày nay có thể tổng hợp gần như hoàn chỉnh mỗi nhiễm sắc thể.

   
## Tóm tắt [quy trình](https://a.storyblok.com/f/196663/cd1c1c07ec/human-assembly-workflow.pdf) phân tích gene:
Toàn bộ quy trình phân tích gen người, từ lúc lấy mẫu đến lúc ra kết quả là bộ gen hoàn chỉnh, bao gồm các bước sau và thời gian ước tính cho mỗi bước:

1. **Thu thập mẫu (Sample Collection)**:
   - **Mô tả**: Lấy mẫu DNA từ máu, nước bọt hoặc mô khác.
   - **Công cụ**: 
   - **Thời gian**: Vài phút đến vài giờ, tùy thuộc vào loại mẫu và quy trình thu thập.
  
2. **Chiết xuất DNA (DNA Extraction - obtaining high molecular-weight DNA)**:
   - **Mô tả**: Tách DNA ra khỏi các thành phần khác trong mẫu.
   - **Công cụ**: NEB Monarch HMW DNA Extraction Kit.  QIAGEN Puregene Blood Kit,
   - **Thời gian**: Vài giờ đến một ngày.

3. **Chuẩn bị thư viện (Library Preparation - selecting a kit)**:
   - **Mô tả**: Chuẩn bị các đoạn DNA để giải trình tự, bao gồm các bước như phân mảnh DNA, thêm adapter và đánh dấu.
   - **Công cụ**: Ultra-Long DNA Sequencing Kit, Ligation Sequencing Kit, Short Fragment Eliminator Expansion Kit, Diagenode Megaruptor 3 (for shearing)
   - **Thời gian**: Vài giờ đến một ngày.

4. **Giải trình tự (Sequencing)**:
   - **Mô tả**: Sử dụng các thiết bị như PromethION để đọc các đoạn DNA.
   - **Công cụ**:  Ultra-Long DNA Sequencing KitPromethION, Ligation Sequencing Kit, [Flow Cell Wash Kit](https://store.nanoporetech.com/flow-cell-wash.html) (để rửa sạch, loại bỏ các mẫu sót, duy trì hiệu suất, tái sử dụng, kéo dài tuổi thọ của các  các flow cells).
   - **Thời gian**: Vài giờ đến vài ngày, tùy thuộc vào độ sâu và độ dài đoạn đọc mong muốn.

5. **Lắp ráp de novo (De Novo Assembly)**:
   - **Mô tả**: Sử dụng các công cụ như Flye để lắp ráp các đoạn đọc thô thành các contig.
   - **Công cụ**: [Flye](https://github.com/fenderglass/Flye);  on-board PromethION [compute](https://nanoporetech.com/products/analyse); [Hifiasm](https://github.com/chhylp123/hifiasm); 
   - **Thời gian**: Khoảng hai ngày để lắp ráp và đánh bóng một bộ gen người.

6. **Đánh bóng bổ sung (Additional Polishing)**:
   - **Mô tả**: Thực hiện một vòng đánh bóng bổ sung với Medaka để cải thiện chất lượng contig.
   - **Công cụ**: [Medaka]( https://github.com/nanoporetech/medaka),
   - **Thời gian**: Vài giờ đến một ngày.

7. **Phân tích và diễn giải (Analysis and Interpretation)**:
   - **Mô tả**: Phân tích các contig đã được đánh bóng để xác định các đặc điểm di truyền và biến thể.
   - **Công cụ**: Có rất nhiều công cụ, tuỳ thuộc bài toán, cơ bản có: Công cụ phát hiện biến dị và chèn/xoá (GATK, FreeBayes, SAMTools for SNPs, indels); Công cụ so sánh và chức năng gene (BLAST, BLAT, và Bowtie2); phân tích chủ đề và biểu đồ (R, Python); Cơ sở dữ liệu tham chiếu (GenBank, RefSeq, và ENSEMBL for reference), và tài nguyên phân tích  GO (Gene Ontology) và KEGG (Kyoto Encyclopedia of Genes and Genomes).
   - **Thời gian**: Vài ngày đến vài tuần, tùy thuộc vào mục đích và độ phức tạp của phân tích.

**Tổng thời gian**: Quá trình từ thu thập mẫu đến có được bộ gen hoàn chỉnh mất khoảng 1-2 tuần, tùy thuộc vào điều kiện cụ thể và độ phức tạp của từng bước.


# 1. Nanopore

[Assembling the human genome](https://a.storyblok.com/f/196663/cd1c1c07ec/human-assembly-workflow.pdf) using long [nanopore](https://nanoporetech.com/products/prepare) sequencing reads 

![de novo assembly](https://github.com/trunghachi/RLearning/assets/45091486/df101ee3-5263-407b-a5ee-0f77cf80585a)

## Công cụ
To assemble a human genome, we recommend the third-party de novo assembly tool [Flye](https://github.com/fenderglass/Flye). This analysis package represents a complete pipeline, taking raw nanopore reads as input, and producing polished contigs as output. We also advise one round of additional polishing of the assembly with [Medeka](https://github.com/nanoporetech/medaka).

# 2. Pacbio

![image](https://github.com/trunghachi/RLearning/assets/45091486/1eea46d0-ecc9-4878-b694-2aac1729276b)

| Type                          | Name                     | Description                                                                                         | Notes                                      |
|-------------------------------|--------------------------|-----------------------------------------------------------------------------------------------------|--------------------------------------------|
| Array[Array[File]?]           | zipped_assembly_fastas   | De novo dual assembly generated by hifiasm                                                          |                                            |
| Array[Array[File]?]           | assembly_noseq_gfas      | Assembly graphs in GFA format.                                                                      |                                            |
| Array[Array[File]?]           | assembly_lowQ_beds       | Coordinates of low quality regions in BED format.                                                   |                                            |
| Array[Array[File]?]           | assembly_stats           | Assembly size and NG50 stats generated by [calN50](https://github.com/lh3/calN50).                                                   |                                            |
| Array[Array[IndexData?]]      | asm_bam                  | minimap2 alignment of assembly to reference.                                                        |                                            |
| Array[Array[IndexData?]]      | paftools_vcf             | Calls variants from coordinate-sorted assembly-to-reference alignment. It calls variants from the cs tag and identifies confident/callable regions as those covered by exactly one contig [paftools](https://github.com/lh3/minimap2/blob/master/misc/README.md#calling-variants-from-haploid-assemblies) |                                            |
| Array[Array[File?]]           | paftools_vcf_stats       | [bcftools](https://samtools.github.io/bcftools/bcftools.html#stats) stats summary statistics for paftools variant calls                                        |                                            |


| Image         | Major tool versions                                                        | 
|---------------|----------------------------------------------------------------------------|
| align_hifiasm | minimap2/2.24-gcccore-11.3.0 <br>samtools/1.16.1-gcc-11.3.0                                           |
| bcftools      | bcftools/1.15.1-gcc-11.3.0                                                             |
| gfatools      | gfatools 0.4<br>htslib 1.14<br>k8 0.2.5<br>caln50 01091f2                  |
| hifiasm       | hifiasm 0.19.4                                                             |
| htslib        | htslib 1.14                                                                |
| paftools      | paftools 2.26-r1182-dirty                                                  |
| pyyaml        | python 3.8.10; custom scripts                                              |
| samtools      |samtools/1.16.1-gcc-11.3.0                                                              |
| yak           | yak 0.1                                                                    |


```
#!/bin/bash
#SBATCH -N 1                       # Yêu cầu 1 node
#SBATCH -n 1                       # Yêu cầu 1 task
#SBATCH -c 16                      # Yêu cầu 16 CPU cores cho mỗi task
#SBATCH --mem=300GB                # Yêu cầu 250GB bộ nhớ RAM
#SBATCH -o out_%x_%j.txt           # Xuất file log ra file có tên out_<tên công việc>_<ID công việc>.txt
#SBATCH -e error_%x_%j.txt         # Xuất file lỗi ra file có tên error_<tên công việc>_<ID công việc>.txt
#SBATCH --job-name=asm920          # Đặt tên công việc là "asm"
#SBATCH --time=30:00:00            # Thời gian chạy tối đa là 24 giờ
#SBATCH --partition=general        # Sử dụng phân vùng "general"
#SBATCH --account=a_nguyen_quan    # Sử dụng tài khoản "a_nguyen_quan" để tính toán tài nguyên sử dụng

# parameters
bam="/QRISdata/Q3570/Data/sequencing_data/NGUY-0032_PacBio/hifi_data/VN_01_01_0920/20220803_Sequel64123_0067/Merged/VN0920.hifi_reads.bam"
fasta="/QRISdata/Q3570/Data/sequencing_data/NGUY-0032_PacBio/hifi_data/VN_01_01_0920/20220803_Sequel64123_0067/Merged/"
prefix="/QRISdata/Q3570/Data/sequencing_data/NGUY-0032_PacBio/hifi_data/VN_01_01_0920/20220803_Sequel64123_0067/asm_output/"
mkdir -p "${prefix}"
bam_basename=$(basename "$bam" .bam)
threads=16

# active env for installed tools: gfatools, bgzip
conda init
source activate quast
# Load tools
module load samtools/1.16.1-gcc-11.3.0 
module load minimap2/2.24-gcccore-11.3.0 
module load  bcftools/1.15.1-gcc-11.3.0 
module load tabixpp/1.1.0-gcc-10.3.0
source ~/.bashrc

# Initial: Convert bam to fasta using samtools or bedtools. 
# Input:            bam file;
# Output:           fasta/fastq file, it is much smaller than binary bam file
samtools fasta -@ $(($threads - 1)) "$bam" > "${fasta}${bam_basename}.fasta"

# Step 1: De-novo assembly by hifiasm. In HPC: hifiasm/0.16.1-gcccore-10.3.0; or download from Github
# Input:            fasta/fastq file;
# Output hifiasm:    gfa, bed, we will need the {basename}.bp.p_ctg.gfa
cd /scratch/project/stseq/Trung/hifiasm/
./hifiasm -o "$prefix" -t "$threads" "${fasta}${bam_basename}.fasta"

# Step 2: gfa -> fasta -> fasta.gz
gfatools gfa2fa "${prefix}${bam_basename}.bp.p_ctg.gfa" > "${prefix}${bam_basename}.bp.p_ctg.fasta"
bgzip --threads $threads --stdout "${prefix}${bam_basename}.bp.p_ctg.fasta" > "${prefix}${bam_basename}.bp.p_ctg.fasta.gz"

# Optional for assembly stats
/scratch/project/stseq/Trung/Conda/envs/quast/bin/k8 \
    /scratch/project/stseq/Trung/Conda/envs/quast/bin/calN50.js \
    -L3.1g "${prefix}${bam_basename}.bp.p_ctg.fasta.gz" > \
    "${prefix}${bam_basename}.bp.p_ctg.fasta.stats.txt"

# Step 3: Align fasta file to HG38 reference
# Input:            HG38 reference (wget http://hgdownload.soe.ucsc.edu/goldenPath/hg38/bigZips/hg38.fa.gz); 
#                   query_sequences: fasta.gz file
# Output:           bam file

reference="/scratch/project/stseq/Trung/vngenome/hg38.fa"
sample_id="VN0920"
query_sequences="${prefix}${bam_basename}.bp.p_ctg.fasta.gz"
reference_name="hg38"

# Ensure the calculated thread count is non-negative
minimap_threads=$((threads > 8 ? threads - 8 : 1))

minimap2 \
    -t "$minimap_threads" \
    -L \
    --secondary=no --eqx --cs -a \
    -x asm5 \
    -R "@RG\tID:${sample_id}_hifiasm\tSM:${sample_id}" \
    "$reference" \
    "$query_sequences" | \
    samtools sort \
    -@ "$minimap_threads" \
    -T ./TMP \
    -m 100G \
    -O BAM \
    -o "${prefix}${sample_id}.asm.${reference_name}.bam"

samtools index "${prefix}${sample_id}.asm.${reference_name}.bam"

# Optional: Get more stats from assembly
samtools \
    view -h "${prefix}${sample_id}.asm.${reference_name}.bam" | \
    /scratch/project/stseq/Trung/Conda/envs/quast/bin/k8 \
        /scratch/project/stseq/Trung/Conda/envs/quast/bin/paftools.js sam2paf - | \
    sort -k6,6 -k8,8n | \
    /scratch/project/stseq/Trung/Conda/envs/quast/bin/k8 \
        /scratch/project/stseq/Trung/Conda/envs/quast/bin/paftools.js call \
        -L5000 -f "$reference" -s "$sample_id" - > "${prefix}${bam_basename}.paftools.vcf"

bgzip --threads $threads --stdout "${prefix}${bam_basename}.paftools.vcf" > "${prefix}${bam_basename}.paftools.vcf.gz"
tabix -p vcf "${prefix}${bam_basename}.paftools.vcf.gz"
bcftools stats --threads $((threads - 1)) "${prefix}${bam_basename}.paftools.vcf.gz" > "${prefix}${bam_basename}.stats.txt"

conda deactivate

## If you can run paftools.js from minimap2, you already have k8 installed. If not:

## install k8 without conda:
# curl -L https://github.com/attractivechaos/k8/releases/download/v0.2.4/k8-0.2.4.tar.bz2 | tar -jxf -
# cp k8-0.2.4/k8-`uname -s` k8         # or copy it to a directory on your $PATH

## install k8 via bioconda:
# conda install -c bioconda minimap2   # k8 comes with minimap2
```

## Hifiasm
Hifiasm là một trình tổng hợp de novo nhanh chóng cho các bản đọc PacBio HiFi với phân giải haplotype. Nó có thể tổng hợp một bộ gen người trong vài giờ và tổng hợp một bộ gen cây sequoia California khoảng 30Gb trong vài ngày. Hifiasm phát ra các bộ phận tổng hợp một phần có chất lượng cạnh tranh với các trình tổng hợp tốt nhất. Khi có dữ liệu đọc ngắn của cha mẹ hoặc dữ liệu Hi-C, nó tạo ra các bộ tổng hợp có phân giải haplotype tốt nhất cho đến nay. Nó giúp đơn giản hoá quy trình tổng hợp, rút ngắn thời gian, không cần các trình đánh bóng như pilon hay racon. 
### Sử dụng hifiasm
Một lệnh cơ bản với hifiasm như sau:
```
./hifiasm -o NA12878.asm -t 32 NA12878.fq.gz
```

Đối với ví dụ này, các contig chính được ghi vào `NA12878.asm.bp.p_ctg.gfa`. Từ phiên bản v0.15, hifiasm cũng tạo ra 2 tập các contigs được một phần vào `NA12878.asm.bp.hap?.p_ctg.gfa`. Cặp tệp này có thể được coi là đại diện cho hai haplotype trong một genôm lưỡng bội, mặc dù có những lỗi chuyển đổi thỉnh thoảng xảy ra. Tần suất của các lỗi chuyển đổi được xác định bởi độ dị hợp tử của mẫu nhập vào.

Trong lần chạy đầu tiên, hifiasm lưu các reads đã sửa và trùng lặp vào đĩa dưới dạng NA12878.asm.*.bin. Nó sử dụng lại kết quả đã lưu để tránh tính toán trùng lặp all-vs-all mất nhiều thời gian vào lần sau. Bạn có thể chỉ định `-i` để bỏ qua các trùng lặp đã tính toán trước và làm lại việc trùng lặp từ các raw reads. Bạn cũng có thể xuất các reads đã sửa lỗi dưới dạng FASTA và reads trùng lặp trong PAF với:

Đối với các mẫu có tỷ lệ dị hợp tử cao, một vấn đề phổ biến là một bộ contig phân đoạn một phần lớn hơn nhiều so với bộ kia. Để khắc phục vấn đề này, vui lòng thiết lập giá trị nhỏ hơn cho `-s` (mặc định: 0.55). Một khả năng khác là hifiasm nhận diện sai ngưỡng phủ sóng cho các đọc đồng hợp tử. Trong trường hợp này, vui lòng thiết lập `--hom-cov` cho phủ sóng đồng hợp tử.

```
hifiasm -o NA12878.asm -t 32 --write-paf --write-ec /dev/null
```
Hifiasm mặc định loại bỏ sự trùng lặp của haplotig (purges haplotig). Đối với các bộ gen thuần chủng (inbred) hoặc đồng hợp tử (homozygous), bạn có thể tắt việc loại bỏ với tùy chọn `-0l0`. Các bản đọc HiFi cũ có thể chứa các chuỗi adapter ngắn ở hai đầu của bản đọc. Bạn có thể chỉ định `-z20` để cắt cả hai đầu của bản đọc bởi 20bp. Đối với các bộ gen nhỏ, sử dụng `-f0` để vô hiệu hóa bộ lọc bloom ban đầu mà chiếm 16GB bộ nhớ ở đầu. Đối với các bộ gen lớn hơn nhiều so với con người, áp dụng `-f38` hoặc thậm chí `-f39` được ưa chuộng để tiết kiệm bộ nhớ trên việc đếm k-mer.

### Produce primary/alternate assemblies
To get primary/alternate assemblies, the option `--primary` should be set:

```
hifiasm -o NA12878.asm --primary -t 32 NA12878.fq.gz
```
The primary contigs and the alternate contigs are written to `NA12878.asm.p_ctg.gfa` and `NA12878.asm.a_ctg.gfa`, respectively. For inbred or homozygous genomes, the primary/alternate assemblies can be also produced by `-l0`. Similarly, turning `-s` or `--hom-cov` should be helpful if the primary assembly is too large.
### Hi-C integration
```
hifiasm -o NA12878.asm -t32 --h1 read1.fq.gz --h2 read2.fq.gz HiFi-reads.fq.gz
```
Trong chế độ này, mỗi contig được cho là một haplotig, theo định nghĩa chỉ đến từ một hợp tử cha mẹ duy nhất.

Hiện tại Hifiasm không thực hiện việc ghép nối. Bạn cần chạy một trình ghép nối độc lập như SALSA hoặc 3D-DNA để ghép nối các haplotig đã được phân loại.

### Trio binning

### Ultra-long ONT integration
Hifiasm could integrate ultra-long ONT reads to produce the telomere-to-telomere assembly:
```
hifiasm -o NA12878.asm -t32 --ul ul.fq.gz HiFi-reads.fq.gz
```
For the single-sample telomere-to-telomere assembly with Hi-C reads:
```
hifiasm -o NA12878.asm -t32 --ul ul.fq.gz --h1 read1.fq.gz --h2 read2.fq.gz HiFi-reads.fq.gz
```
For the trio-binning telomere-to-telomere assembly；
```
hifiasm -o NA12878.asm -t32 --ul ul.fq.gz -1 pat.yak -2 mat.yak HiFi-reads.fq.gz
```
### Quy trình assembly với dữ liệu Pacbio
#### cài đặt hifasm: 
```
git clone https://github.com/chhylp123/hifiasm
cd hifiasm && make
```
hoặc:
```
conda install 0c bioconda hifiasm
```
#### Sử dụng:
Có 3 quy trình khác nhau tuỳ vào dữ liệu đầu vào: 
* **HiFi-only Assembly** - Assembling HiFi reads without additional data types
* **Trio-binning Assembly** - Producing fully phased assemblies with HiFi and trio-binning data
* **Hi-C Integrated Assembly** - Producing fully phased assemblies with HiFi and Hi-C data

#### Assembly với dữ liệu Pacbio 
`/QRISdata/Q3570/Data/sequencing_data/NGUY-0032_PacBio/hifi_data/` 

1. **Bước 1**: Chuyển đổi file `.bam` sang `.fq` nếu cần thiết, sử dụng `bedtools` hoặc `samtools`
```
module load bedtools/2.30.0-gcc-11.3.0
bedtools bamtofastq -i VN0007.hifi_reads.bam -fq VN0007.hifi_reads.fq

# samtools fastq -@ $(nproc) -o output.fq input.bam
```

2. **Assembly with hifiasm**

```
#!/bin/bash
#SBATCH -N 1                       # Yêu cầu 1 node
#SBATCH -n 1                       # Yêu cầu 1 task
#SBATCH -c 16                      # Yêu cầu 16 CPU cores cho mỗi task
#SBATCH --mem=250GB                # Yêu cầu 250GB bộ nhớ RAM
#SBATCH -o out_%x_%j.txt           # Xuất file log ra file có tên out_<tên công việc>_<ID công việc>.txt
#SBATCH -e error_%x_%j.txt         # Xuất file lỗi ra file có tên error_<tên công việc>_<ID công việc>.txt
#SBATCH --job-name=asm          # Đặt tên công việc là "asm"
#SBATCH --time=50:00:00            # Thời gian chạy tối đa là 50 giờ
#SBATCH --partition=general        # Sử dụng phân vùng "general"
#SBATCH --account=a_nguyen_quan    # Sử dụng tài khoản "a_nguyen_quan" để tính toán tài nguyên sử dụng

module load bedtools/2.30.0-gcc-11.3.0      # bedtools/2.30.0-gcc-10.3.0
source ~/.bashrc

# cho 1 sample, chuyển đổi nó về .fq, sau đó gọi hifiasm để assembly
# cd /scratch/project/stseq/Trung/hifiasm
cd /QRISdata/Q3570/Data/sequencing_data/NGUY-0032_PacBio/hifi_data/VN_01_00_0007/20220803_Sequel64123_0067/Merged/
bedtools bamtofastq -i VN0007.hifi_reads.bam -fq VN0007.hifi_reads.fq
/scratch/project/stseq/Trung/hifiasm/hifiasm -o VN0007.hifi_reads.asm -t 32 VN0007.hifi_reads.fq

```

### Workflows HiFi-human-assembly-WDL
```

```

## [Quast](https://github.com/ablab/quast): Genome assembly evaluation tool
**Install**:
```
git clone https://github.com/ablab/quast.git
# /sw/auto/rocky8c/epyc3/software/Miniconda3/23.9.0-0/lib/python3.11/site-packages/
```

**Usage**:
```
./quast.py test_data/contigs_1.fasta \
           test_data/contigs_2.fasta \
        -r test_data/reference.fasta.gz \
        -g test_data/genes.txt \
        -1 test_data/reads1.fastq.gz -2 test_data/reads2.fastq.gz \
        -o quast_test_output
```
**Output**:
```
report.txt      summary table
report.tsv      tab-separated version, for parsing, or for spreadsheets (Google Docs, Excel, etc)  
report.tex      Latex version
report.pdf      PDF version, includes all tables and plots for some statistics
report.html     everything in an interactive HTML file
icarus.html     Icarus main menu with links to interactive viewers
contigs_reports/        [only if a reference genome is provided]
  misassemblies_report  detailed report on misassemblies
  unaligned_report      detailed report on unaligned and partially unaligned contigs
k_mer_stats/            [only if --k-mer-stats is specified]
  kmers_report          detailed report on k-mer-based metrics
reads_stats/            [only if reads are provided]
  reads_report          detailed report on mapped reads statistics
```

**Metrics based only on contigs**:
* Number of large contigs (i.e., longer than 500 bp) and total length of them.
* Length of the largest contig.
* N50 (length of a contig, such that all the contigs of at least the same length together cover at least 50% of the assembly).
* Number of predicted genes, discovered either by GeneMark.hmm (for prokaryotes), GeneMark-ES or GlimmerHMM (for eukaryotes), or MetaGeneMark (for metagenomes).

**When a reference is given**:
* Numbers of misassemblies of different kinds (inversions, relocations, translocations, interspecies translocations (metaQUAST only) or local).
* Number and total length of unaligned contigs.
* Numbers of mismatches and indels, over the assembly and per 100 kb.
* Genome fraction %, assembled part of the reference.
* Duplication ratio, the total number of aligned bases in the assembly divided by the total number of those in the reference. If the assembly contains many contigs that cover the same regions, its duplication ratio will significantly exceed 1. This occurs due to multiple reasons, including overestimating repeat multiplicities and overlaps between contigs.
* Number of genes in the assembly, completely or partially covered, based on a user-provided list of gene positions in the reference.
* NGA50, a reference-aware version of N50 metric. It is calculated using aligned blocks instead of contigs. Such blocks are obtained after removing unaligned regions, and then splitting contigs at misassembly breakpoints. Thus, NGA50 is the length of a block, such that all the blocks of at least the same length together cover at least 50% of the reference.


## Đánh giá kết quả lắp ráp **de novo assembly**

Giả sử ta có kết quả đầu ra từ Quast như sau:

```
# contigs       50
Largest contig  50000
Total length    2500000
Reference length 2800000
GC (%)          42.17
N50             45000
N75             30000
L50             20
L75             35
# misassemblies 5
# mismatches per 100 kbp 3
# indels per 100 kbp 0.5
```

1. **# contigs**: - Số lượng contig trong bộ lắp ráp. Contig là các đoạn DNA liên tục mà không có khoảng trống không xác định.
2. **Largest contig**: - Chiều dài của contig lớn nhất trong bộ lắp ráp, tính bằng base pair (bp).
3. **Total length**: - Tổng chiều dài của tất cả các contig trong bộ lắp ráp, tính bằng base pair (bp).
4. **Reference length**: - Chiều dài của bộ gen tham chiếu. Đây là chiều dài của bộ gen mà bạn đang so sánh với bộ lắp ráp của mình.
5. **GC (%)**: - Tỷ lệ phần trăm của các base guanine (G) và cytosine (C) trong bộ lắp ráp.
6. **N50**: - Chiều dài của contig ngắn nhất trong nhóm các contig dài nhất mà tổng chiều dài của chúng chiếm ít nhất 50% tổng chiều dài của tất cả các contig. Đây là một chỉ số phổ biến để đánh giá độ phân mảnh của bộ lắp ráp.
7. **N75**: - Tương tự như N50, nhưng tính cho 75% tổng chiều dài của tất cả các contig.
8. **L50**: - Số lượng contig dài nhất sao cho tổng chiều dài của chúng chiếm ít nhất 50% tổng chiều dài của tất cả các contig. Chỉ số này giúp bạn hiểu rõ hơn về mức độ phân mảnh của bộ lắp ráp.
9. **L75**: - Tương tự như L50, nhưng tính cho 75% tổng chiều dài của tất cả các contig.
10. **# misassemblies**: - Số lượng lỗi lắp ráp. Lỗi lắp ráp xảy ra khi một đoạn DNA bị lắp ráp sai vị trí hoặc bị đảo ngược so với bộ gen tham chiếu.
11. **# mismatches per 100 kbp**: - Số lượng nucleotide không khớp trên mỗi 100,000 base pair khi so sánh với bộ gen tham chiếu.
12. **# indels per 100 kbp**: - Số lượng các insertion (thêm vào) và deletion (xóa bỏ) trên mỗi 100,000 base pair khi so sánh với bộ gen tham chiếu.

### đánh giá:
- **Số lượng contig ít** và **chiều dài lớn nhất của contig cao** thường là dấu hiệu của một bộ lắp ráp chất lượng cao, ít bị phân mảnh.
- **N50 và L50** càng cao càng tốt, chỉ ra rằng các contig trong bộ lắp ráp có xu hướng dài và ít bị phân mảnh.
- **Số lượng lỗi lắp ráp thấp** và **số lượng mismatches và indels thấp** cho thấy bộ lắp ráp có độ chính xác cao khi so sánh với bộ gen tham chiếu.

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
9.  **HiFi, Duplex, and ultra-long ONT (ULONT)**: Pacbio
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
