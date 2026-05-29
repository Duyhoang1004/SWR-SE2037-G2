

## Citation

| Trường | Thông tin |
|---|---|
| **Tên bài báo** | Pneumonia Detection from Chest X-Ray Images Using Deep Learning and CNN |
| **Tác giả** | Dr. Samuel K. Benson, Prof. Elena Rostova |
| **Năm xuất bản** | 2024 |
| **Nguồn phát hành** | International Journal of Medical Informatics (IJMI) |
| **Link / DOI** | [10.1016/j.ijmedinf.2024.105xxx](https://doi.org/10.1016/j.ijmedinf.2024.105xxx) |

---

## 1. Problem Statement – Vấn đề bài báo giải quyết

Bài báo tập trung giải quyết các thách thức lớn trong khâu chẩn đoán bệnh lý học thông qua hình ảnh y khoa:
* **Sự thiếu hụt bác sĩ X-quang tại các vùng sâu vùng xa:** Tại các bệnh viện tuyến dưới hoặc vùng nông thôn, số lượng bác sĩ có đủ chuyên môn để đọc phim X-quang phổi rất ít. Người bệnh phải chờ đợi nhiều giờ, thậm chí nhiều ngày để có kết quả chẩn đoán viêm phổi.
* **Sai sót chủ quan do áp lực công việc:** Các bác sĩ X-quang thường phải đọc hàng trăm ca mỗi ngày, dẫn đến tình trạng mệt mỏi thị giác (visual fatigue), dễ bỏ sót các tổn thương mờ hoặc dấu hiệu viêm phổi giai đoạn sớm trên phim chụp.
* **Sự tương đồng giữa viêm phổi do vi khuẩn và virus:** Việc phân biệt bằng mắt thường giữa viêm phổi do vi khuẩn (bacterial) và virus rất khó khăn, dẫn đến việc kê đơn kháng sinh sai cách (lạm dụng kháng sinh khi nguyên nhân gốc rễ do virus gây ra).

---

## 2. Method – Phương pháp thực hiện

Nghiên cứu đề xuất xây dựng một hệ thống phân loại 3 lớp (Bình thường, Viêm phổi do vi khuẩn, Viêm phổi do virus) dựa trên mạng nơ-ron tích chập tự thiết kế (**Custom CNN**) và so sánh đối chứng với giải pháp học chuyển giao (**ResNet50**).

#### Quy trình kỹ thuật gồm 4 bước lõi:
1. **Tiền xử lý ảnh y khoa (Medical Image Pre-processing):** Cắt bỏ các vùng nhiễu bên ngoài lồng ngực. Áp dụng thuật toán **CLAHE** (Contrast Limited Adaptive Histogram Equalization) để tăng cường độ tương phản cục bộ của các vùng mô phổi bị mờ, giúp các tổn thương hiển thị rõ nét hơn.
2. **Xử lý mất cân bằng dữ liệu (Class Imbalance Analysis):** Áp dụng kỹ thuật *SMOTE* trên ma trận đặc trưng kết hợp với *Data Augmentation* đặc thù cho y tế (xoay nhẹ ảnh dưới 10 độ, tuyệt đối không lật dọc hoặc lật ngang vì cấu trúc tim/phổi của cơ thể người không được phép đảo ngược).
3. **Huấn luyện mô hình:**
   * *Custom CNN:* Cấu trúc 5 lớp Conv2D xen kẽ MaxPooling2D nhằm tối ưu tốc độ phần cứng, hướng tới việc nhúng vào các máy tính cấu hình yếu ở bệnh viện nhỏ.
   * *ResNet50 (Fine-tuned):* Kế thừa trọng số từ ImageNet, bổ sung lớp Dropout (0.4) ở tầng phân loại cuối cùng để giảm hiện tượng học vẹt (Overfitting).
4. **Bản đồ nhiệt giải thích (Explainable AI - XAI):** Sử dụng thuật toán **Grad-CAM** để khoanh vùng các vị trí trên phổi mà AI dựa vào đó để đưa ra quyết định, giúp bác sĩ hiểu được lý do tại sao AI đưa ra kết luận bệnh.

---

## 3. Dataset – Dữ liệu sử dụng

* **Nguồn dữ liệu:** Tập dữ liệu mở *Chest X-Ray Images (Pneumonia)* được thu thập từ Trung tâm Y tế Phụ sản và Nhi khoa Quảng Châu.
* **Quy mô:** Tổng cộng 5,856 ảnh X-quang ngực thẳng dạng kỹ thuật số (đối tượng nghiên cứu là phim chụp của bệnh nhi từ 1 đến 5 tuổi).
* **Các nhãn phân loại (3 Classes):** `Normal` (Bình thường), `Bacterial Pneumonia` (Viêm phổi do vi khuẩn), và `Virus Pneumonia` (Viêm phổi do virus).
* **Cấu hình:** Chia theo tỷ lệ 80% Train và 20% Test. Kích thước ảnh đầu vào được chuẩn hóa về mức `224x224` pixel.

---

## 4. Evaluation & Results – Thước đo và Kết quả

#### Các chỉ số đánh giá:
* **Accuracy:** Độ chính xác tổng thể trên cả 3 nhóm nhãn.
* **Sensitivity / Recall (Độ nhạy):** Thước đo quan trọng nhất trong y tế, đo lường tỷ lệ AI tìm ra được bao nhiêu ca bệnh trên tổng số ca mắc bệnh thực tế (tránh bỏ sót bệnh nhân).
* **F1-Score & Tốc độ suy luận (Inference Latency).**

#### Bảng hiệu năng thực nghiệm:

| Mô hình | Accuracy | Sensitivity (Recall) | F1-Score | Tốc độ suy luận (giây/ảnh) |
| :--- | :--- | :--- | :--- | :--- |
| **Custom CNN (5 lớp)** | 84.2% | 81.5% | 82.8% | **0.015 giây** |
| **ResNet50 (Fine-tuned)** | **94.6%** | **96.2%** | **95.1%** | 0.085 giây |

#### Phát hiện quan trọng:
* Mô hình **ResNet50 đạt độ nhạy lên tới 96.2%**, kiểm soát tỷ lệ bỏ sót bệnh nhân mắc viêm phổi xuống mức dưới 4%.
* Hệ thống hiển thị trực quan **Grad-CAM** khoanh vùng chính xác các vùng mô phổi bị đông đặc (consolidation), tạo được độ tin cậy cao khi các bác sĩ đối chiếu lâm sàng.

---

## 5. Limitations – Hạn chế của bài báo

1. **Dữ liệu bị giới hạn độ tuổi:** Tập dữ liệu gốc hoàn toàn là trẻ em từ 1-5 tuổi. Cấu trúc xương và mật độ mô phổi của người trưởng thành hoặc người già có sự khác biệt rất lớn, khiến mô hình bị sụt giảm độ chính xác nghiêm trọng khi thử nghiệm trên các nhóm đối tượng này.
2. **Thiếu thông tin ngữ cảnh lâm sàng (Clinical Data):** Mô hình AI chỉ phân tích độc lập hình ảnh trực quan mà không kết hợp với bệnh án văn bản của bệnh nhân (như chỉ số sốt, số ngày ho, số lượng bạch cầu), làm giảm khả năng chẩn đoán chính xác ở các ca bệnh phức tạp.

---

## 6. Relevance & Possible Improvements – Định hướng cải tiến

* **Tính liên quan đến nghiên cứu:** Bài báo là một baseline (điểm tựa) tốt về cách xử lý hình ảnh phi cấu trúc có độ nhiễu cao, đồng thời giới thiệu giải pháp AI có thể giải thích được (Grad-CAM) - một yếu tố rất cần thiết cho các hệ thống phần mềm có sự tương tác giữa người và máy.
* **Gợi ý cải tiến:** Hướng phát triển tiềm năng là nâng cấp bài toán này thành **Multimodal AI (AI đa phương thức)**. Module nhận diện sẽ nhận song song 2 luồng đầu vào: **Ảnh chụp X-quang** (xử lý qua ResNet) + **Bệnh án dạng chữ/số** (xử lý qua BERT hoặc bảng dữ liệu). Việc gộp đặc trưng (Feature Fusion) từ cả ảnh và chữ sẽ giúp AI đưa ra chẩn đoán chính xác và toàn diện như một hội đồng y khoa thực thụ.
