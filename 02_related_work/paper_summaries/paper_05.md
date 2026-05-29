
## Citation

**Tên bài:** Product Tagging with Convolutional Neural Networks (CNN)  
**Tác giả:** Kunal Parkhade  
**Năm:** 2024  
**Nguồn:** GitHub Repository  
**DOI/Link:** https://github.com/KunalParkhade/product-tagging-cnn

## Problem (Vấn đề bài báo giải quyết)

Bài báo giải quyết 2 vấn đề chính:

1. **Gán nhãn (tagging) sản phẩm THỦ CÔNG RẤT TỐN KIỆM THỜI GIAN**
   - Ví dụ: Có 10,000 sản phẩm trên trang web
   - Nhân viên phải tự nhìn từng ảnh và thêm tags: "áo thun", "nam", "cotton", "xanh"
   - Làm thủ công mất HÀNG TUẦN, dễ sai sót, không đồng đều [web:2]

2. **Số lượng sản phẩm TĂNG LIÊN TỤC**
   - Trang web thêm sản phẩm mới mỗi ngày
   - Không thể theo kịp nếu làm thủ công
   - Cần hệ thống TỰ ĐỘNG gán nhãn ngay khi sản phẩm lên [web:2]

## Method (Phương pháp/Làm như thế nào)

Bài báo xây dựng **hệ thống AI tự động gán nhãn ảnh sản phẩm** bằng CNN:

### Quy trình 4 bước:

#### 1. Dataset Preparation (Chuẩn bị dữ liệu)
- Load ảnh sản phẩm từ folder
- Preprocess: resize về 224x224, normalize màu
- Chia train/test: 80% train, 20% test [web:2]

#### 2. Building the CNN (Xây dựng mạng CNN)
**Kiến trúc CNN đơn giản:**

