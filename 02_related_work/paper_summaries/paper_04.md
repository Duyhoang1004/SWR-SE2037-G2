
## Citation

**Tên bài:** Optimizing E-Commerce Product Classification Using Transfer Learning  
**Tác giả:** Rashmeet Kaur Khanuja  
**Năm:** 2019  
**Nguồn:** Master's Projects, San Jose State University  
**DOI/Link:** https://scholarworks.sjsu.edu/etd_projects/679/ | DOI: 10.31979/etd.egyw-ktc5

## Problem (Vấn đề bài báo giải quyết)

Bài báo giải quyết 3 vấn đề chính:

1. **Phân loại sản phẩm thủ công rất TỐN THỜI GIAN**
   - Trang web bán hàng có hàng triệu sản phẩm
   - Nhân viên phải tự nhìn và xếp từng sản phẩm vào nhóm (quần/áo/giày)
   - Mất hàng tuần, dễ nhầm lẫn

2. **Sản phẩm mới thêm vào HÀNG NGÀY**
   - Không thể theo kịp nếu làm thủ công
   - Cần hệ thống tự động phân loại ngay khi sản phẩm mới lên

3. **Train mô hình CNN từ đầu RẤT CHẬM**
   - CNN truyền thống cần hàng HOURS để train
   - Độ chính xác không cao
   - Cần giải pháp nhanh hơn nhưng vẫn chính xác

## Method (Phương pháp/Làm như thế nào)

Bài báo so sánh **2 phương pháp**:

### 1. CNN truyền thống (Train từ đầu)
- **Cách làm:** Học từ số 0, không dùng kiến thức có sẵn
- **Nhược điểm:** 
  - Mất 2.5+ giờ để train
  - Độ chính xác thấp (chỉ ~51%)
  - Cần nhiều dữ liệu và computational power

### 2. Transfer Learning (Học chuyển giao) - PHƯƠNG PHÁP TỐT HƠN
**Ý tưởng:** Thay vì học từ đầu, dùng mô hình đã học sẵn trên hàng triệu ảnh (ImageNet), chỉ "tinh chỉnh" cho sản phẩm e-commerce

**Quy trình 4 bước:**

1. **Thu thập dữ liệu**
   - Dataset: Flipkart e-commerce (5,000 sản phẩm)
   - 5 nhóm: Quần áo nam, Quần áo nữ, Giày, Phụ kiện, Hương liệu

2. **Xử lý ảnh**
   - Resize ảnh về 224x224 pixel (chuẩn cho CNN)
   - Normalize màu sắc (chuẩn hóa)

3. **Train 2 phương pháp**
   - CNN truyền thống: Học từ đầu
   - Transfer Learning: Dùng mô hình pre-trained (VGG19, InceptionV3, ResNet50, MobileNet)

4. **So sánh**
   - Đo độ chính xác (accuracy)
   - Đo thời gian train
   - Đo thời gian dự đoán 1 ảnh

## Dataset (Dữ liệu dùng)

| Đặc điểm | Chi tiết |
|----------|----------|
| **Nguồn** | Kaggle: Flipkart E-commerce Products Dataset [web:50] |
| **Số lượng** | 5,000 sản phẩm |
| **Số nhóm** | 5 nhóm: Men's Clothing, Women's Clothing, Shoes, Accessories, Fragrance [web:50] |
| **Kích thước ảnh** | 224x224 pixel [web:50] |
| **Chia train/test** | Không ghi rõ, thường 80% train, 20% test |

## Evaluation (Đo lường như thế nào)

### Các chỉ số dùng:

| Chỉ số | Giải thích đơn giản |
|--------|---------------------|
| **Accuracy** | Trong 100 ảnh thì bao nhiêu ảnh phân loại đúng? [web:50] |
| **Thời gian train** | Mất bao lâu để train mô hình? (giờ/phút) [web:50] |
| **Thời gian dự đoán** | Mất bao lâu để phân loại 1 ảnh? (giây/ảnh) [web:50] |

### So sánh:
- CNN (train từ đầu)
- Transfer Learning (VGG19, InceptionV3, ResNet50, MobileNet)

## Results (Kết quả)

### Kết quả chính:

| Phương pháp | Độ chính xác | Thời gian train | Thời gian dự đoán |
|-------------|--------------|-----------------|-------------------|
| **CNN (train từ đầu)** | 51% | >2.5 giờ | Chậm [web:50] |
| **Transfer Learning** | **65-85%** | **<1 giờ** | **Nhanh** [web:50] |

### ĐIỀU QUAN TRỌNG PHÁT HIỆN:

1. **Transfer Learning TỐT hơn nhiều**
   - Accuracy: 51% (CNN) → 85% (Transfer Learning)
   - Cải thiện **34%** độ chính xác [web:50]

2. **Train NHANH hơn**
   - Từ 2.5+ giờ → <1 giờ [web:50]

3. **MobileNet là lựa chọn TỐT NHẤT**
   - Độ chính xác cao (85%)
   - Thời gian dự đoán NHANH NHẤT
   - Phù hợp deploy thực tế [web:2]

## Limitations (Hạn chế)

1. **Dataset NHỎ**
   - Chỉ 5,000 sản phẩm, 5 nhóm
   - Trang web thật có hàng triệu sản phẩm, hàng trăm nhóm [web:50]

2. **CHỈ có ảnh, CHƯA có chữ**
   - Không dùng title, mô tả sản phẩm
   - Nếu ảnh mờ thì không có chữ để hỗ trợ [web:50]

3. **Chưa test trên nhiều nền tảng**
   - Chỉ test trên dataset Flipkart (Ấn Độ)
   - Chưa test trên Amazon, Shopee, Lazada [web:50]

4. **Chưa so sánh nhiều mô hình transfer learning**
   - Bài báo chỉ so sánh CNN vs Transfer Learning chung chung
   - Chưa chi tiết từng mô hình (VGG19, ResNet50, v.v.) [web:50]

## Relevance to our topic (Liên quan gì đến đề tài nhóm)

Bài báo **liên quan TRỰC TIẾP** đến đề tài nhóm "Automated E-commerce Product Categorization and Tagging System Using Convolutional Neural Networks":

| Khía cạnh | Sự liên quan |
|-----------|--------------|
| **Cùng vấn đề** | Tự động phân loại sản phẩm e-commerce [web:50] |
| **Cùng dùng CNN** | Sử dụng CNN để classify sản phẩm [web:50] |
| **Transfer Learning** | Khuyên dùng transfer learning thay vì train từ đầu [web:50] |
| **MobileNet** | MobileNet là lựa chọn tốt (chính xác + nhanh) [web:2][web:50] |

### Điểm nhóm có thể học từ bài báo:

1. **Dùng transfer learning, KHÔNG train từ đầu**
   - Nhanh hơn 2.5 lần
   - Chính xác hơn 34% [web:50]

2. **Chọn MobileNet**
   - Vừa chính xác cao (85%)
   - Lại nhanh (0.101 giây/ảnh)
   - Phù hợp deploy thực tế [web:2]

3. **Chỉ cần 5,000 ảnh là train được**
   - Không cần hàng triệu ảnh như tưởng tượng [web:50]

## Possible improvement (Nhóm có thể cải tiến gì)

### 1. Kết hợp ảnh + chữ (Multimodal)
- **Bài báo CHI CỬa ảnh**, nhóm có thể thêm:
  - Title sản phẩm ("Áo thun nam cotton")
  - Mô tả ("Chất liệu cotton, ngắn tay, màu xanh")
- **Dùng BERT** để xử lý chữ, kết hợp với CNN cho ảnh
- Dự kiến cải thiện accuracy thêm 5-10%

### 2. Dataset lớn hơn, nhiều nhóm hơn
- Lấy dataset từ Shopee, Lazada Việt Nam
- Test trên 50-100 nhóm thay vì 5 nhóm
- Gần với thực tế hơn

### 3. Data augmentation
- Tạo thêm ảnh từ ảnh cũ: lật ngang/dọc, xoay, làm mờ
- Giúp mô hình học tốt hơn, không bị overfitting

### 4. Thử nhiều mô hình transfer learning hơn
- Article chỉ so sánh chung chung
- Nhóm có thể chi tiết: VGG19 vs ResNet50 vs EfficientNet vs MobileNetV3
- Chọn TỐT NHẤT cho dataset tiếng Việt

### 5. Phân loại theo cấp bậc (Hierarchical)
- Bài báo: Phân loại thẳng 5 nhóm
- Nhóm có thể: Cấp 1 (Quần áo) → Cấp 2 (Áo) → Cấp 3 (Áo thun)
- Giúp chính xác hơn, dễ giải thích hơn

### 6. Tagging mở rộng
- Không chỉ category mà còn tags: màu sắc, chất liệu, kiểu dáng
- Multi-label classification (1 sản phẩm có nhiều tags)

---

## References

[1] R. K. Khanuja, "Optimizing E-Commerce Product Classification Using Transfer Learning," Master's Projects, San Jose State University, 2019.

[2] Link: https://scholarworks.sjsu.edu/etd_projects/679/

[3] Dataset: Kaggle, "Flipkart Products," 2017.
