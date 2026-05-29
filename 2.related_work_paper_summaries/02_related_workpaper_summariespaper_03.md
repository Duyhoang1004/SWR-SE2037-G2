# Paper Summary – Optimizing E-Commerce Product Classification Using Transfer Learning

---

## Citation

| Trường | Thông tin |
|---|---|
| **Tên bài báo** | Optimizing E-Commerce Product Classification Using Transfer Learning |
| **Tác giả** | Rashmeet Kaur Khanuja |
| **Năm công bố** | 2019 (Spring) |
| **Loại tài liệu** | Master's Project – CS 298 |
| **DOI** | https://doi.org/10.31979/etd.egyw-ktc5 |
| **Link** | https://scholarworks.sjsu.edu/etd_projects/679 |

---

## 1. Research Objective – Mục tiêu nghiên cứu

Nghiên cứu này xuất phát từ một bài toán thực tiễn mà bất kỳ sàn thương mại điện tử
lớn nào cũng phải đối mặt: làm thế nào để tự động phân loại hàng triệu sản phẩm vào
đúng danh mục, trong khi các merchant đến từ mọi nơi và không ai dùng chung một hệ
thống phân loại nhất quán?

Mục tiêu cụ thể của tác giả có hai tầng rõ ràng:

- **Tầng kỹ thuật:** Áp dụng Transfer Learning (cụ thể là VGG-16 pre-trained trên
  ImageNet) để phân loại ảnh sản phẩm TMĐT, và so sánh hiệu quả với CNN huấn luyện
  từ đầu (from scratch) về cả độ chính xác lẫn thời gian huấn luyện.

- **Tầng ứng dụng:** Xây dựng một pipeline phân loại ảnh sản phẩm thực tế, trong đó
  mỗi category sẽ có một model riêng theo chiến lược "One vs All" – thay vì cố gắng
  giải quyết tất cả trong một model duy nhất.

Đây không phải một nghiên cứu đề xuất kiến trúc model mới. Điểm nhấn của bài là
chứng minh rằng Transfer Learning có thể rút ngắn đáng kể thời gian và chi phí tính
toán, trong khi vẫn duy trì – thậm chí cải thiện – độ chính xác so với CNN truyền thống.

---

## 2. Main Problem – Vấn đề nghiên cứu

Bài báo chỉ ra một chuỗi vấn đề liên tiếp nhau trong hệ thống phân loại sản phẩm
TMĐT hiện tại:

| # | Vấn đề | Mô tả chi tiết |
|---|---|---|
| 1 | **Thiếu chuẩn hóa taxonomy** | Mỗi merchant có hệ thống phân loại riêng. Khi hàng ngàn merchant bán trên cùng một sàn, taxonomy của họ xung đột nhau, dẫn đến sản phẩm bị gán nhầm danh mục. Tác giả minh họa bằng ví dụ thực tế: tìm "cotton" trong Beauty lại ra kết quả là kayak. |
| 2 | **Text-based classification không đáng tin** | Các phương pháp phân loại dựa trên văn bản (tên, mô tả sản phẩm) dễ thất bại khi merchant nhập thiếu thông tin, dùng từ khóa sai, hoặc cố tình nhồi nhét từ khóa không liên quan để tăng khả năng hiển thị. Ngoài ra, "Asus Laptop with Battery" và "Asus Laptop Battery" có thể bị xử lý giống nhau dù một cái là laptop và một cái là phụ kiện. |
| 3 | **CNN from scratch quá tốn tài nguyên** | Chỉ với 3,039 ảnh, CNN truyền thống đã mất hơn 3 giờ để huấn luyện, và kết quả lại bị overfit nặng – train accuracy đạt ~90% nhưng validation accuracy tụt dần khi số epoch tăng. |
| 4 | **Thiếu dữ liệu ở cấp độ category** | Dù tổng số sản phẩm trên sàn TMĐT có thể lên đến hàng triệu, nhưng khi chia nhỏ ra từng category cụ thể thì số lượng ảnh mỗi loại thường không đủ để train một CNN hiệu quả từ đầu. |

---

## 3. Proposed Method – Phương pháp đề xuất

Tác giả đề xuất framework gồm hai giai đoạn, được triển khai thực tế bằng Python 3 +
Keras + TensorFlow backend trên máy cá nhân (i3, 8GB RAM, AMD Radeon GPU).

### 3.1. Lựa chọn model nguồn: VGG-16

VGG-16 được chọn làm pre-trained model vì ba lý do chính:

- Được huấn luyện trên ImageNet – bộ dữ liệu ảnh lớn nhất thế giới với hàng triệu
  ảnh thuộc 1,000 categories.
- Kiến trúc đơn giản, dễ hiểu, dễ triển khai hơn so với GoogleNet hay ResNet.
- Hội tụ nhanh và ổn định hơn các kiến trúc phức tạp hơn.

Kiến trúc gốc của VGG-16 gồm 16 lớp: 13 convolutional layers (dùng bộ lọc 3×3) và
3 fully connected layers.

### 3.2. Chiến lược Transfer Learning

| Bước | Thao tác | Chi tiết |
|---|---|---|
| **Freeze** | Giữ nguyên trọng số 5 convolutional blocks đầu | Các block này đã học được đặc trưng tổng quát (cạnh, góc, texture, hình dạng) từ ImageNet – không cần train lại |
| **Cắt top layers** | Loại bỏ 3 lớp cuối của VGG-16 (2 fully connected + 1 dense 1000 units) | Đây là phần phân loại cho 1,000 class ImageNet, không phù hợp với bài toán của chúng ta |
| **Thêm classifier mới** | Flatten → Dense(128, ReLU) → Dropout(0.5) → Dense(1, Sigmoid) | Phân loại nhị phân (binary) theo chiến lược One vs All |
| **Augmentation** | Rescale, zoom, rotation, width/height shift, shear, horizontal flip | Tăng lượng dữ liệu train, giúp model tổng quát hóa tốt hơn |
| **Optimizer** | Adam (lr=1e-5 cho Appliances; default cho các category khác) | Binary cross-entropy loss |

### 3.3. Chiến lược phân loại: One vs All

Đây là điểm độc đáo nhất của bài. Thay vì train một model duy nhất cho tất cả 5
categories (multi-class), tác giả xây dựng **một model riêng cho mỗi category**:

- **Class 0:** Ảnh thuộc category đang xét (ví dụ: Appliances)
- **Class 1:** Ảnh từ tất cả các category còn lại gộp lại (Electronics + Furniture +
  Toys + ...)

Quyết định này xuất phát từ thực nghiệm: khi thử multi-class TL (tất cả classes cùng
lúc), accuracy chỉ đạt 35.9% – quá tệ để sử dụng thực tế.

---

## 4. Dataset Used – Bộ dữ liệu sử dụng

| Thuộc tính | Chi tiết |
|---|---|
| **Nguồn** | Ảnh sản phẩm thu thập từ một sàn TMĐT (không công bố tên) bằng web crawler tự viết (Selenium + BeautifulSoup) |
| **Tổng số ảnh** | ~17,500 ảnh |
| **Số categories** | 5: Appliances, Electronics, Furniture, Toys, và một category khác |
| **Phân bổ train** | Appliances ~1,698 / Electronics ~2,951 / Furniture ~1,548 / Toys ~2,004 ảnh |
| **Test samples** | ~900 ảnh/category |
| **Subset Phase 1** | 3,039 ảnh (train) + 600 ảnh (validation) – dùng để so sánh CNN vs TL |
| **Full Phase 2** | ~8,201 ảnh train + ~909 ảnh validation |
| **Kích thước ảnh** | Resize về 200×200 pixels, normalize /255 |
| **Lưu trữ** | Cassandra database kết nối qua Python API |
| **Cấu trúc thư mục** | `data/train/<category>/train_images` |

Một điểm đáng chú ý: vì ảnh trên website được load động qua AJAX calls nên không
thể lấy trực tiếp bằng HTML scraping thông thường. Tác giả phải dùng Selenium để
điều khiển trình duyệt, sau đó mới dùng BeautifulSoup để trích xuất URL ảnh.

---

## 5. Baselines Compared – Mô hình so sánh

| Model | Mô tả | Mục đích |
|---|---|---|
| **Traditional CNN (from scratch)** | 5 blocks Conv+Activation+Pooling, Dense(64) → Dropout(0.5) → Dense(1, Sigmoid); optimizer RMSprop; binary cross-entropy | Baseline chính để chứng minh TL vượt trội |
| **VGG-16 Transfer Learning (One vs All)** | Model đề xuất chính | So sánh với CNN |
| **VGG-16 TL – Multi-class** | Train tất cả 5 classes cùng lúc trong một model | Thử nghiệm bổ sung; bị loại do accuracy quá thấp (35.9%) |

---

## 6. Evaluation Metrics – Thước đo đánh giá

| Metric | Ý nghĩa | Lý do sử dụng |
|---|---|---|
| **Accuracy** | Tỉ lệ phân loại đúng tổng thể (train + validation) | Thước đo chính để so sánh các model |
| **Loss** | Binary cross-entropy loss qua từng epoch | Giám sát quá trình học, phát hiện overfitting sớm |
| **Training Time** | Tổng thời gian huấn luyện (giờ/phút) | Chứng minh TL tiết kiệm tài nguyên đáng kể |
| **Accuracy/Loss vs Epoch graphs** | Đồ thị trực quan hóa quá trình học | Quan sát overfitting, underfitting, sự hội tụ |
| **Binary prediction test** | Kiểm tra model dự đoán đúng class 0 (target) hay class 1 (others) | Đánh giá định tính trên ảnh test thực tế |

*Lưu ý: Bài báo không sử dụng Precision, Recall, hay F1-score – đây là một điểm thiếu
sót so với các tiêu chuẩn nghiên cứu hiện đại.*

---

## 7. Main Results – Kết quả chính

### 7.1. Phase 1: CNN from scratch vs. VGG-16 Transfer Learning (subset 3,039 ảnh)

| Model | Accuracy (avg) | Training Time | Ghi chú |
|---|---|---|---|
| Traditional CNN | ~79% (train) | **> 3 giờ** | Overfit nặng – val accuracy giảm dần theo epoch |
| VGG-16 Transfer Learning | **~85%** | **~16.96 phút** | Ổn định hơn; ít overfit; nhanh hơn ~10 lần |

### 7.2. Phase 2: Các chiến lược phân loại trên full dataset

| Chiến lược | Model | Accuracy | Ghi chú |
|---|---|---|---|
| Multi-class (tất cả cùng lúc) | VGG-16 TL | **35.9%** | Thất bại hoàn toàn – quá thấp để dùng thực tế |
| One vs All (model riêng/category) | VGG-16 TL | **~89% trung bình** | Kết quả tốt nhất; minh họa rõ qua Appliance model |

### 7.3. Nhận xét tổng hợp

Transfer Learning vượt trội CNN truyền thống trên cả hai chiều:

- **Tốc độ:** nhanh hơn khoảng 10 lần (16 phút so với 3+ giờ)
- **Chất lượng:** accuracy cao hơn và ổn định hơn (không overfit)
- **Chiến lược One vs All** là chìa khóa để đạt 89% – không phải multi-class

---

## 8. Limitations – Hạn chế

| # | Hạn chế | Phân tích |
|---|---|---|
| 1 | **Chỉ dùng hình ảnh** | Bỏ qua toàn bộ thông tin văn bản (tên sản phẩm, mô tả, tags) – trong khi thực tế cả hai nguồn thông tin đều có giá trị |
| 2 | **Phạm vi nhỏ – 5 categories** | Chỉ phân loại ở cấp top-level. Trong thực tế, Electronics còn có Laptops, TVs, Tablets... – bài báo chưa đụng đến sub-categories |
| 3 | **Dataset không công khai** | Thu thập bằng crawler riêng, không chia sẻ. Các nghiên cứu sau không thể dùng lại dataset này để so sánh công bằng |
| 4 | **Hardware yếu** | Chỉ dùng máy i3 + 8GB RAM + AMD Radeon. Không thể thử nghiệm với dataset lớn hơn hoặc kiến trúc phức tạp hơn |
| 5 | **One vs All không scalable** | Nếu có 100 categories thì cần 100 model riêng biệt. Chi phí lưu trữ, maintain và inference sẽ tăng tuyến tính |
| 6 | **Không so sánh nhiều model TL** | Chỉ thử VGG-16. Không có benchmark với InceptionV3, ResNet50, MobileNet, hay EfficientNet |
| 7 | **Thiếu metric đánh giá toàn diện** | Không có Precision, Recall, F1-score, confusion matrix. Accuracy đơn thuần có thể gây hiểu nhầm nếu dataset mất cân bằng |

---

## 9. Future Work – Hướng phát triển

Tác giả đề xuất hai hướng mở rộng chính:

**Hướng 1 – Phân loại sâu hơn (sub-categories):**
Hiện tại, "Electronics" được xử lý như một khối đồng nhất. Bước tiếp theo là đi sâu
vào từng tầng con: Electronics → Laptops / TVs / Tablets / Phones... Mỗi sub-category
sẽ có model riêng theo cùng chiến lược One vs All.

**Hướng 2 – Kết hợp với hệ thống gợi ý sản phẩm (Recommender):**
Sau khi sản phẩm đã được phân loại đúng category, feature vector từ VGG-16 có thể
được tái sử dụng để tìm các sản phẩm tương tự trong cùng danh mục. Điều này có thể
được triển khai real-time để hiển thị "sản phẩm liên quan" khi user đang xem một mặt
hàng.

---

## 10. Possible Research Gaps – Khoảng trống nghiên cứu

Đây là phần quan trọng nhất khi nhóm nghiên cứu muốn đóng góp điểm mới so với bài
báo này:

| # | Research Gap | Gợi ý cải tiến |
|---|---|---|
| 1 | **Thiếu multimodal input** | Kết hợp ảnh + văn bản mô tả sản phẩm (VGG-16 + BERT/TF-IDF) → multimodal fusion để tận dụng cả hai nguồn thông tin |
| 2 | **Chưa benchmark đa dạng model TL** | So sánh toàn diện: VGG-16 vs InceptionV3 vs MobileNet vs EfficientNet trên cùng bộ dữ liệu |
| 3 | **One vs All không scalable** | Nghiên cứu Hierarchical Classification (phân loại theo cây phân cấp) để xử lý hàng trăm categories mà không cần hàng trăm model |
| 4 | **Không có user/expert evaluation** | Thêm khảo sát từ phía seller và buyer về chất lượng phân loại; đo lường thời gian tiết kiệm so với phân loại thủ công |
| 5 | **Fine-tuning chưa được khảo sát** | Bài chỉ freeze hoàn toàn conv blocks. Chưa thử unfreeze từng block để tìm điểm cân bằng tối ưu giữa feature reuse và domain adaptation |
| 6 | **Dataset chuẩn hóa** | Dùng dataset công khai (Amazon Product Dataset, Flipkart Kaggle dataset) thay vì tự thu thập, giúp so sánh công bằng với các bài báo khác |

---

## Relevance to Our Topic – Liên quan đến đề tài nhóm

Bài báo này có mức liên quan **cao** nếu đề tài của nhóm liên quan đến phân loại ảnh
sản phẩm, hệ thống gợi ý, hoặc tự động hóa trong thương mại điện tử. Cụ thể:

- **Pipeline tham khảo được:** Thu thập dữ liệu → Augmentation → Transfer Learning →
  Binary classification (One vs All) là một quy trình hoàn chỉnh mà nhóm có thể mở
  rộng.

- **Baseline rõ ràng:** CNN from scratch (accuracy ~79%, >3 giờ) là baseline tự nhiên
  để nhóm chứng minh sự cải tiến của mình.

- **Gap rõ ràng để khai thác:** Bài không dùng văn bản, không so sánh nhiều model TL,
  không đánh giá từ góc độ người dùng, và không xử lý sub-categories – tất cả đều là
  cơ hội nghiên cứu thực sự cho nhóm.