# Paper 02 Summary

## Citation
*   **Tên bài:** Non-Functional Requirements for Machine Learning: Challenges and New Directions
*   **Tác giả:** Jennifer Horkoff
*   **Năm:** 2019
*   **Nguồn:** IEEE 27th International Requirements Engineering Conference (RE)
*   **DOI/Link:** (Tìm kiếm theo tên bài trên IEEE Xplore)

## Problem
*   **Bài báo giải quyết vấn đề gì?**
    Trong Kỹ thuật Yêu cầu (RE) truyền thống, ý nghĩa, cách phân rã (refinement) và sự đánh đổi của các Yêu cầu phi chức năng (NFRs) đã được định nghĩa rất rõ ràng. Tuy nhiên, khi áp dụng cho hệ thống Machine Learning (ML), những kiến thức này không còn đúng nữa. Một số NFRs mới nổi lên trở nên cực kỳ quan trọng (như tính công bằng - fairness, tính minh bạch - transparency, quyền riêng tư - privacy), trong khi các NFRs cũ (như tính mô-đun) lại giảm vai trò. Vấn đề là hiện tại chúng ta thiếu hiểu biết về cách định nghĩa, đo lường và đánh đổi các NFRs đặc thù này trong bối cảnh ML.

## Method
*   **Bài báo dùng phương pháp nghiên cứu nào?**
    Đây là một bài báo định hướng nghiên cứu (Vision Paper / Position Paper). Tác giả thực hiện phân tích tổng quan các nghiên cứu hiện có (State-of-the-Art) trong cả hai mảng RE và ML để vạch ra những khoảng trống kiến thức. Từ đó, tác giả đúc kết thành 7 thách thức (Challenges) và đề xuất 6 mục tiêu nghiên cứu (Research Agenda) để cộng đồng học thuật giải quyết trong tương lai.

## Context
*   **Bài báo được thực hiện trong bối cảnh nào?**
    Bối cảnh giao thoa giữa Kỹ thuật Yêu cầu (Requirements Engineering) và Học máy (Machine Learning). Bài báo tập trung vào quá trình thiết kế, mô hình hóa và giám sát vòng đời của các phần mềm có tích hợp thuật toán ML.

## Key Findings
*   **Kết quả/phát hiện chính là gì?**
    Bài báo chỉ ra 7 thách thức cốt lõi (C1-C7), trong đó nổi bật là:
    *   **C1 & C3:** Sự hiểu biết về NFRs cho ML còn phân mảnh. Chúng ta chưa biết cách định nghĩa, phân rã và đo lường chính xác các NFRs (ví dụ: làm sao để định lượng được "fairness" hay "explainability" của một mô hình?).
    *   **C2:** Thiếu kiến thức về sự tác động và **đánh đổi (trade-offs)** giữa các thuật toán ML và các NFRs (ví dụ: mô hình bảo mật dữ liệu tốt hơn thì lại chạy chậm hơn).
    *   **C4 & C6:** Khó khăn trong việc giám sát chất lượng mô hình ở thời gian thực (runtime) và quản lý sự tiến hóa của ML (khi nào cần huấn luyện lại mô hình do dữ liệu hoặc yêu cầu thay đổi?).
    *   **C5:** Thiếu một ngôn ngữ mô hình hóa (modeling language) chuyên biệt để thể hiện các NFRs cho hệ thống ML.
    Dựa trên đó, tác giả đề xuất lộ trình nghiên cứu (Obj1-Obj6) bao gồm: tạo danh mục (catalogue) NFRs cho ML, thu thập các thước đo (metrics), và phát triển các phương pháp hỗ trợ quyết định ở cả giai đoạn thiết kế và chạy thực tế.

## Limitations
*   **Hạn chế của bài báo là gì?**
    Vì đây là bài báo vạch ra "thách thức và hướng đi mới" (Challenges and New Directions), nó không cung cấp một giải pháp hoàn chỉnh hay dữ liệu thực nghiệm cụ thể nào để giải quyết các thách thức đó. Nó chỉ đóng vai trò là kim chỉ nam để các nhà nghiên cứu khác (như nhóm của bạn) tiếp tục đào sâu.

## Relevance to our topic
*   **Bài báo liên quan gì đến đề tài của nhóm?**
    *   **Khẳng định tính cấp thiết của đề tài:** Bài báo này là minh chứng học thuật tuyệt vời (khoảng trống nghiên cứu) hỗ trợ cho mục "Problem Statement" của nhóm: *Việc thiếu hụt phương pháp đặc tả NFRs cho AI đang là một bài toán nhức nhối của thế giới.*
    *   **Củng cố trọng tâm NFRs:** Nhóm đang muốn đo lường "Explainability" và "Data Quality" cho hệ thống phân loại e-commerce. Bài báo xác nhận rằng việc định nghĩa và tìm thước đo (metrics) cho các yếu tố này là thách thức quan trọng nhất hiện nay (Challenge C1 & C3).
    *   **Định hướng phân tích Trade-off:** Tương tự bài báo số 1, bài này nhấn mạnh việc phân tích sự đánh đổi (Challenge C2). Nhóm có thể dùng điểm này để lập luận tại sao việc chọn mô hình CNN (độ chính xác cao nhưng khó giải thích) lại cần một quy trình RE khắt khe để thiết kế giao diện bù đắp lại tính minh bạch.
