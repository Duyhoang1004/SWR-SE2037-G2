# TOPIC PROPOSAL

## 1. Group Information

- **Class:** SE2037
- **Group:** Group 2
- **Leader:** Nguyen Duy Hoang
- **Members:**
  - Bui Van Nghia
  - Nguyen Thanh Son
  - Nhieu Si Luan
  - Nguyen Dinh Nhat Dinh
  - Dao Trong Tan

---

## 2. Proposed Title

- **English title:** Requirements Engineering for an AI-Based Automated E-commerce Product Categorization System using Convolutional Neural Networks (CNN).
- **Vietnamese title:** Nghiên cứu Quy trình Thu thập và Đặc tả Yêu cầu Phần mềm cho Hệ thống Tự động Phân loại Sản phẩm Thương mại Điện tử bằng Mạng Nơ-ron Tích chập (CNN).

---

## 3. Application Domain

- Requirements Engineering (RE) for AI/ML Systems.
- E-commerce (Thương mại điện tử).
- Computer Vision / Deep Learning (CNN).

---

## 4. Problem Statement

Trên các sàn thương mại điện tử, mỗi ngày người bán phải đăng hàng trăm sản phẩm và phải tự chọn danh mục phù hợp (ví dụ: Quần áo, đồ điện tử, gia dụng). Việc chọn sai danh mục khiến sản phẩm khó tìm thấy, ảnh hưởng trực tiếp đến doanh thu. Vì vậy, nhiều nền tảng đã ứng dụng AI để tự động phân loại sản phẩm dựa trên hình ảnh.

Tuy nhiên, vấn đề nằm ở chỗ: các nhóm phát triển thường tập trung hoàn toàn vào việc làm cho AI phân loại chính xác, mà bỏ qua một bước quan trọng trước đó — đó là **xác định rõ hệ thống cần làm gì và cần đảm bảo những gì** trước khi bắt tay vào xây dựng. Bước này trong kỹ thuật phần mềm gọi là **Requirements Engineering (RE)**.

Cụ thể có ba vấn đề chưa được giải quyết:

1. **Chưa có quy trình thu thập yêu cầu rõ ràng** — Các tính năng như tự động gợi ý danh mục, hiển thị độ tin cậy của kết quả AI, hay cho phép người bán phản hồi khi AI phân loại sai, thường không được xác định cụ thể từ đầu.
2. **Bỏ sót các yêu cầu phi chức năng quan trọng** — Ngoài độ chính xác, hệ thống AI còn cần đảm bảo: giải thích được tại sao phân loại như vậy (để người bán tin dùng), và có đủ dữ liệu hình ảnh chất lượng để huấn luyện AI. Những điều này thường không được đưa vào tài liệu yêu cầu từ đầu.
3. **Khoảng cách giao tiếp giữa người dùng và đội kỹ thuật** — Người bán hàng không biết diễn đạt nhu cầu bằng ngôn ngữ kỹ thuật, còn lập trình viên AI thì không hiểu nghiệp vụ bán hàng. Kết quả là hệ thống xây xong nhưng không đáp ứng đúng nhu cầu thực tế.

---

## 5. Motivation

Việc áp dụng RE cho các hệ thống AI/ML đặt ra nhiều thách thức bổ sung so với phần mềm thông thường. Khác với phần mềm truyền thống — nơi yêu cầu được lập trình trực tiếp từng bước — hệ thống ML học từ dữ liệu, khiến nhiều yêu cầu quan trọng như chất lượng dữ liệu huấn luyện hay khả năng giải thích kết quả trở nên khó xác định và đo lường hơn. Các nghiên cứu gần đây xác nhận rằng phần lớn tổ chức gặp khó khăn trong việc define và specify các NFR đặc thù cho ML, và các kỹ thuật RE hiện tại cần được điều chỉnh để phù hợp với bối cảnh này (Vogelsang & Borg, 2019; Habibullah & Horkoff, 2021).

Tuy nhiên, dù đã có nhiều nghiên cứu về RE cho AI systems nói chung, vẫn còn thiếu nghiên cứu áp dụng cụ thể cho bài toán phân loại sản phẩm thương mại điện tử. Đây là một khoảng trống đáng chú ý, vì hệ thống phân loại sản phẩm có đặc thù riêng: stakeholder đa dạng (người bán, quản trị viên, lập trình viên AI), dữ liệu đầu vào là hình ảnh với chất lượng không đồng đều, và yêu cầu về khả năng giải thích kết quả AI có tác động trực tiếp đến niềm tin của người dùng. Nghiên cứu này nhằm khám phá khả năng áp dụng một quy trình RE phù hợp cho bối cảnh đó, thông qua việc đề xuất và kiểm chứng quy trình bằng một prototype thực tế.

---

## 6. Target Users

- Người bán hàng (Sellers/Merchants): Được hỗ trợ gợi ý danh mục tự động ngay khi đăng tải sản phẩm, giúp tiết kiệm thời gian, tối ưu quy trình đăng bán và giảm thiểu sai sót do cấu hình thủ công.
- Quản trị viên nền tảng (Platform Administrators): Tự động hóa quy trình kiểm duyệt và phân loại hàng loạt sản phẩm đổ về hệ thống, giảm tải tối đa khối lượng công việc thủ công và hạn chế rủi ro duyệt sai.
- Nhân viên quản lý danh mục sản phẩm (Catalog Managers): Dễ dàng chuẩn hóa cấu trúc cây danh mục toàn sàn, kiểm soát chất lượng dữ liệu đầu vào và phát hiện nhanh các sản phẩm bị phân loại sai vị trí.
- Lập trình viên AI phát triển hệ thống phân loại (ML Engineers / AI Developers): Thu thập được dữ liệu phản hồi (feedback loop) từ thực tế để liên tục huấn luyện, tối ưu hóa độ chính xác và nâng cấp mô hình phân loại sản phẩm.

---

## 7. Proposed AI Model / Method

### 7.1 Mô hình AI

Hệ thống sử dụng mạng nơ-ron tích chập (CNN) với kỹ thuật Transfer Learning — tận dụng lại mô hình AI đã được huấn luyện sẵn (ResNet hoặc MobileNet) và tinh chỉnh lại cho bài toán phân loại sản phẩm. Mô hình CNN ở đây đóng vai trò là **prototype triển khai** để kiểm chứng tính khả thi của bộ yêu cầu đã được xây dựng, không phải là đối tượng nghiên cứu chính.

### 7.2 Quy trình Requirements Engineering

Nhóm áp dụng quy trình RE 3 bước dựa trên phương pháp Prototype-Driven RE (Paper #10). Phương pháp này được chọn vì stakeholder trong bài toán AI thường khó diễn đạt nhu cầu bằng lời — việc cho họ tương tác trực tiếp với prototype giúp elicitation requirements thực tế và đầy đủ hơn so với phỏng vấn thuần túy:

1. **Bước 1 - Thu thập yêu cầu (Elicitation):** Phỏng vấn người bán hàng, quản trị viên và catalog managers, kết hợp với cho họ dùng thử prototype để tìm ra những nhu cầu thực sự mà họ không thể diễn đạt bằng lời.
2. **Bước 2 - Viết tài liệu yêu cầu (Specification):** Lập tài liệu SRS (Software Requirements Specification) phân loại rõ ràng: yêu cầu chức năng (FR), yêu cầu phi chức năng (NFR) tập trung vào explainability và data quality, và yêu cầu về dữ liệu huấn luyện AI.
3. **Bước 3 - Xác nhận yêu cầu (Validation):** Cho các bên liên quan xem lại tài liệu và xác nhận rằng yêu cầu đã được ghi đúng và đủ trước khi bắt đầu lập trình.

---

## 8. System Features

- **Giao diện quản lý (Merchant Dashboard):** Cho phép người bán tải ảnh sản phẩm lên để hệ thống tự động phân loại.
- **Tiền xử lý ảnh tự động:** Hệ thống tự chuẩn hóa hình ảnh (điều chỉnh kích thước, độ sáng) trước khi đưa vào AI.
- **Phân loại tự động (Auto-Tagging):** AI phân tích ảnh và gợi ý top 3 danh mục phù hợp nhất kèm theo mức độ tin cậy của từng gợi ý (Confidence Score).
- **Giải thích kết quả (Explainability Module):** Hiển thị confidence score và visual cues để người bán hiểu tại sao sản phẩm được phân vào danh mục đó.
- **Phản hồi của người bán (Seller Feedback Interface):** Cho phép người bán báo cáo khi AI phân loại sai, dữ liệu này được dùng để cải thiện mô hình theo thời gian.
- **Backend & AI Service:** Phần xử lý nghiệp vụ dùng Java, phần chạy mô hình AI dùng Python, hai phần tích hợp với nhau trong cùng một hệ thống để dễ triển khai và bảo trì.

---

## 9. Expected Contribution

- Xây dựng quy trình RE đầy đủ cho hệ thống AI phân loại sản phẩm e-commerce, bao gồm FR, NFR và Data Requirements.
- Đề xuất cách xác định và đo lường các yêu cầu về khả năng giải thích kết quả AI (explainability) và chất lượng dữ liệu huấn luyện trong bối cảnh e-commerce.
- Chứng minh tính khả thi của bộ yêu cầu đã xây dựng thông qua một prototype CNN có khả năng phân loại sản phẩm và hiển thị kết quả cho người bán.
- Cung cấp tài liệu RE có thể tái sử dụng làm tham khảo cho các dự án AI e-commerce tương tự.

---

## 10. Evaluation Plan

**Dataset:**
Sử dụng bộ dữ liệu ảnh sản phẩm mã nguồn mở trên Kaggle (Fashion Product Images Dataset hoặc E-Commerce Products Image Dataset). Yêu cầu về dữ liệu được xác định rõ ràng trong tài liệu RE trước khi thu thập.

**Baseline:**
- Về AI prototype: So sánh mô hình CNN với phương pháp phân loại ảnh truyền thống (SVM + HOG) để validate tính khả thi và hiệu năng của prototype.
- Về RE: So sánh mức độ đầy đủ của yêu cầu giữa quy trình có hệ thống của nhóm và cách làm thông thường.

**Metrics:**

| Metric | Mô tả |
|--------|-------|
| Accuracy | Tỷ lệ phân loại đúng tổng thể của prototype CNN |
| Precision / Recall / F1-Score | Đánh giá độ chính xác chi tiết theo từng danh mục sản phẩm |
| Requirements completeness rate | Tỷ lệ yêu cầu được stakeholder xác nhận đầy đủ, đo bằng số yêu cầu được chấp nhận không cần sửa lớn trên tổng số yêu cầu đã thu thập |
| Explainability satisfaction score | Mức độ hài lòng của người bán với phần giải thích kết quả của AI, thu thập qua khảo sát |
| Upload time | Thời gian hoàn thành đăng 1 sản phẩm khi có AI hỗ trợ so với làm thủ công |

**Expert evaluation:** Không áp dụng.

**User survey:** Khảo sát người bán hàng về tính dễ hiểu của phần giải thích kết quả AI.

---

## 11. Related Papers

| No | Title | Year | Source | DOI / Link |
|----|-------|------|--------|------------|
| #1 | Requirements Engineering for Machine Learning: Perspectives from Data Scientists | 2019 | IEEE | [10.1109/ICREW.2019.00009](https://ieeexplore.ieee.org/document/8933800/) |
| #2 | Requirements Engineering in Machine Learning Projects | 2023 | IEEE Access | [10.1109/ACCESS.2023.3294840](https://doi.org/10.1109/ACCESS.2023.3294840) |
| #3 | Tailoring Requirements Engineering for Responsible AI | 2023 | arXiv | [arXiv:2302.10816](https://arxiv.org/pdf/2302.10816) |
| #4 | Modeling Data Requirements for Machine Learning Systems | 2022 | IEEE | [10.1109/RE54965.2022.00046](https://ieeexplore.ieee.org/document/9930317/) |
| #5 | Non-Functional Requirements for Machine Learning: Challenges and New Directions | 2021 | ResearchGate | [10.1007/978-3-030-49392-9_1](https://www.researchgate.net/publication/337793978) |
| #6 | Requirements Engineering (RE) in AI Systems: The Need to Emphasize NFRs for Ethical AI | 2025 | Springer | [10.1007/978-3-031-78255-8_25](https://link.springer.com/chapter/10.1007/978-3-031-78255-8_25) |
| #7 | Elicitation and Documentation of Explainability Requirements in AI Systems | 2025 | SCITEPRESS | [scitepress.org/Papers/2025/134706](https://www.scitepress.org/Papers/2025/134706/134706.pdf) |
| #8 | Requirements Elicitation and Stakeholder Communications for Explainable ML Systems | 2023 | IEEE | [10.1109/RE57078.2023.00057](https://ieeexplore.ieee.org/document/10225934/) |
| #9 | Machine Learning-Enhanced Requirements Engineering: A Systematic Literature Review | 2024 | SCITEPRESS | [scitepress.org/Papers/2024/126881](https://www.scitepress.org/Papers/2024/126881/126881.pdf) |
| #10 | Requirements Elicitation for Prototype-Driven AI Engineering | 2024 | CEUR-WS | [ceur-ws.org/Vol-3959/PT-paper4](https://ceur-ws.org/Vol-3959/PT-paper4.pdf) |
| #11 | AI for Requirements Engineering: Industry Adoption and Challenges | 2025 | arXiv | [arXiv:2511.01324](https://arxiv.org/pdf/2511.01324) |
