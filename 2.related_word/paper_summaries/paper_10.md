# Paper 10 Summary

## Citation

**Tên bài:** Requirements Elicitation for Prototype-driven AI Engineering  
**Tác giả:** Various authors  
**Năm:** 2025  
**Nguồn:** CEUR Workshop Proceedings, Vol. 3959  
**DOI/Link:** https://ceur-ws.org/Vol-3959/PT-paper4.pdf

## Problem

Bài báo giải quyết một vấn đề rất phổ biến trong Requirements Engineering cho AI: **stakeholder thường không biết diễn đạt rõ yêu cầu khi hệ thống AI còn đang ở giai đoạn ý tưởng**.  
Với các hệ thống AI, yêu cầu ban đầu thường mơ hồ, khó xác định đầy đủ ngay từ đầu, và dễ bỏ sót các nhu cầu ẩn nếu chỉ hỏi theo cách truyền thống .

Nói đơn giản, bài báo muốn trả lời câu hỏi:  
**làm sao elicitation requirements cho AI system một cách có cấu trúc, để nhiều stakeholder khác nhau cùng đóng góp và cùng làm rõ yêu cầu dần dần?**.

## Method

Bài báo đề xuất một phương pháp elicitation dựa trên prototype, được thiết kế riêng cho AI engineering.  
Phương pháp này đi theo **3 giai đoạn**, cho phép stakeholder xây dựng dần trên ý tưởng của nhau thay vì chỉ trả lời riêng lẻ.
Quy trình chính:
1. **Khởi tạo bằng prototype** để stakeholder dễ hình dung hệ thống.
2. **Trao đổi và bổ sung qua nhiều vòng phản hồi**, giúp làm rõ yêu cầu và phát hiện yêu cầu ẩn.
3. **Tổng hợp yêu cầu cuối cùng** thành bộ requirements có cấu trúc hơn.

Điểm mạnh của cách làm này là nó giúp tránh tình trạng **unknown unknowns**, tức là những yêu cầu mà stakeholder ban đầu chưa nghĩ ra .

## Dataset

Bài báo không dùng dataset kiểu ảnh hay văn bản lớn, mà dùng dữ liệu thu được từ quá trình **thực nghiệm elicitation với stakeholder đa ngành** .

| Đặc điểm | Chi tiết |
|----------|----------|
| **Nguồn dữ liệu** | Phản hồi của stakeholders khi làm việc với prototype |
| **Loại dữ liệu** | Requirements ban đầu được elicitate |
| **Số lượng requirements thu được** | 23 |
| **Thành phần** | 9 Functional Requirements, 4 Performance Requirements, 8 Quality Aspects, 2 Constraints |

## Evaluation

Bài báo đánh giá phương pháp dựa trên số lượng và loại requirements thu được từ thực nghiệm.  
Kết quả cho thấy phương pháp đã giúp gợi ý được **23 requirements ban đầu** từ stakeholder đa ngành.

Các nhóm yêu cầu thu được gồm:
- **9 FRs**
- **4 Performance requirements**
- **8 Quality aspects**
- **2 Constraints** .

Điều này cho thấy phương pháp không chỉ thu được yêu cầu chức năng, mà còn giúp lộ ra các yêu cầu phi chức năng và ràng buộc quan trọng của hệ thống AI.

## Results

Kết quả chính của bài báo là đề xuất thành công một phương pháp elicitation dựa trên prototype cho AI systems.  
Phương pháp này giúp stakeholder từ nhiều lĩnh vực khác nhau đóng góp dần, làm rõ ý tưởng, và cùng hình thành bộ yêu cầu đầy đủ hơn .

Các kết quả đáng chú ý:
- Có thể elicitate được yêu cầu từ stakeholder đa ngành.
- Phương pháp hỗ trợ phát hiện yêu cầu ẩn tốt hơn.
- Bộ yêu cầu thu được bao gồm cả FR, performance, quality aspects và constraints.

## Limitations

Bài báo vẫn có một số hạn chế:
1. Mới ở mức phương pháp đề xuất và thực nghiệm ban đầu.
2. Kết quả phụ thuộc vào ngữ cảnh và nhóm stakeholder tham gia.
3. Chưa chứng minh rằng phương pháp sẽ áp dụng tốt cho mọi loại AI system .

## Relevance to our topic

Bài báo này rất phù hợp với đề tài **AI-assisted e-commerce product categorization** vì hệ thống của nhóm cũng có nhiều stakeholder khác nhau, như:
- **Seller**
- **Buyer**
- **Admin**

Phương pháp prototype-driven elicitation có thể giúp nhóm:
- cho seller xem prototype để góp ý về nhập sản phẩm và gợi ý danh mục,
- cho buyer thử tìm kiếm và phân loại sản phẩm,
- cho admin thử kiểm soát, sửa category và quản lý loại.

Từ bài báo này, nhóm có thể rút ra rằng:
- cần elicitation theo nhiều vòng, không chỉ hỏi một lần,
- prototype giúp stakeholder hiểu hệ thống AI rõ hơn,
- requirements cho AI không chỉ là chức năng, mà còn gồm performance, quality và constraints .

## Possible improvement

Nếu áp dụng vào đề tài nhóm, bài báo này có thể được mở rộng bằng cách:
1. Thiết kế prototype cho từng nhóm stakeholder.
2. Tách riêng requirements của seller, buyer và admin.
3. Làm thêm vòng feedback để phát hiện yêu cầu ẩn.
4. Thử xác định các quality aspects riêng cho product categorization, như accuracy, explainability, latency và usability.
5. Kết hợp phương pháp này với một framework RE đầy đủ hơn cho AI-based e-commerce systems.

