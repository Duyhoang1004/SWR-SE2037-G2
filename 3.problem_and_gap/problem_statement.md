# Problem Statement

Trong lĩnh vực thương mại điện tử (E-commerce), việc phân loại sản phẩm tự động bằng Trí tuệ nhân tạo (AI), đặc biệt là các mô hình Học sâu (Deep Learning) như Mạng Nơ-ron Tích chập (CNN), đang trở thành một giải pháp thiết yếu để giảm tải công sức phân loại thủ công cho người bán (merchants) và tăng cường trải nghiệm tìm kiếm cho người mua. 

Tuy nhiên, việc phát triển các hệ thống AI này thường gặp thất bại khi đưa vào thực tế (production) không phải do thuật toán yếu kém, mà do sự thiếu hụt nghiêm trọng trong quy trình Kỹ thuật Yêu cầu (Requirements Engineering - RE). Cụ thể, vấn đề bao gồm:

1. **Sự không tương thích của RE truyền thống:** Các phương pháp RE truyền thống vốn được thiết kế cho phần mềm tất định (deterministic), không thể xử lý được bản chất dữ liệu dẫn dắt (data-driven) và đầu ra mang tính xác suất của mô hình ML/DL. 
2. **Khó khăn trong khơi gợi và đặc tả NFRs:** Việc xác định các Yêu cầu phi chức năng (NFRs) đặc thù của AI như tính công bằng (Fairness), khả năng giải thích (Explainability) và chất lượng dữ liệu (Data Quality) gặp nhiều khó khăn. Khách hàng thường không biết diễn đạt kỳ vọng của họ, dẫn đến sự lệch pha giữa mô hình (thường là "hộp đen" - black-box) và nhu cầu minh bạch của người dùng.
3. **Khoảng cách giao tiếp:** Thiếu một cơ chế hợp tác hiệu quả giữa các bên liên quan (người bán, admin) và đội ngũ phát triển AI/Data Scientists để cùng nhau tinh chỉnh yêu cầu liên tục dựa trên dữ liệu thực tế.

Tóm lại, bài toán đặt ra là: *Làm thế nào để xây dựng và tùy biến một quy trình Kỹ thuật Yêu cầu một cách có hệ thống, giúp thu thập và đặc tả chính xác các yêu cầu (đặc biệt là yêu cầu dữ liệu và yêu cầu phi chức năng) cho một hệ thống AI phân loại sản phẩm thương mại điện tử, nhằm cân bằng giữa độ chính xác của thuật toán và sự tin tưởng của người dùng?*
