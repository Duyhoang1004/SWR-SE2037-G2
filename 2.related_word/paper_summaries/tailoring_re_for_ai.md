# Paper 01 Summary

## Citation
*   **Tên bài:** Tailoring Requirements Engineering for Responsible AI
*   **Tác giả:** Walid Maalej, Yen Dieu Pham, and Larissa Chazette
*   **Năm:** 2023
*   **Nguồn:** arXiv (được trích dẫn nhiều trong các hội nghị IEEE)
*   **DOI/Link:** [arXiv:2302.10816](https://arxiv.org/abs/2302.10816)

## Problem
*   **Bài báo giải quyết vấn đề gì?**
    Rất nhiều dự án AI thất bại khi đưa vào thực tế (dù độ chính xác trong phòng lab rất cao) do thiếu hoặc hiểu sai về các yêu cầu của người dùng, kỹ thuật và xã hội. Việc áp dụng Kỹ thuật Yêu cầu (RE) cho hệ thống AI gặp khó khăn vì các yêu cầu phi chức năng (NFRs) như tính công bằng (fairness), khả năng giải thích (explainability) thường rất mơ hồ, khó đặc tả và khó đo lường đối với các mô hình "hộp đen" (black-box).

## Method
*   **Bài báo dùng phương pháp nghiên cứu nào?**
    Đây là dạng bài báo khái niệm / định hướng (Position Paper / Vision Paper). Phương pháp chính dựa trên **tổng quan tài liệu (Literature Review)** kết hợp với **kinh nghiệm và quan sát cá nhân (Personal observations and experience)** của các tác giả trong việc phát triển các dự án Machine Learning và Data Science để rút ra 6 khía cạnh cần tinh chỉnh của RE dành riêng cho AI.

## Context
*   **Bài báo được thực hiện trong bối cảnh nào?**
    Bài báo không tập trung vào một dự án hay ngành cụ thể, mà nhắm tới bối cảnh chung của **Kỹ thuật AI có trách nhiệm (Responsible AI Engineering)**. Bối cảnh áp dụng rộng khắp từ y tế (chẩn đoán bệnh), ô tô (xe tự lái) đến các hệ thống đánh giá tự động, nơi mà yếu tố con người, đạo đức và sự an toàn được đặt lên hàng đầu.

## Key Findings
*   **Kết quả/phát hiện chính là gì?**
    Tác giả đề xuất 6 khía cạnh để "tinh chỉnh" (tailor) quy trình RE cho hệ thống AI:
    1.  **Chấp nhận các "Mức độ chất lượng" (Quality Levels):** Thay vì đòi hỏi một độ chính xác tuyệt đối, cần thỏa thuận các mức độ chất lượng (ví dụ: Level 8 là 80-89%) và phân tích rủi ro của các loại lỗi dự đoán.
    2.  **Kết hợp Prototype cho Dữ liệu và Người dùng:** Tránh việc chỉ test model trên Jupyter Notebook (Data-centered). Cần mang prototype cho người dùng test sớm, kết hợp yếu tố Human-in-the-Loop làm phương án dự phòng.
    3.  **Mở rộng RE để tập trung vào Dữ liệu (Data RE):** Cần thiết kế bộ câu hỏi riêng để thu thập yêu cầu về việc thu thập, gán nhãn, bảo mật và chất lượng dữ liệu.
    4.  **Nhúng từ vựng cụ thể vào quy trình làm việc:** Dùng các từ ngữ chuyên biệt, cụ thể (ví dụ thay vì nói "Explainability" chung chung, hãy dùng "Visualization", "Interpretability") trong khi phỏng vấn để giúp Stakeholder dễ dàng đưa ra yêu cầu.
    5.  **Phân tích sự đánh đổi (Tradeoff Analysis):** Phải làm rõ sự đánh đổi giữa các NFRs (ví dụ: Mô hình Transformer chính xác cao nhưng tốn điện và khó giải thích hơn Decision Tree).
    6.  **Dùng yêu cầu làm nền tảng để Test AI:** Các khả năng (capabilities) của mô hình cần được kiểm thử dựa trên yêu cầu từ đầu (giống như metamorphic testing).

## Limitations
*   **Hạn chế của bài báo là gì?**
    Do bài báo chủ yếu dựa trên quan sát và kinh nghiệm cá nhân của nhóm tác giả nên họ thừa nhận rằng nghiên cứu này **chưa hoàn thiện và thiếu tính khái quát hóa (completeness and generalizability)**. Các hướng đề xuất cần được kiểm chứng, đánh giá chi tiết hơn thông qua các nghiên cứu thực nghiệm (Case studies, User studies) ở các miền ứng dụng cụ thể.

## Relevance to our topic
*   **Bài báo liên quan gì đến đề tài của nhóm?**
    *   **Củng cố phương pháp tiếp cận:** Bài báo xác nhận phương pháp "Prototype-Driven RE" mà nhóm đề xuất trong Proposal (mục 7.2) là một hướng đi đúng đắn để thu hẹp khoảng cách giữa người dùng và lập trình viên AI. Tính năng phản hồi từ người bán (Seller Feedback) của nhóm chính là ứng dụng thực tế của mô hình Human-in-the-Loop.
    *   **Định hướng thiết kế bộ câu hỏi phỏng vấn (Elicitation):** Cung cấp sẵn các danh mục câu hỏi về "Data RE" (Phần III của bài báo) và gợi ý dùng từ vựng cụ thể để thu thập yêu cầu về tính giải thích (Explainability).
    *   **Cơ sở cho tài liệu Đặc tả (Specification):** Gợi ý nhóm dùng "Quality Levels" để viết tài liệu SRS cho AI thay vì các con số cứng nhắc.
    *   **Làm rõ sự đánh đổi trong mô hình CNN:** Giúp nhóm có cơ sở khoa học để lập luận về sự đánh đổi (Tradeoff) giữa việc dùng CNN (để đạt độ chính xác cao) và việc phải bù đắp các giải pháp UI/UX để đáp ứng yêu cầu khả năng giải thích (Explainability).
