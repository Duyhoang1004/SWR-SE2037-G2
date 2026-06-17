# Paper 12 Summary

## Citation

**Tên bài:** Status Quo and Problems of Requirements Engineering for Machine Learning: Results from an International Survey  
**Tác giả:** Antonio Pedro Santos Alves, Marcos Kalinowski, và các đồng tác giả  
**Năm:** 2023  
**Nguồn:** PROFES 2023 (International Conference on Product-Focused Software Process Improvement)  
**DOI/Link:** https://arxiv.org/abs/2310.06726 | https://arxiv.org/pdf/2310.06726.pdf

## Problem

Bài báo này tìm hiểu về **Requirements Engineering (RE)** trong các dự án dùng Machine Learning (ML).

Ngắn gọn thì bài báo này muốn trả lời 2 câu hỏi:

1. Người ta đang làm RE trong dự án ML như thế nào?
2. Những vấn đề khó khăn chính khi làm RE cho hệ thống ML là gì?

## Method

Bài báo dùng phương pháp **khảo sát quốc tế**.

- Có **188 câu trả lời đầy đủ** từ **25 quốc gia** .

Bài báo tập trung vào 2 câu hỏi nghiên cứu:
- **RQ1:** Thực hành RE hiện nay trong hệ thống ML là gì?
- **RQ2:** Những vấn đề chính liên quan đến RE trong hệ thống ML là gì?

## Dataset

Dữ liệu của bài báo không phải là dataset ảnh hay dữ liệu sản phẩm, mà là **dữ liệu khảo sát từ con người**.

| Đặc điểm | Chi tiết |
|----------|----------|
| **Nguồn dữ liệu** | Khảo sát quốc tế |
| **Số người tham gia** | 188 |
| **Số quốc gia** | 25 |
| **Loại dữ liệu** | Câu trả lời về thực hành RE trong dự án ML |

## Evaluation

Bài báo không đánh giá bằng accuracy như bài toán ML.  
Thay vào đó, bài báo đánh giá bằng:

- Tỷ lệ lựa chọn của người tham gia.
- Phân tích thống kê.
- Phân tích chủ đề từ câu trả lời mở .

Các kết quả được tổng hợp theo từng nhóm vấn đề và từng thực hành RE.

## Results

Kết quả chính của bài báo:

### 1. Ai thường làm RE trong dự án ML?
- Chủ yếu là **project leaders** và **data scientists**
- **Requirements engineers** không phải là người làm chính trong nhiều dự án .

### 2. Cách ghi lại yêu cầu phổ biến là gì?
- Phổ biến nhất là **interactive notebooks** như Jupyter Notebook
- Ngoài ra còn có user stories và requirements lists .

### 3. Những yêu cầu phi chức năng nào được chú ý nhiều nhất?
- **Data quality**
- **Model reliability**
- **Model explainability** .

### 4. Khó khăn chính là gì?
- Quản lý kỳ vọng của khách hàng
- Làm cho yêu cầu phù hợp với dữ liệu có sẵn
- Thiếu hiểu biết về nghiệp vụ
- Mục tiêu và yêu cầu chưa rõ
- Khách hàng tham gia chưa đủ nhiều .

## Limitations

Bài báo cũng có một số hạn chế:

1. Kết quả dựa trên khảo sát, nên phụ thuộc vào câu trả lời của người tham gia. Thiếu empirical evidence (bằng chứng thực nghiệm).
2. Dù có 188 người từ 25 quốc gia, nhưng vẫn chưa thể đại diện cho toàn bộ ngành.
3. Đây là nghiên cứu về RE cho ML nói chung, chưa đi riêng vào một bài toán cụ thể như phân loại sản phẩm e-commerce.

## Relevance to our topic

Bài báo này rất liên quan đến đề tài của nhóm vì nó giúp xác định **phần Requirements Engineering** cho hệ thống AI phân loại sản phẩm.

Từ bài báo này, nhóm có thể rút ra:

- **Ai nên tham gia làm RE:** project leader, data scientist, business stakeholder.
- **Cần ghi rõ yêu cầu gì:** accuracy, data quality, explainability, reliability.
- **Cần chú ý khó khăn nào:** dữ liệu không đủ, yêu cầu mơ hồ, khách hàng kỳ vọng quá cao.
- **Cần dùng cách ghi yêu cầu phù hợp:** có thể dùng notebook, tài liệu yêu cầu ngắn gọn, hoặc prototype.

## Possible improvement

Nhóm có thể mở rộng từ bài báo này bằng cách:

1. Làm một bộ **RE riêng cho hệ thống phân loại sản phẩm e-commerce**.
2. Xác định rõ **functional requirements** và **non-functional requirements** cho hệ thống AI.
3. Đề xuất cách phối hợp giữa **business team, data team, và kỹ thuật**.
4. Thử nghiên cứu thêm xem trong e-commerce thì những yêu cầu nào quan trọng nhất.
5. Kiểm tra xem AI có thể hỗ trợ viết yêu cầu ban đầu hay không.