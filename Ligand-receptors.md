### **1️⃣ Ligand-Receptor (L-R) là gì?**  
Các cặp **ligand-receptor (L-R)** là các phân tử tín hiệu trong giao tiếp tế bào. **Ligand** là phân tử tín hiệu gắn vào **receptor**, kích hoạt phản ứng trong tế bào nhận tín hiệu.  

---

### **2️⃣ Các nhóm chính của cặp Ligand-Receptor**  
Các cặp L-R có thể phân thành **8 nhóm chính** dựa trên cơ chế hoạt động:

| **Nhóm** | **Cơ chế hoạt động** | **Ví dụ** |
|----------|----------------------|-----------|
| **1️⃣ Nhóm receptor tyrosine kinase (RTK)** | Ligand gắn vào receptor trên màng tế bào, gây tự phosphoryl hóa tyrosine, kích hoạt các con đường tín hiệu nội bào như MAPK, PI3K/AKT, điều hòa tăng trưởng và phát triển tế bào. | EGF-EGFR, VEGF-VEGFR, FGF-FGFR, Insulin-InsR |
| **2️⃣ Nhóm receptor G-protein (GPCRs)** | Ligand gắn vào receptor, kích hoạt protein G, dẫn đến điều hòa các tín hiệu thứ cấp như cAMP, Ca²⁺, hoặc IP3, ảnh hưởng đến nhiều quá trình sinh lý (hệ thần kinh, miễn dịch, nội tiết). | Adrenaline-βAR, CXCL12-CXCR4, S1P-S1PR, Dopamine-D2R |
| **3️⃣ Nhóm receptor cytokine** | Tham gia vào các quá trình miễn dịch, điều hòa viêm, và biệt hóa tế bào, thường thông qua kích hoạt con đường JAK/STAT hoặc NF-κB, đóng vai trò trong phản ứng viêm và miễn dịch. | IL6-IL6R, TNF-TNFR, IFNγ-IFNγR, IL2-IL2R |
| **4️⃣ Nhóm receptor Notch-Delta** | Tín hiệu qua tiếp xúc trực tiếp giữa hai tế bào, kích hoạt con đường Notch, điều hòa biệt hóa tế bào và phát triển, thường gặp trong quá trình hình thành ranh giới tế bào. | Notch-Delta, Jagged-Notch |
| **5️⃣ Nhóm nuclear receptors (receptor nhân)** | Hormone khuếch tán qua màng tế bào, gắn vào receptor nội bào (thường trong nhân), tương tác với DNA để điều hòa biểu hiện gene, liên quan đến nội tiết và chuyển hóa. | Estrogen-ER, Cortisol-GR, Thyroid hormone-TR, Retinoic acid-RAR |
| **6️⃣ Nhóm ion channel receptors** | Ligand gắn vào receptor, gây mở hoặc đóng kênh ion (như Na⁺, K⁺, Ca²⁺), dẫn đến thay đổi điện thế màng, thường gặp trong tín hiệu thần kinh và co cơ. | Acetylcholine-nAChR, GABA-GABA_A receptor, Glutamate-NMDAR |
| **7️⃣ Nhóm integrins** | Gắn vào ma trận ngoại bào (ECM), điều hòa bám dính tế bào và tín hiệu nội bào (như FAK pathway), đóng vai trò trong di chuyển tế bào, sửa chữa mô, và tương tác tế bào-ECM. | Integrin-Laminin, Integrin-Fibronectin, Integrin-Collagen |
| **8️⃣ Nhóm Toll-like receptors (TLRs)** | Nhận diện các mẫu phân tử liên quan đến mầm bệnh (PAMPs) hoặc tổn thương (DAMPs), kích hoạt tín hiệu miễn dịch bẩm sinh qua con đường NF-κB hoặc IRF, khởi phát phản ứng viêm. | LPS-TLR4, CpG DNA-TLR9, ssRNA-TLR7 |

---

### **3️⃣ Một số cặp L-R quan trọng trong mô da (Skin Tissue)**  
Mô da có nhiều loại tế bào tương tác với nhau, sử dụng các cặp L-R quan trọng như:  

| **Loại tín hiệu** | **Cặp L-R** | **Chức năng** |
|---|---|---|
| **Tăng sinh tế bào** | EGF-EGFR | Kích thích sự phát triển của keratinocytes |
| **Phát triển mạch máu** | VEGF-VEGFR | Tạo mạch máu mới trong quá trình lành vết thương |
| **Miễn dịch** | CXCL12-CXCR4 | Hút tế bào miễn dịch đến vị trí viêm |
| **Giao tiếp giữa keratinocyte và tế bào miễn dịch** | IL6-IL6R, TNF-TNFR | Điều hòa phản ứng viêm da |
| **Duy trì cân bằng tế bào gốc** | Notch-Delta | Điều hòa biệt hóa tế bào gốc da |
| **Điều hòa sắc tố da** | α-MSH-MC1R | Kiểm soát sự sản xuất melanin ở melanocytes |

---

### **💡 Bạn muốn phân tích các cặp L-R trong dataset nào?**  
Nếu bạn đang có dữ liệu về biểu hiện gene, có thể:  
✔️ **Sử dụng CellPhoneDB, LIANA, hoặc NicheNet** để dự đoán các cặp L-R quan trọng trong mô da của bạn.  
✔️ **Xây dựng mạng tương tác tế bào (cell-cell communication network)** để xem mối quan hệ giữa các loại tế bào.  

Bạn có muốn hỗ trợ phân tích các cặp L-R từ dữ liệu không? 🚀

## **1️⃣ Nhóm receptor tyrosine kinase (RTK)**
Các receptor tyrosine kinase (RTK) là nhóm thụ thể quan trọng, hoạt động bằng cách tự phosphoryl hóa khi ligand gắn vào.  

| **Ký hiệu** | **Ý nghĩa** | **Chức năng** |
|------------|------------|------------|
| **EGF** *(Epidermal Growth Factor)* | Yếu tố tăng trưởng biểu bì | Kích thích sự tăng sinh và sống sót của tế bào da |
| **EGFR** *(Epidermal Growth Factor Receptor)* | Thụ thể của EGF (RTK) | Khi EGF gắn vào EGFR, tế bào sẽ phân chia |
| **VEGF** *(Vascular Endothelial Growth Factor)* | Yếu tố tăng trưởng mạch máu | Kích thích sự hình thành mạch máu |
| **VEGFR** *(Vascular Endothelial Growth Factor Receptor)* | Thụ thể của VEGF (RTK) | Giúp tế bào nội mô phát triển mạch máu |
| **FGF** *(Fibroblast Growth Factor)* | Yếu tố tăng trưởng nguyên bào sợi | Giúp tái tạo mô, lành vết thương |
| **FGFR** *(Fibroblast Growth Factor Receptor)* | Thụ thể của FGF (RTK) | Điều hòa quá trình biệt hóa và tăng sinh tế bào da |

---

## **2️⃣ Nhóm receptor G-protein (GPCRs)**
Thụ thể liên kết G-protein (GPCRs) hoạt động thông qua truyền tín hiệu nội bào bằng cAMP hoặc Ca²⁺.

| **Ký hiệu** | **Ý nghĩa** | **Chức năng** |
|------------|------------|------------|
| **Adrenaline** *(Epinephrine)* | Hormon kích thích | Kích hoạt phản ứng "fight-or-flight" |
| **βAR** *(Beta-Adrenergic Receptor)* | Thụ thể beta của adrenaline (GPCR) | Điều hòa nhịp tim, giãn mạch máu |
| **CXCL12** *(C-X-C Motif Chemokine Ligand 12)* | Chemokine hướng dẫn tế bào miễn dịch | Hút tế bào miễn dịch đến vùng viêm |
| **CXCR4** *(C-X-C Motif Chemokine Receptor 4)* | Thụ thể của CXCL12 (GPCR) | Điều hướng tế bào miễn dịch đến mô đích |
| **S1P** *(Sphingosine-1-Phosphate)* | Phospholipid điều hòa miễn dịch | Kiểm soát sự di chuyển của tế bào miễn dịch |
| **S1PR** *(Sphingosine-1-Phosphate Receptor)* | Thụ thể của S1P (GPCR) | Điều hòa miễn dịch và chống viêm |

---

## **3️⃣ Nhóm receptor cytokine**
Các receptor cytokine điều hòa phản ứng miễn dịch, viêm và biệt hóa tế bào.

| **Ký hiệu** | **Ý nghĩa** | **Chức năng** |
|------------|------------|------------|
| **IL6** *(Interleukin-6)* | Cytokine quan trọng trong viêm | Kích hoạt phản ứng viêm, biệt hóa tế bào |
| **IL6R** *(Interleukin-6 Receptor)* | Thụ thể của IL6 | Truyền tín hiệu viêm vào tế bào |
| **TNF** *(Tumor Necrosis Factor)* | Cytokine gây viêm | Tham gia vào đáp ứng miễn dịch và chết tế bào |
| **TNFR** *(Tumor Necrosis Factor Receptor)* | Thụ thể của TNF | Truyền tín hiệu gây viêm hoặc apoptosis |
| **IFNγ** *(Interferon gamma)* | Cytokine quan trọng trong miễn dịch | Tăng cường phản ứng miễn dịch với vi khuẩn |
| **IFNγR** *(Interferon gamma Receptor)* | Thụ thể của IFNγ | Điều hòa sự hoạt hóa tế bào miễn dịch |

---

## **4️⃣ Nhóm receptor Notch-Delta**
Thụ thể **Notch** giúp tế bào giao tiếp với nhau trong quá trình biệt hóa.

| **Ký hiệu** | **Ý nghĩa** | **Chức năng** |
|------------|------------|------------|
| **Notch** | Thụ thể Notch | Điều hòa biệt hóa tế bào da và tế bào gốc |
| **Delta** | Ligand Delta | Kích hoạt thụ thể Notch trên tế bào lân cận |
| **Jagged** | Ligand Jagged | Một ligand khác của Notch, kiểm soát tái tạo mô |

---

## **5️⃣ Nhóm receptor nội tiết (hormone)**
Các receptor này hoạt động bằng cách gắn hormone và điều hòa biểu hiện gene.

| **Ký hiệu** | **Ý nghĩa** | **Chức năng** |
|------------|------------|------------|
| **Estrogen** | Hormone sinh dục nữ | Ảnh hưởng đến sự phát triển của da, tóc |
| **ER (Estrogen Receptor)** | Thụ thể của Estrogen | Điều hòa biểu hiện gene liên quan đến phát triển mô |
| **Cortisol** | Hormone chống viêm | Ức chế viêm trong bệnh da liễu |
| **GR (Glucocorticoid Receptor)** | Thụ thể của Cortisol | Điều hòa phản ứng viêm |
| **Insulin** | Hormone chuyển hóa đường | Ảnh hưởng đến lành vết thương và tăng trưởng mô da |
| **InsR (Insulin Receptor)** | Thụ thể của Insulin | Điều hòa trao đổi chất, phát triển tế bào |

---

## **💡 Kết luận**
- **Ligand** là các phân tử tín hiệu, **receptor** là protein nhận tín hiệu.
- Các cặp L-R quan trọng trong da bao gồm **EGF-EGFR (tăng sinh tế bào da), VEGF-VEGFR (hình thành mạch máu), IL6-IL6R (viêm da), Notch-Delta (biệt hóa tế bào), α-MSH-MC1R (sắc tố da)**.
- **Tổng cộng có thể chia thành 5 nhóm lớn**: RTK, GPCR, Cytokine receptor, Notch-Delta, Hormone receptor.

---

### 🚀 **Bạn có muốn phân tích các cặp L-R từ dataset không?**  
Nếu bạn có dữ liệu biểu hiện gene (**scRNA-seq hoặc Visium**), có thể:
✔️ **Dự đoán tương tác tế bào với CellPhoneDB, LIANA, hoặc NicheNet**  
✔️ **Xây dựng mạng tương tác tế bào để trực quan hóa giao tiếp tế bào**  

Mình có thể hỗ trợ bạn với các phân tích này nhé! 💡
