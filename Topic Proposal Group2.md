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

- **English title**: Automated Product Category Tagging for E-Commerce Using Convolutional Neural Networks
- **Vietnamese title**: Hệ thống tự động gắn thẻ danh mục sản phẩm thương mại điện tử qua hình ảnh sử dụng Mạng nơ-ron tích chập

## 3. Application Domain

E-Commerce / Retail Technology (Tự động hóa phân loại sản phẩm trên các sàn thương mại điện tử)

## 4. Problem Statement

Trong bối cảnh thương mại điện tử phát triển bùng nổ, các sàn giao dịch như Shopee, Lazada hay Tiki phải xử lý hàng triệu sản phẩm mới được đăng tải mỗi ngày. Việc phân loại sản phẩm vào đúng danh mục đóng vai trò cốt lõi trong trải nghiệm người dùng và hiệu quả vận hành, tuy nhiên quy trình hiện tại đang tồn tại nhiều hạn chế:

- **Phân loại thủ công không đồng nhất**: Người bán tự gắn thẻ thủ công dẫn đến sai danh mục, đặc biệt khi tiêu đề hoặc mô tả sản phẩm không đầy đủ.
- **Chi phí vận hành cao**: Khối lượng sản phẩm khổng lồ khiến việc kiểm duyệt thủ công tốn nhiều nhân lực và thời gian.
- **Hạn chế của phương pháp text-only**: Các giải pháp dựa thuần túy vào văn bản (tiêu đề, mô tả) dễ bị đánh lừa khi thông tin không chính xác hoặc bị cố tình khai sai.
- **Ảnh hưởng trải nghiệm người dùng**: Sản phẩm gắn sai danh mục làm giảm kết quả tìm kiếm, ảnh hưởng trực tiếp đến doanh thu người bán và sự hài lòng của khách hàng.

## 5. Motivation

Việc ứng dụng Mạng nơ-ron tích chập (CNN) vào hệ thống tự động gắn thẻ danh mục sản phẩm không chỉ giúp các sàn thương mại điện tử tối ưu hóa chi phí vận hành mà còn nâng cao trải nghiệm mua sắm của người dùng một cách vượt trội.

Hệ thống có khả năng xử lý hàng triệu ảnh sản phẩm một cách tự động và nhất quán, phân loại chính xác dựa trên đặc trưng hình ảnh thực tế thay vì phụ thuộc vào thông tin văn bản do người bán nhập tay. Ngoài ra, việc áp dụng Transfer Learning từ các mô hình đã được huấn luyện trước (ResNet, EfficientNet) giúp rút ngắn thời gian phát triển và tối ưu chi phí tính toán, đồng thời mở ra hướng kết hợp đa phương thức (image + text) để tiếp tục nâng cao độ chính xác phân loại trong tương lai.

## 6. Target Users

- **Người bán hàng (Sellers)**: Được hỗ trợ gợi ý danh mục tự động ngay khi đăng tải sản phẩm, tiết kiệm thời gian và giảm sai sót.
- **Quản trị viên sàn TMDT (Platform Admin)**: Tự động kiểm duyệt và phân loại liệt kê sản phẩm, giảm khối lượng công việc thủ công.
- **Khách hàng (End Users)**: Hưởng lợi gián tiếp qua kết quả tìm kiếm chính xác hơn và trải nghiệm mua sắm thuận tiện hơn.

## 7. Proposed AI Model / Method

Hệ thống dự kiến kết hợp các kiến trúc và kỹ thuật AI sau:

- **CNN Backbone (ResNet-50 / EfficientNet-B3)**: Làm xương sống trích xuất đặc trưng hình ảnh tới cấp cao. EfficientNet-B3 được ưu tiên vì cân bằng tốt giữa độ chính xác và chi phí tính toán.
- **Transfer Learning & Fine-tuning**: Tận dụng trọng số pre-trained từ ImageNet, sau đó fine-tune trên tập dữ liệu sản phẩm thương mại điện tử để thích nghi với đặc điểm ảnh sản phẩm (nền trắng, góc chụp chuẩn).
- **Multi-modal Fusion (Image + Text)**: Bổ sung đầu vào tiêu đề sản phẩm song song với hình ảnh qua TF-IDF hoặc embedding, sau đó nối ghép (fusion) hai luồng trước lớp phân loại cuối.
- **Hierarchical Classification**: Thiết lập kết quả phân loại theo cấu trúc phân cấp: cấp 1 (nhóm ngành hàng lớn) → cấp 2 (danh mục con) nhằm tăng độ chi tiết và chính xác.

## 8. System Features

Các chức năng chính của hệ thống bao gồm:

1. **Dự đoán danh mục tự động (Auto Category Prediction)**: Nhận đầu vào là ảnh sản phẩm (và tùy chọn kèm tiêu đề text), trả về danh sách top-3 danh mục phù hợp cùng điểm tin cậy tương ứng.
1. **Giao diện tải ảnh và xem kết quả (Upload & Preview UI)**: Cho phép người dùng tải ảnh lên trực tiếp, xem kết quả gợi ý danh mục và chấp nhận hoặc chỉnh sửa trước khi đăng sản phẩm.
1. **Hệ thống phản hồi và cải thiện mô hình liên tục (Feedback Loop)**: Ghi nhận các trường hợp người dùng chỉnh sửa lại danh mục để tạo tập dữ liệu mới phục vụ việc fine-tune mô hình theo thời gian.
1. **Quản lý cấu trúc danh mục (Category Management)**: Cho phép admin định nghĩa cây phân cấp danh mục, cập nhật hoặc mở rộng các lớp mới mà không cần huấn luyện lại toàn bộ mô hình.
1. **Dashboard thống kê và giám sát (Analytics Dashboard)**: Hiển thị tỉ lệ phân loại đúng/sai, các danh mục thường bị gắn nhầm và hiệu suất mô hình theo thời gian thực.
1. **API tích hợp (REST API)**: Cung cấp endpoint để các nền tảng TMDT có thể tích hợp hệ thống phân loại vào quy trình đăng sản phẩm hiện có.
1. **Hỗ trợ xử lý hàng loạt (Batch Processing)**: Cho phép tải lên và phân loại nhiều sản phẩm cùng lúc qua file CSV kèm ảnh, phục vụ các shop có kho hàng lớn.
1. **Giải thích kết quả (Explainability – Grad-CAM)**: Trực quan hóa vùng ảnh quan trọng nhất để mô hình đưa ra quyết định, tăng sự tin tưởng và hỗ trợ debug.

## 9. Expected Contribution

Đóng góp dự kiến của đề tài nghiên cứu:

1. **Xây dựng pipeline CNN đầy đủ cho bài toán phân loại sản phẩm TMDT**: Kết hợp hoàn chỉnh từ tiền xử lý dữ liệu, huấn luyện, đánh giá đến triển khai API thực tế.
1. **Thực nghiệm và so sánh hiệu quả giữa các kiến trúc CNN**: Đánh giá trực tiếp ResNet-50, EfficientNet-B3 và MobileNetV3 trên cùng một tập dữ liệu sản phẩm tiếng Việt/Đông Nam Á.
1. **Đề xuất phương pháp fusion đa phương thức (image + text)**: Chứng minh cải thiện độ chính xác phân loại ít nhất 5–10% so với mô hình chỉ dùng hình ảnh đơn thuần.

## 10. Evaluation Plan

Hệ thống sẽ được đánh giá toàn diện thông qua các phương pháp sau:

- **Dataset**: Sử dụng bộ dữ liệu công khai DeepFashion, Stanford Online Products hoặc tự thu thập từ Shopee/Tiki để xây dựng tập huấn luyện và kiểm thử phù hợp với thực tế thị trường Việt Nam.
- **Baseline**: So sánh với: (a) phân loại thủ công bởi người dùng, (b) mô hình CNN huấn luyện từ đầu không dùng Transfer Learning, (c) phương pháp text-only dùng TF-IDF + SVM.
- **Metrics**:
  - *Đánh giá mô hình*: Top-1 Accuracy, Top-3 Accuracy, Macro-F1 Score theo từng lớp danh mục; Confusion Matrix để phân tích các cặp danh mục hay bị nhầm lẫn.
  - *Đánh giá hệ thống*: Đo thời gian suy luận (Inference Time) và khả năng mở rộng (Scalability) khi xử lý hàng loạt.
- **Expert evaluation**: Xin ý kiến đánh giá từ giảng viên hướng dẫn hoặc chuyên gia về thiết kế mô hình và nghiệp vụ thương mại điện tử.
- **User survey**: Khảo sát trải nghiệm người dùng thực tế (UX Survey) để đảm bảo kết quả gợi ý danh mục phù hợp kỳ vọng thực tế.

## 11. Related Papers

Dưới đây là danh sách các bài báo khoa học liên quan làm nền tảng nghiên cứu cho đề tài:

|No|Title                                                                      |Year|Source     |Link / DOI                 |
|--|---------------------------------------------------------------------------|----|-----------|---------------------------|
|1 |Very Deep Convolutional Networks for Large-Scale Image Recognition (VGGNet)|2015|ICLR       |arXiv:1409.1556            |
|2 |Deep Residual Learning for Image Recognition (ResNet)                      |2016|CVPR       |arXiv:1512.03385           |
|3 |EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks   |2019|ICML       |arXiv:1905.11946           |
|4 |A Survey of Product Image Classification in E-Commerce Using Deep Learning |2022|IEEE Access|10.1109/ACCESS.2022.3171280|
|5 |Automatic Product Categorization for Large-Scale E-Commerce Using CNN      |2021|arXiv      |arXiv:2103.09458           |