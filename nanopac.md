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

```
bam="path/to/your/file.bam"
prefix="prefix_for_output_files"
bam_basename=$(basename "$bam" .bam)
threads=32

# Initial: Convert bam to fasta
samtools fasta -@ $(($threads - 1)) "$bam" > "${bam_basename}.fasta"

# Step 1: De-novo assembly by hifiasm
hifiasm -o "$prefix" -t "$threads" "${bam_basename}.fasta"

# Step: gfa -> fa
gfatools gfa2fa "${prefix}.bp.p_ctg.gfa" > "${prefix}.bp.p_ctg.fasta"
bgzip --threads $threads --stdout "${prefix}.bp.p_ctg.fasta" > "${prefix}.bp.p_ctg.fasta.gz"

# Optional for assembly stats
k8 /opt/calN50/calN50.js -L3.1g "${prefix}.bp.p_ctg.fasta.gz" > "${prefix}.bp.p_ctg.fasta.stats.txt"

# Step 3: Align fasta file to HG38 reference
reference="path/to/HG38/reference"
sample_id="sample123"
query_sequences="${prefix}.bp.p_ctg.fasta.gz"
minimap2 -t $(($threads - 4)) -L --secondary=no --eqx --cs -a -x asm5 -R "@RG\\tID:${sample_id}_hifiasm\\tSM:${sample_id}" "$reference" "$query_sequences" | \
    samtools sort -@ 3 -T ./TMP -m 8G -O BAM -o "${sample_id}.asm.${reference_name}.bam"
samtools index "${sample_id}.asm.${reference_name}.bam"

# Optional step to get more stats from assembly
samtools view -h "${sample_id}.asm.${reference_name}.bam" | \
k8 /opt/minimap2-2.17/misc/paftools.js sam2paf - | \
sort -k6,6 -k8,8n | \
k8 /opt/minimap2-2.17/misc/paftools.js call -L5000 -f "$reference" -s "$sample_id" - > "${bam_basename}.paftools.vcf"
bgzip --threads $threads --stdout "${bam_basename}.paftools.vcf" > "${bam_basename}.paftools.vcf.gz"
tabix -p vcf "${bam_basename}.paftools.vcf.gz"
bcftools stats --threads $(($threads - 1)) "${bam_basename}.paftools.vcf.gz" > "${bam_basename}.stats.txt"
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

1. **# contigs**:
   - Số lượng contig trong bộ lắp ráp. Contig là các đoạn DNA liên tục mà không có khoảng trống không xác định.

2. **Largest contig**:
   - Chiều dài của contig lớn nhất trong bộ lắp ráp, tính bằng base pair (bp).

3. **Total length**:
   - Tổng chiều dài của tất cả các contig trong bộ lắp ráp, tính bằng base pair (bp).

4. **Reference length**:
   - Chiều dài của bộ gen tham chiếu. Đây là chiều dài của bộ gen mà bạn đang so sánh với bộ lắp ráp của mình.

5. **GC (%)**:
   - Tỷ lệ phần trăm của các base guanine (G) và cytosine (C) trong bộ lắp ráp.

6. **N50**:
   - Chiều dài của contig ngắn nhất trong nhóm các contig dài nhất mà tổng chiều dài của chúng chiếm ít nhất 50% tổng chiều dài của tất cả các contig. Đây là một chỉ số phổ biến để đánh giá độ phân mảnh của bộ lắp ráp.

7. **N75**:
   - Tương tự như N50, nhưng tính cho 75% tổng chiều dài của tất cả các contig.

8. **L50**:
   - Số lượng contig dài nhất sao cho tổng chiều dài của chúng chiếm ít nhất 50% tổng chiều dài của tất cả các contig. Chỉ số này giúp bạn hiểu rõ hơn về mức độ phân mảnh của bộ lắp ráp.

9. **L75**:
   - Tương tự như L50, nhưng tính cho 75% tổng chiều dài của tất cả các contig.

10. **# misassemblies**:
    - Số lượng lỗi lắp ráp. Lỗi lắp ráp xảy ra khi một đoạn DNA bị lắp ráp sai vị trí hoặc bị đảo ngược so với bộ gen tham chiếu.

11. **# mismatches per 100 kbp**:
    - Số lượng nucleotide không khớp trên mỗi 100,000 base pair khi so sánh với bộ gen tham chiếu.

12. **# indels per 100 kbp**:
    - Số lượng các insertion (thêm vào) và deletion (xóa bỏ) trên mỗi 100,000 base pair khi so sánh với bộ gen tham chiếu.

### Kết Luận

- **Số lượng contig ít** và **chiều dài lớn nhất của contig cao** thường là dấu hiệu của một bộ lắp ráp chất lượng cao, ít bị phân mảnh.
- **N50 và L50** càng cao càng tốt, chỉ ra rằng các contig trong bộ lắp ráp có xu hướng dài và ít bị phân mảnh.
- **Số lượng lỗi lắp ráp thấp** và **số lượng mismatches và indels thấp** cho thấy bộ lắp ráp có độ chính xác cao khi so sánh với bộ gen tham chiếu.
