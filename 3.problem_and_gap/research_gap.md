# Research Gap

Dựa trên phân tích tổng quan tài liệu (Literature Review) từ các nghiên cứu gần đây về Kỹ thuật Yêu cầu cho Học máy (RE for ML), nhóm nghiên cứu nhận diện các khoảng trống (gaps) chính sau:

1. **Thiếu bằng chứng thực nghiệm (Empirical Evidence) trong một miền ứng dụng cụ thể:** 
   Nhiều nghiên cứu hiện tại chỉ dừng lại ở việc đề xuất các khung lý thuyết (Conceptual Frameworks), định hướng tầm nhìn (Vision papers) hoặc thực hiện khảo sát diện rộng (Surveys). Thiếu đi các nghiên cứu thực nghiệm (Empirical Case Studies) áp dụng các phương pháp RE tiên tiến (như Prototype-Driven RE) vào một bài toán cụ thể và quy mô như *Phân loại sản phẩm Thương mại điện tử*, để đánh giá tính khả thi và đo lường độ hiệu quả thực tế.

2. **Thiếu hướng dẫn đặc tả NFRs cho các mô hình "Hộp đen" (Black-box Models):**
   Mặc dù giới học thuật thừa nhận tầm quan trọng của các yêu cầu phi chức năng (NFRs) như Khả năng giải thích (Explainability), nhưng lại thiếu các hướng dẫn cụ thể về cách chuyển đổi (translate) nhu cầu minh bạch của người dùng thành các chỉ số đo lường hoặc tính năng hệ thống đối với các mô hình phức tạp và độ chính xác cao như Mạng nơ-ron tích chập (CNN). Khoảng trống lớn nằm ở việc dung hòa sự mâu thuẫn (trade-off) giữa độ chính xác và khả năng giải thích.

3. **Chưa có cấu trúc rõ ràng cho sự hợp tác Người-AI (Human-in-the-Loop) trong Elicitation:**
   Các nghiên cứu cho thấy sự cần thiết của sự tham gia của con người trong quy trình AI, nhưng việc tận dụng cơ chế Human-in-the-Loop kết hợp với Nguyên mẫu (Prototype) làm công cụ để khơi gợi (elicit) các yêu cầu ẩn từ nhiều nhóm stakeholder (Seller, Admin, Data Scientist) vẫn chưa được khai thác và cấu trúc hóa sâu sắc.

**Đóng góp của nghiên cứu:** Nghiên cứu này sẽ lấp đầy các khoảng trống trên bằng cách mang phương pháp *Prototype-Driven Requirements Engineering* vào thực nghiệm trực tiếp trong bài toán *E-Commerce Product Categorization*, tập trung đo lường cách tiếp cận này giúp giải quyết bài toán đặc tả dữ liệu và NFRs (Explainability) cho mô hình CNN.
