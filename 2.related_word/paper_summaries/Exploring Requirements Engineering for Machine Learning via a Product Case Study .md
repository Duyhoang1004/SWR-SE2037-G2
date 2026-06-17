# Paper 06 Summary

## Citation
*   **Tên bài:** Exploring Requirements Engineering for Machine Learning via a Product Case Study.
*   **Tác giả:** Lynn Vonderhaar, Timothy Elvira, Juan Couder, Omar Ochoa.
*   **Năm:** 2025.
*   **Nguồn:** The International FLAIRS Conference Proceedings, Vol. 38.
*   **DOI/Link:** https://www.researchgate.net/publication/391794910_Exploring_Requirements_Engineering_for_Machine_Learning_via_a_Product_Case_Study.

## Problem
*   **Bài báo giải quyết vấn đề gì?** Quá trình Kỹ thuật Yêu cầu (RE) truyền thống vốn được thiết kế cho các phần mềm có tính tất định (deterministic software), do đó thiếu đi cấu trúc chính thức cần thiết để áp dụng vào quá trình phát triển Học máy (Machine Learning). Khi ML ngày càng trở nên phổ biến trên nhiều lĩnh vực, việc phát triển và triển khai công nghệ này đang rất cần một quy trình thiết kế và kiểm chứng có cấu trúc rõ ràng để tránh sai sót.

## Method
*   **Bài báo dùng phương pháp nghiên cứu nào?** Bài báo sử dụng phương pháp nghiên cứu tình huống (Case Study). Các tác giả đã thực nghiệm toàn bộ quy trình RE trên một hệ thống phần mềm dựa trên ML thực tế, bắt đầu từ bước lấy mô tả sản phẩm của khách hàng cho đến bước xác chuẩn tài liệu đặc tả yêu cầu (requirement specification validation).

## Context
*   **Bài báo được thực hiện trong bối cảnh nào?** Nghiên cứu được thực hiện trong bối cảnh công nghệ Học máy đang phát triển mạnh mẽ và được ứng dụng vào nhiều miền khác nhau, nhưng lại vấp phải rào cản là thiếu vắng một quy trình cấu trúc phát triển phần mềm bài bản. Trọng tâm của bài báo là áp dụng quy trình RE cho việc phát triển một sản phẩm ML cụ thể.

## Key Findings
*   **Kết quả/phát hiện chính là gì?** 
    *   Qua nghiên cứu tình huống, nhóm tác giả đã xác định và đúc kết được thành công 23 Yêu cầu phi chức năng (NFRs) và 151 Yêu cầu chức năng (FRs) cho sản phẩm ML được thử nghiệm.
    *   Phát hiện quan trọng nhất là: mặc dù các FRs và NFRs dành cho hệ thống ML có hình thức và tính chất khác biệt so với các hệ thống phần mềm truyền thống, nhưng Kỹ thuật Yêu cầu (RE) hoàn toàn có thể được điều chỉnh (adapted) để áp dụng mượt mà vào việc phát triển ML, qua đó giúp cải thiện rõ rệt chất lượng mô tả hệ thống.

## Limitations
*   **Hạn chế của bài báo là gì?** Do bài báo chủ yếu dựa trên một nghiên cứu tình huống (case study) duy nhất trên một sản phẩm, các kết quả và bộ yêu cầu thu được có thể mang tính đặc thù cho sản phẩm đó và cần có thêm nhiều nghiên cứu mở rộng trên các miền ứng dụng ML khác để khẳng định tính khái quát.

## Relevance to our topic
*   **Bài báo liên quan gì đến đề tài của nhóm?**
    *   **Khẳng định tính khả thi của quy trình:** Bài báo chứng minh thực tế rằng quy trình Kỹ thuật Yêu cầu (RE) có thể được tùy chỉnh để áp dụng thành công cho việc thu thập và phân loại yêu cầu của một hệ thống có chứa yếu tố AI. Điều này trực tiếp củng cố phương pháp luận của nhóm khi tiến hành thu thập yêu cầu từ quản trị viên và người bán hàng (merchants) cho hệ thống E-commerce.
    *   **Định hướng thiết kế bộ yêu cầu:** Nhận định của bài báo về việc "yêu cầu cho ML trông sẽ khác biệt so với phần mềm truyền thống" giúp nhóm nhận thức rõ rằng khi xác định yêu cầu cho tính năng gợi ý danh mục tự động, nhóm cần định nghĩa các NFRs đặc thù cho mô hình học máy (ví dụ: yêu cầu về chất lượng gợi ý, giới hạn sai số của AI) thay vì chỉ tập trung vào các yêu cầu hệ thống thông thường (như tốc độ phản hồi trang web hay tải ảnh).