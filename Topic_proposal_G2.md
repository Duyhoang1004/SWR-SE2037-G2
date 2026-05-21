# Topic Proposal: Khoa học Dữ liệu và Trí tuệ Nhân tạo

## 1. Group Information

- **Class:** SE2037
- **Group:** Group 2
- **Leader:** Nguyen Duy Hoang
- **Members:** 
  1. Nguyen Duy Hoang (Nhóm trưởng)
  2. Bui Van Nghia
  3. Nguyen Thanh Son
  4. Nhieu Si Luan
  5. Nguyen Dinh Nhat Dinh
  6. Dao Trong Tan

## 2. Proposed Title

- **English title:** Efficient Fine-Grained Product Attribute Extraction and Automated Tagging for E-Commerce Cataloging via Attention-Enhanced Convolutional Neural Networks.
- **Vietnamese title:** Hệ thống trích xuất thuộc tính sản phẩm và tự động gắn thẻ danh mục thương mại điện tử dựa trên Mạng nơ-ron tích chập(CNN).

## 3. Application Domain

- Intelligent Retail Technology & E-commerce Automation (Công nghệ bán lẻ thông minh & Tự động hóa Thương mại điện tử)

---

## 4. Problem Statement

Sự bùng nổ của Thương mại điện tử kéo theo sự quá tải trong quản lý danh mục sản phẩm (Product Cataloging). Quy trình vận hành hiện tại đang đối mặt với "nút thắt cổ chai" lớn:
- **Sự mơ hồ và mất đối xứng thông tin:** Người bán (Sellers) khi đăng tải sản phẩm thường chỉ gán các nhãn rất chung chung (ví dụ: "Áo","Quần",...) mà bỏ qua các thuộc tính chi tiết (kiểu cổ, chiều dài tay, họa tiết, màu sắc,...), làm giảm khả năng phân loại sâu của hệ thống.
- **Rác dữ liệu dạng văn bản (Textual Noise):** Các giải pháp lọc danh mục dựa vào từ khóa tiêu đề hoặc mô tả rất dễ bị nhiễu do người bán cố tình spam từ khóa thịnh hành để câu tương tác, khiến thuật toán phân loại dựa trên văn bản bị sai lệch nghiêm trọng.
- **Chi phí hậu kiểm (Post-moderation Cost):** Các sàn đang phải duy trì một đội ngũ nhân sự khổng lồ để rà soát, sửa đổi thủ công các thẻ danh mục bị gắn sai nhằm bảo vệ cấu trúc cây thư mục hệ thống.

## 5. Motivation

Thay vì ép buộc người dùng phải điền thủ công hàng chục biểu mẫu thuộc tính phức tạp, giải pháp khai thác thông tin trực tiếp từ **hình ảnh thực tế** của sản phẩm là hướng đi tối ưu nhất. Việc ứng dụng mạng CNN cải tiến không chỉ dừng lại ở phân loại lớp thô (Coarse-grained) mà hướng tới trích xuất các đặc trưng hạt mịn (Fine-grained), tự động bóc tách các đặc tính thị giác ẩn sâu trong sản phẩm. 

Đặc biệt, việc hướng tới tối ưu hóa kiến trúc mô hình (kiến trúc gọn nhẹ, hiệu năng cao) giúp hệ thống có thể chạy trực tiếp với độ trễ thấp (Low-latency), sẵn sàng tích hợp vào luồng xử lý thời gian thực của các sàn Thương mại điện tử tại Việt Nam mà không đòi hỏi hạ tầng máy chủ quá đắt đỏ.

## 6. Target Users

- **Bộ phận Kiểm soát Chất lượng Dữ liệu (Data QC / Platform Admins):** Sở hữu một bộ công cụ tự động phát hiện, cảnh báo và chỉnh sửa các sản phẩm bị phân loại sai ngành hàng ngay từ bộ lọc đầu vào.
- **Nhà bán hàng doanh nghiệp & Cá nhân (Sellers):** Trải nghiệm quy trình đăng sản phẩm "một chạm" – chỉ cần tải ảnh, hệ thống tự động điền (Auto-populate) toàn bộ cây danh mục và từ khóa thuộc tính liên quan.
- **Khách hàng mua sắm (End-users):** Tiếp cận bộ lọc tìm kiếm chính xác đến từng chi tiết nhỏ (ví dụ: tìm chính xác "áo cổ chữ V tay bồng" thay vì ra hàng ngàn kết quả "áo nữ" chung chung).

## 7. Proposed AI Model / Method

Nhóm đề xuất giải pháp mạng tích chập tích hợp cơ chế chú ý nhằm tối ưu hóa độ chính xác trên dữ liệu ảnh thương mại điện tử phức tạp:

- **Mạng xương sống hướng hiệu năng (Efficient CNN Backbone):** Sử dụng kiến trúc **EfficientNet (B2/B3)** hoặc **MobileNetV3** kết hợp kỹ thuật *Transfer Learning* từ bộ trọng số ImageNet. Lựa chọn này đảm bảo mô hình có dung lượng nhỏ, tốc độ suy luận nhanh phù hợp môi trường production thực tế.
- **Cơ chế Chú ý Thị giác (Attention Mechanism):** Tích hợp các khối chú ý dạng khối (như **SE Block - Squeeze-and-Excitation**) vào giữa các tầng tích chập để ép mô hình tập trung vào vùng pixel chứa sản phẩm mục tiêu, loại bỏ hoàn toàn sự ảnh hưởng của nhiễu nền (nền phòng chụp, đạo cụ livestream).
- **Phân loại đa nhãn phân cấp (Hierarchical Multi-label Learning):** Thiết kế mạng đầu ra đa nhánh xử lý đồng thời: Nhánh 1 phân loại danh mục gốc (Ngành hàng lớn), Nhánh 2 trích xuất các nhãn thuộc tính chi tiết (Attributes) qua hàm kích hoạt Sigmoid.

## 8. System Features

1. **Pipeline Tiền xử lý ảnh thích ứng (Adaptive Preprocessing):** Tự động phát hiện vật thể chính, thực hiện cắt biên (Auto-cropping) và chuẩn hóa độ tương phản để triệt tiêu sự chênh lệch ánh sáng giữa ảnh chụp studio chuyên nghiệp và ảnh điện thoại của cá nhân.
2. **Công cụ Trích xuất Thuộc tính Thời gian thực (Real-time Attribute Tagging API):** Tiếp nhận ảnh qua REST API, phân tích dữ liệu thị giác dưới 200ms để trả về cấu trúc JSON chứa cây danh mục và các nhãn thuộc tính kèm điểm tin cậy ($Confidence\ Score$).
3. **Cơ chế Duyệt Phân cấp có Giám sát (Human-in-the-loop Gate):** Phân luồng dữ liệu tự động. Sản phẩm có điểm tin cậy cao được đưa thẳng vào kho lưu trữ; các sản phẩm có độ nhập nhằng cao (Ambiguity) được chuyển về giao diện trực quan hóa bản đồ nhiệt để Admin phê duyệt nhanh.
4. **Hệ thống Ghi nhận và Tự điều chỉnh (Feedback Loop Dashboard):** Lưu vết mọi thao tác chỉnh sửa nhãn của người dùng để tự động đóng gói thành tập dữ liệu phạt (Hard negative examples), hỗ trợ chu kỳ tái huấn luyện (Retraining) định kỳ nhằm nâng cấp mô hình.

## 9. Expected Contribution

1. Nghiên cứu thực nghiệm thành công giải pháp tích hợp cơ chế chú ý (Attention) vào mạng CNN dạng nhẹ để giải quyết bài toán phân loại ảnh sản phẩm TMĐT tại thị trường bản địa.
2. Thiết kế và đóng gói thành công một giải pháp API hoàn chỉnh có khả năng chịu tải tốt, kết nối chặt chẽ giữa tầng xử lý AI thông minh và hệ thống quản trị cơ sở dữ liệu quan hệ truyền thống.
3. Cung cấp một ứng dụng Web trực quan minh chứng cho khả năng tự động hóa quy trình phân loại, giúp giảm thời gian duyệt danh mục sản phẩm của doanh nghiệp lên tới 70%.

## 10. Evaluation Plan

- **Dataset:** Khai thác bộ dữ liệu quy chuẩn quốc tế về thuộc tính sản phẩm thời trang và bán lẻ hàng đầu là **DeepFashion (Attribute Prediction Subset)** kết hợp với tập dữ liệu tự thu thập có gán nhãn thực tế từ môi trường E-commerce Đông Nam Á.
- **Baseline:** Đặt mô hình đề xuất lên bàn cân so sánh với:
  1. Mô hình CNN thuần túy phiên bản cũ (VGG16 / ResNet50 truyền thống không có cơ chế Attention).
  2. Các mô hình phân loại dựa trên chuỗi văn bản thô (Text-only) sử dụng kỹ thuật trích xuất đặc trưng truyền thống.
- **Metrics:** 
  - *Độ chính xác học sâu:* Tính toán chỉ số Mean Average Precision (mAP) cho bài toán đa nhãn, Macro-F1 Score, và ma trận nhầm lẫn để kiểm soát lỗi sai giữa các nhóm nhãn có độ tương đồng thị giác cao.
  - *Hiệu năng thực tế:* Đo lường thông số thời gian phản hồi (Inference Latency) và dung lượng bộ nhớ tiêu thụ khi phân loại đồng thời luồng dữ liệu lớn.
- **Expert & User Evaluation:** Thu thập chỉ số hài lòng hệ thống (System Usability Scale - SUS) từ nhóm người dùng thử nghiệm để tối ưu hóa luồng tương tác của giao diện.

## 11. Related Papers

Dưới đây là danh mục các bài báo khoa học cốt lõi, hoàn toàn có thật trên các thư viện học thuật uy tín (IEEE, CVPR, Springer) làm điểm tựa lý thuyết vững chắc cho đề tài:

| No | Title | Year | Source | Link / DOI |
|---|---|---|---|---|
| 1 | **Deep Residual Learning for Image Recognition** | 2016 | CVPR (IEEE) | [10.1109/CVPR.2016.90](https://doi.org/10.1109/CVPR.2016.90) |
| 2 | **Squeeze-and-Excitation Networks** | 2018 | CVPR (IEEE) | [10.1109/CVPR.2018.00745](https://doi.org/10.1109/CVPR.2018.00745) |
| 3 | **EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks** | 2019 | ICML | [arXiv:1905.11946](https://arxiv.org/abs/1905.11946) |
| 4 | **Deep Learning for Fashion Cloud Shopping System** | 2020 | IEEE Access | [10.1109/ACCESS.2020.2974152](https://doi.org/10.1109/ACCESS.2020.2974152) |
| 5 | **Deep Learning in Product Image Classification for E-Commerce: A Review** | 2022 | Computer Modeling in Engineering & Sciences | [10.32604/cmes.2022.019553](https://doi.org/10.32604/cmes.2022.019553) |