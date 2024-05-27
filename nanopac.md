
# 1. Một số khái niệm cơ bản:
1. **Transposon**
Transposon(còn được gọi là **phần tử di động**) là một chuỗi **ADN** có khả năng tự di chuyển hoặc tự chèn chính nó vào một vị trí mới trong **genôm** (genome là tập hợp toàn bộ thông tin di truyền - bao gồm cả DNA, genes, và nhiễm sắc thể, 
trong khi nhiễm sắc thể là các đơn vị cấu tạo của genome chứa các gen cụ thể). Chúng có thể gây ra các hiệu ứng như tạo hoặc đảo ngược đột biến và thay đổi kích thước của genôm.

Có hai loại transposon chính:
   * **Cut-and-Paste Transposons**:
      - Chúng di chuyển bằng cách cắt chuỗi transposon từ một vị trí trong genôm và chèn nó vào một vị trí khác trong genôm.
      - Quá trình này được thực hiện bởi một protein gọi là **transposase**.
      - Ví dụ về loại transposon này là các phần tử **IS** (Insertion Sequences) và **P-elements** trong ngô³.
   
   * **Replicative Transposons**:
      - Chúng di chuyển bằng cách sao chép chuỗi transposon và chèn bản sao của nó vào vị trí đích trong genôm.
      - Trong loại transposition này, có một bản sao mới của transposon và cả donor lẫn recipient DNA đều có một chuỗi transposon sau khi di chuyển.
   
   * **Transposase**  là một enzyme quan trọng trong quá trình di chuyển của transposon. Nó giúp thực hiện việc cắt và chèn chuỗi transposon vào genôm.
1. **depth of 20x** : Trong ngữ cảnh của việc giải trình tự gen, “độ sâu tối thiểu 20x” nghĩa là mỗi vị trí trên bộ gen được đọc trung bình 20 lần. Điều này giúp tăng độ tin cậy của việc xác định các nucleotide tại mỗi vị trí và giảm thiểu sai sót. Độ sâu giải trình tự càng cao, khả năng phát hiện biến thể gen càng chính xác

1. **Basecalling**  là quá trình chuyển đổi các tín hiệu điện tử thô thu được từ thiết bị giải trình tự thành chuỗi nucleotide (DNA hoặc RNA). Đây giống như quá trình nhận dạng giọng nói, nơi ngôn ngữ nói được chuyển thành văn bản viết. Trong giải trình tự gen, basecalling là bước quan trọng để từ các tín hiệu điện tử, xác định được trình tự các nucleotide tạo nên DNA hoặc RNA 
1. **25–35 kilobase reads)** có nghĩa là các đoạn DNA được giải trình tự có chiều dài từ 25.000 đến 35.000 base (cặp nucleotide).

1. **contig**: contiguous sequence: dùng để chỉ một đoạn trình tự DNA liên tục được lắp ráp từ các đoạn đọc nhỏ hơn ("reads"). Đây là thành phần quan trọng của lắp ráp de novo 

## Tóm tắt một quy trình phân tích gene:
Toàn bộ quy trình phân tích gen người, từ lúc lấy mẫu đến lúc ra kết quả là bộ gen hoàn chỉnh, bao gồm các bước sau và thời gian ước tính cho mỗi bước:

1. **Thu thập mẫu (Sample Collection)**:
   - **Mô tả**: Lấy mẫu DNA từ máu, nước bọt hoặc mô khác.
   - **Công cụ**: 
   - **Thời gian**: Vài phút đến vài giờ, tùy thuộc vào loại mẫu và quy trình thu thập.
  
2. **Chiết xuất DNA (DNA Extraction)**:
   - **Mô tả**: Tách DNA ra khỏi các thành phần khác trong mẫu.
   - **Thời gian**: Vài giờ đến một ngày.

3. **Chuẩn bị thư viện (Library Preparation)**:
   - **Mô tả**: Chuẩn bị các đoạn DNA để giải trình tự, bao gồm các bước như phân mảnh DNA, thêm adapter và đánh dấu.
   - **Công cụ**: 
   - **Thời gian**: Vài giờ đến một ngày.

4. **Giải trình tự (Sequencing)**:
   - **Mô tả**: Sử dụng các thiết bị như PromethION để đọc các đoạn DNA.
   - **Công cụ**: 
   - **Thời gian**: Vài giờ đến vài ngày, tùy thuộc vào độ sâu và độ dài đoạn đọc mong muốn.

5. **Lắp ráp de novo (De Novo Assembly)**:
   - **Mô tả**: Sử dụng các công cụ như Flye để lắp ráp các đoạn đọc thô thành các contig.
   - **Công cụ**: 
   - **Thời gian**: Khoảng hai ngày để lắp ráp và đánh bóng một bộ gen người.

6. **Đánh bóng bổ sung (Additional Polishing)**:
   - **Mô tả**: Thực hiện một vòng đánh bóng bổ sung với Medaka để cải thiện chất lượng contig.
   - **Công cụ**: 
   - **Thời gian**: Vài giờ đến một ngày.

7. **Phân tích và diễn giải (Analysis and Interpretation)**:
   - **Mô tả**: Phân tích các contig đã được đánh bóng để xác định các đặc điểm di truyền và biến thể.
   - **Công cụ**: 
   - **Thời gian**: Vài ngày đến vài tuần, tùy thuộc vào mục đích và độ phức tạp của phân tích.

**Tổng thời gian**: Quá trình từ thu thập mẫu đến có được bộ gen hoàn chỉnh mất khoảng 1-2 tuần, tùy thuộc vào điều kiện cụ thể và độ phức tạp của từng bước.


# 1. Nanopore

[Assembling the human genome](https://a.storyblok.com/f/196663/cd1c1c07ec/human-assembly-workflow.pdf) using long [nanopore](https://nanoporetech.com/products/prepare) sequencing reads 

# 2. Pacbio
