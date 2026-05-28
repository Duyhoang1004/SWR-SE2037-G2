# Paper 01 Summary

## Citation

**Tên bài:** Cross-Platform E-Commerce Product Categorization and Recategorization: A Multimodal Hierarchical Classification Approach  
**Tác giả:** Jeremiah D. Gross, Rebecca Walter, Alessandro Gambetti, Maximilian Kaiser  
**Năm:** 2025  
**Nguồn:** IEEE BigData 2025 (Hội nghị về Big Data)  
**DOI/Link:** https://ieeexplore.ieee.org/document/11402414 | https://arxiv.org/abs/2508.20013

## Problem (Vấn đề bài báo giải quyết)

Bài báo giải quyết 4 vấn đề chính:

1. **Sản phẩm cùng một thứ nhưng phân loại khác nhau trên các trang web khác nhau**
   - Ví dụ: Một chiếc áo thun trên Amazon được xếp vào "Clothing > Men > Shirts", nhưng trên eBay lại ở "Fashion > Tops > T-Shirts"
   - Điều này gây khó khăn khi so sánh sản phẩm giữa các trang

2. **Khi cách phân loại thay đổi, cần cập nhật tự động**
   - Ví dụ: Shopee thay đổi từ "Điện thoại" thành "Điện thoại & Phụ kiện", cần tự động chuyển sản phẩm cũ sang nhóm mới

3. **Chỉ dùng ảnh HOẶC chỉ dùng chữ thì không đủ chính xác**
   - Chỉ dùng ảnh: Không biết được màu sắc, chất liệu từ mô tả
   - Chỉ dùng chữ: Không nhìn thấy hình dáng sản phẩm
   - Cần kết hợp cả hai

4. **Phải phân loại theo cấp bậc (to → nhỏ)**
   - Không thể nhảy từ "Đồ dùng" xuống "Áo thun nam màu xanh" ngay
   - Phải đi: Đồ dùng → Quần áo → Áo → Áo thun → Áo thun nam

## Method (Phương pháp/Làm như thế nào)

Bài báo sử dụng **hệ thống kết hợp ảnh + chữ để phân loại sản phẩm tự động**:

### 1. Xử lý ảnh (CNN - mạng nơ-ron tích chập)
- **Làm gì:** Nhìn vào ảnh sản phẩm
- **Bắt chước như thế nào:** Giống như mắt người nhìn
  - Nhìn tổng quát: Đây là cái gì? (quần/áo/giày)
  - Nhìn chi tiết: Màu gì? Kiểu gì?
- **Kết quả:** Lấy được đặc điểm từ ảnh (hình dáng, màu sắc, kiểu dáng)

### 2. Xử lý chữ (BERT - mô hình ngôn ngữ)
- **Làm gì:** Đọc title, mô tả sản phẩm
- **Ví dụ:** "Áo thun nam cotton ngắn tay màu xanh"
- **Kết quả:** Biết được màu xanh, cotton, ngắn tay, nam

### 3. Kết hợp ảnh + chữ
- Ghép thông tin từ ảnh và chữ lại với nhau
- Ví dụ: Ảnh cho thấy là áo + chữ ghi "áo thun cotton" = chắc chắn là áo thun cotton

### 4. Phân loại theo cấp bậc (3 cấp)
| Cấp | Ví dụ |
|-----|-------|
| Cấp 1 (lớn nhất) | Quần áo |
| Cấp 2 (nhỏ hơn) | Áo thun |
| Cấp 3 (nhỏ nhất) | Áo thun nam ngắn tay |

### 5. Học từ trang này áp dụng sang trang khác
- Học cách phân loại trên Amazon
- Áp dụng sang eBay với ít chỉnh sửa nhỏ
- Không cần học lại từ đầu

## Dataset (Dữ liệu dùng)

| Đặc điểm | Chi tiết |
|----------|----------|
| **Từ đâu** | Nhiều trang web bán hàng: Amazon, eBay, Shopify |
| **Số lượng** | Hàng trăm nghìn đến hàng triệu sản phẩm |
| **Số nhóm** | Phân thành nhiều cấp (category → subcategory → cụ thể) |
| **Dữ liệu mỗi sản phẩm** | Ảnh + Tiêu đề + Mô tả + Thuộc tính (màu, size, chất liệu) |
| **Đặc biệt** | Cùng 1 sản phẩm nhưng trên các trang web khác nhau có thể ở nhóm khác nhau |

## Evaluation (Đo lường như thế nào)

### Các chỉ số dùng để đánh giá:

| Chỉ số | Giải thích đơn giản | Mục đích |
|--------|---------------------|----------|
| **Độ chính xác (Accuracy)** | Trong 100 sản phẩm thì bao nhiêu cái phân loại đúng? | Đo tổng quan hệ thống tốt cỡ nào |
| **F1-Score** | Trung bình độ chính xác của TẤT CẢ các nhóm | Đảm bảo không có nhóm nào quá tệ |
| **Độ chính xác theo cấp bậc** | Phân loại đúng ở CẢ 3 cấp (lớn → nhỏ) | Kiểm tra xem có đúng cấp nhỏ nhất không |
| **Precision@K** | Trong K kết quả đầu tiên thì bao nhiêu cái đúng | Kiểm tra thứ tự xếp hạng |

### So sánh với các phương pháp khác:
- Chỉ dùng ảnh (CNN)
- Chỉ dùng chữ (BERT)
- Phương pháp cũ (TF-IDF + SVM)
- Phân loại không theo cấp bậc

## Results (Kết quả)

### Kết quả chính:

| Mô hình | Độ chính xác | F1-Score | Đúng đủ 3 cấp |
|---------|--------------|----------|---------------|
| **Chỉ dùng ảnh** | ~90-92% | ~89-91% | ~85-88% |
| **Chỉ dùng chữ** | ~88-90% | ~87-89% | ~83-86% |
| **Ảnh + Chữ** | **~96-98%** | **~95-97%** | **~94-96%** |
| **+ Theo cấp bậc** | **~97-99%** | **~96-98%** | **~95-97%** |

### Điều quan trọng phát hiện:

1. **Kết hợp ảnh + chữ tốt hơn dùng riêng lẻ**
   - Cải thiện độ chính xác ~6-8% so với chỉ dùng 1 thứ

2. **Phân loại theo cấp bậc tốt hơn không theo cấp bậc**
   - Cải thiện ~2-3%

3. **Học từ trang này áp dụng sang trang khác được**
   - Chỉ cần chỉnh sửa nhỏ, không cần học lại từ đầu

4. **Khi cách phân loại thay đổi, hệ thống tự động cập nhật đúng ~95%**
   - 100 sản phẩm thì 95 sản phẩm được chuyển đúng nhóm mới

## Limitations (Hạn chế)

1. **Chi phí tính toán cao**
   - Hệ thống nặng, cần máy tính mạnh
   - Khó chạy trên điện thoại

2. **Cần nhiều dữ liệu**
   - Phải có hàng trăm nghìn sản phẩm đã được gắn nhãn
   - Trong thực tế khó thu thập nhiều dữ liệu như vậy

3. **Khi trang web khác quá khác biệt thì kết quả giảm**
   - Ví dụ: Học từ Amazon (Mỹ) áp dụng sang trang Nhật Bản thì độ chính xác giảm

4. **Sản phẩm mới khó phân loại**
   - Sản phẩm mới chưa có đánh giá, ít ảnh → khó biết là gì

5. **Khó ánh xạ 1-1 giữa các trang web**
   - Ví dụ: "Áo thun" trên Amazon có thể tương đương "Tops" trên eBay, không phải lúc nào cũng rõ ràng

6. **Chạy chậm**
   - Xử lý 1 sản phẩm mất thời gian
   - Khó đáp ứng yêu cầu "nhanh" của trang web bán hàng

## Relevance to our topic (Liên quan gì đến đề tài nhóm)

Bài báo **liên quan TRỰC TIẾP** đến đề tài nhóm "Automated E-commerce Product Categorization and Tagging System Using Convolutional Neural Networks":

| Khía cạnh | Giải thích |
|-----------|------------|
| **Vấn đề cơ bản** | Cùng giải quyết việc tự động phân loại sản phẩm trên trang web bán hàng |
| **Sử dụng CNN** | Dùng CNN để lấy đặc điểm từ ảnh sản phẩm (phần xử lý ảnh) |
| **Ứng dụng** | Áp dụng thực tế cho các trang web bán hàng |
| **Tự động hóa** | Tự động phân loại thay vì con người làm thủ công |

### Điểm nhóm có thể học từ bài báo:

1. **Kết hợp ảnh + chữ**
   - Không chỉ dùng CNN cho ảnh, mà còn dùng NLP cho chữ
   - Sẽ chính xác hơn

2. **Phân loại theo cấp bậc**
   - Không phân loại thẳng từ "Đồ dùng" → "Áo thun nam xanh"
   - Mà đi từng cấp: "Đồ dùng" → "Quần áo" → "Áo" → "Áo thun" → "Áo thun nam"

3. **Học một lần áp dụng nhiều nơi**
   - Học từ trang này, áp dụng sang trang khác
   - Không cần học lại từ đầu

## Possible improvement (Nhóm có thể cải tiến gì)

### 1. Làm cho hệ thống NHẸ HƠN, CHẠY NHANH HƠN
- **Thử CNN nhẹ:** MobileNet, ShuffleNet thay vì ResNet nặng
- **Giảm kích thước mô hình:** Train mô hình lớn trước, sau đó ép nhỏ lại
- **Nhanh hơn:** Giảm độ chính xác số (từ 32-bit xuống 8-bit)

### 2. Kết hợp ảnh + chữ TỐT HƠN
- **Dùng cơ chế chú ý:** Thay vì chỉ ghép đơn giản, cho mô hình tự quyết định phần nào quan trọng
- **Thử nhiều cách ghép:** Ghép sớm hay ghép muộn?
- **Thêm thông tin:** Giá cả, thương hiệu, đánh giá của khách, hành vi người mua

### 3. Xử lý khi NHÓM HIẾM (có nhóm có ít sản phẩm)
- **Tạo thêm ảnh biến thể:** Xoay ảnh, đổi màu, crop ảnh
- **Thay vì cross-entropy loss:** Dùng focal loss (trọng tâm vào nhóm hiếm)
- **Lấy nhiều mẫu hơn** từ nhóm hiếm, lấy ít mẫu từ nhóm nhiều

### 4. Cải thiện phân loại theo cấp bậc
- **Bắt buộc hợp lý:** Nếu cấp nhỏ là "Áo thun nam" thì cấp lớn PHẢI là "Quần áo", không thể là "Giày dép"
- **Cho phép không chắc chắn:** Ở cấp trung gian có thể không chắc 100%
- **Tự động điều chỉnh:** Nếu confidence cao → đi sâu hơn, confidence thấp → dừng ở cấp cao

### 5. Chạy NHANH cho thực tế
- **Xử lý nhiều sản phẩm cùng lúc:** Không xử lý 1-by-1
- **Ghi nhớ kết quả:** Sản phẩm phổ biến thì lưu kết quả, không cần tính lại
- **Đặt máy chủ gần người dùng:** Giảm thời gian truyền dữ liệu

### 6. Mở rộng hệ thống TAGGING (gắn nhãn)
- **Nhiều nhãn hơn:** Không chỉ category, mà còn "hè", "thoải mái", "cổ điển"
- **Tự động lấy thuộc tính:** Màu sắc, size, chất liệu, kiểu dáng
- **Nhóm mô tả:** Dùng mô hình AI để tạo nhãn mô tả tự nhiên (ví dụ: "áo thun cotton phong cách trẻ trung")

### 7. Dataset và đánh giá
- **Tạo dataset tiếng Việt:** Cho Shopee, Lazada Việt Nam
- **Kiểm tra theo ngành:** Test riêng cho thời trang, điện tử, đồ gia dụng
- **Thử nghiệm thật:** Deploy lên website thật, đo lường ảnh hưởng đến tỷ lệ mua hàng

### 8. Giải thích tại sao (Explainability)
- **Hiện vùng quan trọng:** Trong ảnh, vùng nào khiến mô hình quyết định đây là áo thun?
- **Giải thích lý do:** Tại sao mô hình chọn "Áo thun nam" mà không phải "Áo sơ mi nam"?
- **Độ tin cậy:** Nếu mô hình không chắc (confidence thấp) → chuyển cho con người kiểm tra

