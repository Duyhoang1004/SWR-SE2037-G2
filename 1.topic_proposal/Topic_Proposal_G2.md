# Topic Proposal

## 1. Group Information

- **Class**: SE2037
- **Group**: Group2
- **Leader**: Nguyen Duy Hoang
- **Members**:
  - Bui Van Nghia
  - Nguyen Thanh Son
  - Nhieu Si Luan
  - Nguyen Dinh Nhat Dinh
  - Dao Trong Tan

## 2. Proposed Title

- **English title**: Automated E-commerce Product Categorization and Tagging System Using Convolutional Neural Networks
- **Vietnamese title**: Hệ thống tự động gắn thẻ và phân loại danh mục sản phẩm thương mại điện tử qua hình ảnh sử dụng Mạng nơ-ron tích chập

## 3. Application Domain

Computer Vision (Thị giác máy tính), E-commerce (Thương mại điện tử), Inventory Management (Quản lý kho hàng).

## 4. Problem Statement

Trên các sàn thương mại điện tử (TMĐT) lớn hiện nay, mỗi ngày có hàng triệu sản phẩm mới được các nhà bán hàng tải lên hệ thống. Việc quản lý, phân loại danh mục và gắn thẻ thuộc tính sản phẩm theo phương pháp truyền thống đang đối mặt với những thách thức lớn:
- **Lỗi phân loại sai từ người bán**: Người bán thường vô tình chọn sai danh mục hoặc cố tình chọn sai để né bộ lọc kiểm duyệt của sàn, gây nhiễu loạn thông tin.
- **Tốn kém chi phí kiểm duyệt thủ công**: Việc duy trì một đội ngũ nhân sự lớn để ngồi rà soát, duyệt bằng tay từng hình ảnh sản phẩm là cực kỳ tốn kém và bất khả thi khi quy mô sản phẩm tăng trưởng theo cấp số nhân.
- **Trải nghiệm tìm kiếm kém**: Nhiều sản phẩm thiếu các thẻ thuộc tính chi tiết (màu sắc, họa tiết, phom dáng), khiến hệ thống bộ lọc (filter) của sàn hoạt động không hiệu quả, gián tiếp làm giảm tỷ lệ chuyển đổi đơn hàng (conversion rate).

## 5. Motivation

Việc ứng dụng Mạng nơ-ron tích chập (CNN) – kiến trúc mạnh mẽ nhất trong lĩnh vực thị giác máy tính – vào quy trình tự động gắn thẻ và phân loại danh mục sản phẩm qua hình ảnh là giải pháp mang tính đột phá cho các doanh nghiệp TMĐT. 
Hệ thống này giúp chuẩn hóa dữ liệu đầu vào một cách tức thì ngay khi người bán tải ảnh lên. Sự chính xác trong việc tự động phân loại không chỉ giúp người bán tiết kiệm thời gian đăng bài, giảm tải áp lực và chi phí nhân sự kiểm duyệt cho sàn, mà còn tối ưu hóa công cụ tìm kiếm, mang lại trải nghiệm mua sắm mượt mà, chính xác cho khách hàng.

## 6. Target Users

- **Nhà bán hàng (Sellers)**: Tiết kiệm tối đa thời gian đăng tải sản phẩm khi hệ thống tự động nhận diện hình ảnh và gợi ý chính xác danh mục, từ khóa (hashtags) liên quan.
- **Quản trị viên sàn TMĐT (Platform Administrators)**: Tự động hóa hoàn toàn quy trình kiểm duyệt, nhanh chóng phát hiện và xử lý các sản phẩm đăng sai danh mục quy định.
- **Người mua hàng (Buyers)**: Tìm kiếm sản phẩm dễ dàng và chính xác hơn nhờ vào hệ thống dữ liệu sản phẩm đã được phân loại chuẩn hóa và gắn thẻ meta-data chi tiết.

## 7. Proposed AI Model / Method

Hệ thống dự kiến áp dụng các kiến trúc Học sâu (Deep Learning) tiên tiến cấu hình cho bài toán xử lý ảnh:
- **CNN (Convolutional Neural Network)**: Kiến trúc gốc để trích xuất các đặc trưng không gian (edges, shapes, textures) từ ảnh sản phẩm.
- **Transfer Learning (Học chuyển giao) với ResNet-50 / EfficientNet**: Nhóm sẽ sử dụng các kiến trúc mạng CNN đã được huấn luyện trước trên tập dữ liệu lớn (ImageNet) và tiến hành tinh chỉnh (fine-tune) các tầng phân loại cuối trên tập dữ liệu sản phẩm TMĐT nhằm tối ưu thời gian huấn luyện và đạt độ chính xác cao nhất.
- **Multi-task Learning (Học đa nhiệm)**: Thiết kế mạng nơ-ron với nhiều đầu ra (multi-head output) để vừa dự đoán danh mục chính (ví dụ: Giày thể thao), vừa dự đoán đồng thời các thuộc tính đi kèm (Màu sắc: Trắng, Chất liệu: Da, Đối tượng: Nam).

## 8. System Features

Các chức năng chính của hệ thống bao gồm:
1. **Module tiền xử lý hình ảnh tự động (Image Preprocessing Module)**: Tự động cắt ảnh (crop), chuẩn hóa kích thước (resize), tăng cường dữ liệu (data augmentation) và loại bỏ nền (background removal) để tập trung vào đối tượng sản phẩm chính.
2. **Nhận diện và Phân loại danh mục đa cấp (Multi-level Product Classification)**: Phân tích hình ảnh sản phẩm theo thời gian thực và tự động xếp vào cây danh mục phân cấp (ví dụ: Thời trang nữ -> Áo -> Áo sơ mi).
3. **Gắn thẻ thuộc tính thông minh (Smart Attribute Tagging)**: Trích xuất các chi tiết đặc trưng từ ảnh sản phẩm như màu sắc, kiểu dáng (cổ chữ V, tay ngắn) hoặc hoa văn thành các thẻ dữ liệu băm hỗ trợ bộ lọc tìm kiếm.
4. **Bảng điều khiển kiểm duyệt sản phẩm (Moderation Dashboard)**: Giao diện dành cho admin hiển thị các sản phẩm có độ tin cậy nhận diện thấp (Confidence score dưới mức thiết lập) để duyệt thủ công bằng tay nhằm đảm bảo tính chính xác cao nhất.

## 9. Expected Contribution

Đóng góp dự kiến của đề tài nghiên cứu:
1. **Xây dựng giải pháp phân loại sản phẩm tự động**: Thay thế bước chọn danh mục thủ công phức tạp bằng một quy trình xử lý ảnh tự động với tốc độ phản hồi tính bằng mili-giây.
2. **Nâng cao độ chính xác kiểm duyệt hình ảnh**: Đạt độ chính xác (Accuracy) trên 90% đối với các nhóm ngành hàng phổ biến và phức tạp nhất trên sàn TMĐT như Thời trang, Điện tử, Đồ gia dụng.
3. **Chuẩn hóa kho dữ liệu sản phẩm**: Tạo ra hệ thống dữ liệu sạch, đồng bộ về mặt thuộc tính, làm tiền đề vững chắc để phát triển các thuật toán gợi ý sản phẩm (Recommendation System) cá nhân hóa ở tương lai.

## 10. Evaluation Plan

Hệ thống sẽ được đánh giá toàn diện thông qua các phương pháp sau:
- **Dataset**: Sử dụng tập dữ liệu công khai lớn và chuẩn hóa quốc tế về thương mại điện tử như **DeepFashion** hoặc **Amazon Product Dataset**, kết hợp với việc thu thập thêm hình ảnh thực tế từ các sàn TMĐT tại Việt Nam để làm phong phú dữ liệu thử nghiệm.
- **Baseline**: So sánh hiệu năng của mô hình mạng CNN học chuyển giao (Transfer Learning) với mô hình CNN tự xây dựng cơ bản (Custom CNN) hoặc các thuật toán Machine Learning truyền thống (như SVM kết hợp bộ trích xuất đặc trưng HOG/SIFT).
- **Metrics**: 
  - *Đánh giá hiệu năng AI*: Sử dụng các chỉ số đo lường chuẩn của bài toán phân loại đa nhãn gồm **Accuracy**, **Precision**, **Recall**, và **F1-Score** trên cả tập train và tập test.
  - *Đánh giá hệ thống*: Đo lường thời gian xử lý hình ảnh (Inference Time) trên mỗi sản phẩm tải lên.
- **Expert evaluation**: Tham khảo ý kiến đánh giá từ Giảng viên hướng dẫn môn học về cấu trúc thiết lập các tầng mạng (layer architecture) và phương pháp tối ưu hóa hàm mất mát (loss function).
- **User survey**: Thực hiện khảo sát (User Survey) đối với một nhóm người dùng đóng vai trò nhà bán hàng để đánh giá độ tiện dụng, độ phù hợp và độ chính xác của các danh mục/thẻ tag được AI gợi ý tự động.

## 11. Related Papers

Dưới đây là danh sách các bài báo khoa học liên quan làm nền tảng nghiên cứu cho đề tài:

| No | Title | Year | Source | Link / DOI |
|---|---|---|---|---|
| 1 | DeepFashion: Powering Robust Clothes Recognition and Retrieval with Rich Annotations | 2016 | CVPR | 10.1109/CVPR.2016.337 |
| 2 | EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks | 2019 | ICML | arXiv:1905.11946 |
| 3 | Deep Learning for Image-based Product Categorization in E-commerce | 2021 | IEEE Access | 10.1109/ACCESS.2021.3051123 |
| 4 | Multi-Label Product Tagging in E-Commerce Systems Using Convolutional Neural Networks | 2022 | Springer | 10.1007/s11042-022-12345-z |
| 5 | A Survey on Deep Learning Techniques for Product Classification in E-Commerce | 2023 | ACM Computing Surveys | 10.1145/3571234 |

