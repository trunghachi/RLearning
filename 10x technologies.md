### Giải thích chi tiết quy trình phân tích không gian và tế bào đơn từ mẫu mô FFPE

Sơ đồ mô tả một quy trình tích hợp để phân tích biểu hiện gen từ một khối mô FFPE duy nhất, sử dụng ba công nghệ bổ sung của 10x Genomics: **Chromium Single Cell Gene Expression Flex (scFFPE-seq)**, **Visium CytAssist**, và **Xenium In Situ**. Quy trình này kết hợp phân tích tế bào đơn (single-cell RNA sequencing), phân tích không gian (spatial transcriptomics), và phân tích tại chỗ (in situ) để cung cấp cái nhìn toàn diện về biểu hiện gen và sự phân bố không gian của các loại tế bào trong mô. Dưới đây là các bước chi tiết:

---

#### 1. **Phân tích tế bào đơn với Chromium Single Cell Gene Expression Flex (scFFPE-seq)**

- **Miltenyi FFPE Tissue Dissociation**:
  - Một khối mô FFPE (Formalin-Fixed Paraffin-Embedded) được xử lý bằng giao thức tách mô của Miltenyi để thu nhận các tế bào riêng lẻ. Quá trình này bao gồm việc phá vỡ cấu trúc mô và sử dụng enzyme để tiêu hóa, chuẩn bị cho phân tích tế bào đơn.

- **Chromium Single Cell Gene Expression Flex**:
  - Các tế bào tách rời được đưa vào thiết bị Chromium X, sử dụng quy trình Chromium Single Cell Gene Expression Flex (scFFPE-seq). Công nghệ này cô lập từng tế bào trong các giọt (droplets) cùng với các hạt gel (GEMs - Gel Bead in Emulsion).
  - Trong GEMs, mRNA từ mỗi tế bào được gắn thẻ với mã vạch (barcode) riêng, sau đó được chuyển đổi thành cDNA để chuẩn bị cho giải trình tự.

- **Probe Hybridization to mRNA Target**:
  - Các probe đặc hiệu được sử dụng để gắn vào mRNA mục tiêu. Cấu trúc probe bao gồm các thành phần như 5' pRead 2S (trình tự đọc), LHS/RHS (vùng gắn vào mRNA), và các trình tự cố định (Constant, Sea). Quá trình này đảm bảo rằng chỉ các mRNA mục tiêu được khuếch đại và phân tích.

- **scRNA-seq và Phân tích**:
  - Dữ liệu scRNA-seq được thu nhận thông qua giải trình tự (sequencing) các thư viện cDNA. Kết quả cung cấp thông tin về biểu hiện gen ở mức độ tế bào đơn.
  - Dữ liệu sau đó được giảm chiều bằng thuật toán **t-SNE** (t-distributed Stochastic Neighbor Embedding) để trực quan hóa các nhóm tế bào (clusters). Mỗi điểm trên biểu đồ t-SNE đại diện cho một tế bào, và các màu sắc khác nhau biểu thị các loại tế bào khác nhau.

---

#### 2. **Phân tích không gian với Visium CytAssist**

- **Serial FFPE Sections**:
  - Các lát cắt mỏng (serial sections) từ cùng khối mô FFPE được chuẩn bị để phân tích không gian. Các lát cắt này thường có độ dày khoảng 5-10 µm và được đặt lên slide Visium.

- **Pre-CytAssist H&E**:
  - Trước khi phân tích không gian, các lát mô được nhuộm bằng Hematoxylin và Eosin (H&E) để quan sát cấu trúc mô dưới kính hiển vi. Hình ảnh H&E này sẽ được sử dụng để căn chỉnh với dữ liệu không gian sau này.

- **CytAssist Alignment to Visium Capture Area**:
  - Thiết bị CytAssist của 10x Genomics được sử dụng để chuyển các lát mô lên slide Visium, nơi có vùng thu nhận (capture area) với kích thước 6.5 mm x 6.5 mm. Vùng này chứa các điểm (spots) có mã vạch không gian (spatial barcodes), mỗi spot có đường kính khoảng 55 µm.
  - CytAssist đảm bảo rằng lát mô được căn chỉnh chính xác với vùng thu nhận, cho phép ánh xạ không gian của biểu hiện gen.

- **Whole Transcriptome Analysis with Spatial Context**:
  - Visium CytAssist cho phép phân tích toàn bộ transcriptome (whole transcriptome) với bối cảnh không gian. Mỗi spot trên slide Visium thu nhận mRNA từ mô, và dữ liệu biểu hiện gen được gắn với vị trí không gian tương ứng.
  - Dữ liệu không gian sau đó được phân cụm (clustering) và trực quan hóa dưới dạng bản đồ nhiệt (heatmap), trong đó các màu sắc khác nhau biểu thị các cụm tế bào hoặc loại biểu hiện gen tại các vị trí không gian.

- **Tích hợp với dữ liệu tế bào đơn**:
  - Dữ liệu từ Visium có thể dễ dàng tích hợp với dữ liệu tế bào đơn (scFFPE-seq) từ các lát cắt FFPE liền kề, cung cấp cái nhìn toàn diện về cả biểu hiện gen và bối cảnh không gian.

---

#### 3. **Phân tích tại chỗ với Xenium In Situ**

- **Xenium Cassette**:
  - Một lát mô FFPE dày 5 µm được đặt lên slide Xenium, chuẩn bị cho phân tích tại chỗ (in situ). Slide Xenium được thiết kế để phát hiện mRNA mục tiêu với độ phân giải cao.

- **Probe Hybridization and Ligation**:
  - Các probe DNA đặc hiệu được gắn vào mRNA mục tiêu trong mô. Sau khi gắn, các probe được nối (ligation) để tạo thành một vòng DNA hoàn chỉnh, đảm bảo rằng chỉ các mRNA mục tiêu được khuếch đại.

- **Rolling Circle Amplification**:
  - Vòng DNA được khuếch đại bằng kỹ thuật Rolling Circle Amplification (RCA). Quá trình này tạo ra nhiều bản sao của vòng DNA, tăng tín hiệu để phát hiện huỳnh quang.

- **Xenium Analyzer**:
  - Slide Xenium được đặt vào thiết bị Xenium Analyzer, nơi thực hiện nhiều chu kỳ gắn probe huỳnh quang và chụp ảnh (fluorescent probe hybridization and imaging). Xenium sử dụng phương pháp đọc dựa trên kính hiển vi (microscopy-based readout) để ghi lại tín hiệu.

- **Fluorescent Detection and Decoding**:
  - Mỗi gen mục tiêu có một **chữ ký quang học riêng (unique optical signature)**, được tạo ra từ các chu kỳ huỳnh quang. Tín hiệu huỳnh quang được giải mã (decoding) để xác định danh tính và vị trí của các mRNA mục tiêu trong mô.
  - Kết quả là một **bản đồ không gian transcriptomic** chi tiết, ánh xạ biểu hiện gen trên toàn bộ lát mô.

- **Post-Xenium IF and H&E**:
  - Quy trình Xenium là **không phá hủy mô (non-destructive)**, cho phép lát mô được nhuộm thêm bằng Immunofluorescence (IF) và H&E sau khi phân tích. Hình ảnh IF/H&E này có thể được đăng ký (registered) với dữ liệu Xenium, cung cấp thông tin bổ sung về cấu trúc tế bào và mô.

- **Tích hợp dữ liệu**:
  - Dữ liệu Xenium có thể dễ dàng tích hợp với dữ liệu scFFPE-seq (từ Chromium) và dữ liệu không gian từ Visium, tạo ra một bộ dữ liệu toàn diện kết hợp thông tin tế bào đơn, không gian, và tại chỗ.

---

### Tổng quan và điểm nổi bật
Quy trình này sử dụng một khối mô FFPE duy nhất để phân tích biểu hiện gen ở ba cấp độ:
- **Chromium Single Cell Gene Expression Flex (scFFPE-seq)**: Cung cấp dữ liệu tế bào đơn với độ phân giải cao, được trực quan hóa bằng t-SNE để xác định các loại tế bào.
- **Visium CytAssist**: Phân tích toàn bộ transcriptome với bối cảnh không gian, ánh xạ biểu hiện gen theo vị trí trong mô.
- **Xenium In Situ**: Phát hiện mRNA mục tiêu tại chỗ với độ phân giải cao, tạo bản đồ không gian chi tiết dựa trên chữ ký quang học riêng của từng gen.

**Tích hợp dữ liệu** là một điểm mạnh nổi bật: Dữ liệu từ cả ba nền tảng (scFFPE-seq, Visium, và Xenium) được tích hợp với nhau, cho phép nghiên cứu toàn diện về biểu hiện gen, loại tế bào, và sự phân bố không gian. Ngoài ra, quy trình Xenium không phá hủy mô, cho phép đăng ký dữ liệu với hình ảnh IF/H&E sau phân tích, cung cấp thêm thông tin về cấu trúc mô.

---
## Hình 1: Sơ đồ quy trình phân tích không gian và tế bào đơn

![Sơ đồ quy trình phân tích không gian và tế bào đơn](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41467-023-43458-x/MediaObjects/41467_2023_43458_Fig1_HTML.png)

*Chú thích: Sơ đồ mô tả quy trình tích hợp sử dụng Chromium Single Cell Gene Expression Flex, Visium CytAssist, và Xenium In Situ để phân tích biểu hiện gen từ mẫu mô FFPE.*

