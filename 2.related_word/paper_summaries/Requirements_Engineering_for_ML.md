# Paper Summary – Requirements Engineering for Machine Learning: Perspectives from Data Scientists

---

## Citation

| Trường | Thông tin |
|---|---|
| **Tên bài báo** | Requirements Engineering for Machine Learning: Perspectives from Data Scientists |
| **Tác giả** | Andreas Vogelsang, Markus Borg |
| **Năm công bố** | 2019 (August 13) |
| **Loại tài liệu** | Workshop Paper – REFSQ 2019 / International Requirements Engineering Conference Workshop (AIRE) |
| **Link tài liệu** | https://arxiv.org/abs/1908.04674 |
| **Cơ quan công tác**| Technische Universität Berlin (Đức) và RISE Research Institutes of Sweden AB (Thụy Điển) |

---

## 1. Research Objective – Mục tiêu nghiên cứu

Nghiên cứu này được thực hiện trong bối cảnh các cấu phần Học máy (Machine Learning - ML) ngày càng được tích hợp sâu vào các ứng dụng phần mềm thế giới thực. Tuy nhiên, sự dịch chuyển mô hình phát triển từ "viết mã lệnh" (coding-driven) sang "huấn luyện dữ liệu" (training-driven) đang đặt ra nhiều thách thức chưa có lời giải cho các kỹ sư phần mềm.

Mục tiêu cụ thể của nhóm tác giả bao gồm hai phương diện:
* **Tầng lý thuyết và nhận thức:** Định hình và phân tích rõ nét các đặc tính cũng như thách thức độc nhất vô nhị của quy trình Kỹ nghệ Yêu cầu (Requirements Engineering - RE) dành riêng cho các hệ thống dựa trên nền tảng Học máy.
* **Tầng thực nghiệm:** Thu thập, mổ xẻ góc nhìn trực tiếp từ các chuyên gia Khoa học Dữ liệu (Data Scientists)—những người trực tiếp xây dựng mô hình nhưng thường đứng ngoài quy trình RE truyền thống—để hiểu cách họ tiếp cận việc khơi gợi, đặc tả, và đảm bảo các yêu cầu/kỳ vọng của hệ thống. Từ đó, đề xuất những đóng góp đầu tiên hướng tới một phương pháp luận RE chuẩn hóa cho ML.

---

## 2. Main Problem – Vấn đề nghiên cứu

Bài báo tập trung làm rõ những điểm nghẽn nghiêm trọng khi áp dụng các nguyên lý Kỹ nghệ Yêu cầu (RE) truyền thống vào các hệ thống phần mềm nhúng học máy:

| # | Vấn đề | Mô tả chi tiết |
|---|---|---|
| 1 | **Sự dịch chuyển mô hình phát triển** | Trong phần mềm truyền thống, lập trình viên tạo ra hành vi hệ thống bằng các quy tắc logic tường minh (Deductive). Ngược lại, hệ thống ML tự suy diễn ra các quy tắc dựa trên dữ liệu huấn luyện (Inductive). RE truyền thống hoàn toàn thiếu các công cụ để đặc tả một hành vi hệ thống mang tính "suy diễn và bất định" như vậy từ giai đoạn đầu. |
| 2 | **Sự mơ hồ giữa tính năng và độ chính xác** | Khách hàng thường đưa ra các yêu cầu chức năng (Functional Requirements) theo kiểu định tính chung chung (ví dụ: "Hệ thống phải nhận diện được biển báo giao thông"). Tuy nhiên, đối với ML, một tính năng luôn gắn liền với các chỉ số phân phối xác suất và độ chính xác (Accuracy, Precision, Recall). Kỹ sư RE truyền thống không biết cách hoán đổi các mong muốn này thành các mục tiêu định lượng khả thi cho Data Scientist. |
| 3 | **Sự bùng nổ của các Yêu cầu Chất lượng Mới (NFRs)** | Hệ thống ML sinh ra các thuộc tính chất lượng phi chức năng hoàn toàn mới và cực kỳ phức tạp như: Tính có thể giải thích được (Explainability), Tính không phân biệt đối xử / Công bằng (Fairness), và các ràng buộc pháp lý đặc thù về quyền riêng tư dữ liệu (ví dụ: GDPR). Quy trình RE cũ không có sẵn khung biểu đạt cho các thuộc tính này. |
| 4 | **Khoảng cách giao tiếp liên ngành** | Có một hố sâu ngăn cách về mặt thuật ngữ và tư duy giữa Kỹ sư Yêu cầu (Requirements Engineer - tập trung vào bối cảnh bài toán của khách hàng) và Nhà khoa học dữ liệu (Data Scientist - tập trung vào tối ưu hóa thuật toán và dữ liệu), dẫn đến việc phân tách kỳ vọng hệ thống bị sai lệch. |

---

## 3. Proposed Method – Phương pháp đề xuất

Để khám phá và giải quyết bài toán, nhóm tác giả sử dụng phương pháp **Nghiên cứu Phỏng vấn Khám phá (Exploratory Interview Study)**, được thiết kế dựa trên các hướng dẫn thực hành chuẩn hóa của phần mềm thực nghiệm.

### 3.1. Cấu trúc thiết kế nghiên cứu hành động

Tác giả thiết kế một bộ khung câu hỏi phỏng vấn bán cấu trúc xoay quanh 3 trụ cột cốt lõi của kỹ nghệ yêu cầu (RE) nhưng dưới lăng kính của ML:
* **Khơi gợi yêu cầu (Elicitation):** Làm thế nào để thu thập các mong muốn của khách hàng đối với một hệ thống không thể xác định trước 100% hành vi?
* **Đặc tả yêu cầu (Specification):** Tài liệu hóa các yêu cầu về dữ liệu, tính năng và các ràng buộc của mô hình như thế nào để Data Scientist có thể làm việc được?
* **Đảm bảo yêu cầu (Assurance / Validation):** Làm sao để thẩm định và kiểm tra xem mô hình được huấn luyện ra đã thực sự đáp ứng đúng bài toán kinh doanh ban đầu?

### 3.2. Quá trình triển khai và Thu thập thông tin

Phương pháp này chủ động tiếp cận sâu vào đối tượng Nhà khoa học dữ liệu (Data Scientists) thông qua các cuộc phỏng vấn chuyên sâu có ghi âm, sau đó tiến hành mã hóa dữ liệu định tính (Qualitative Coding) để trích xuất ra các kết luận cốt lõi, thay vì chỉ khảo sát các kỹ sư phần mềm truyền thuần túy.

---

## 4. Dataset Used – Bộ dữ liệu sử dụng

Nghiên cứu mang tính định chất (Qualitative Research), nguồn dữ liệu đầu vào thực nghiệm bao gồm:
* Đối tượng khảo sát là **4 nhà khoa học dữ liệu cấp cao (Data Scientists)** hoạt động độc lập tại các tổ chức, doanh nghiệp công nghệ khác nhau ở Đức và Thụy Điển, có kinh nghiệm dày dặn trong việc triển khai các dự án ML thực tế vào sản xuất.
* Dữ liệu thô là các **bản ghi âm và biên bản phỏng vấn bán cấu trúc** tập trung vào trải nghiệm thực tế, các thất bại và bài học kinh nghiệm của họ khi phải đối mặt với các bản đặc tả yêu cầu từ phía khách hàng hoặc từ các kỹ sư phần mềm truyền thống chuyển sang.

---

## 5. Baselines Compared – Các cơ sở so sánh

Do đây là bài báo tiên phong mở đường định hình một nhánh nghiên cứu mới trong kỹ nghệ yêu cầu, tác giả không so sánh với các thuật toán cụ thể.

Cơ sở đối chứng (Baseline) duy nhất của bài báo là **Khung Kỹ nghệ Yêu cầu truyền thống (Traditional RE Framework)**—nơi coi phần mềm là một thực thể tất định (deterministic system), hoạt động dựa trên mã nguồn viết tay và có đặc tả ca sử dụng (Use Cases) đóng khung cố định. Bài báo đối chiếu để chỉ ra những điểm sụp đổ của baseline này khi va chạm với các dự án AI/ML.

---

## 6. Evaluation Metrics – Tiêu chí đánh giá

Hiệu quả của các phát hiện trong bài nghiên cứu được thẩm định dựa trên:

* **Tính thực tế của thông tin (Empirical Validity):** Các thách thức được chỉ ra phải phản ánh đúng thực trạng nghẽn cổ chai trong công nghiệp mà các Data Scientist đang gặp phải.
* **Khả năng hành động của giải pháp (Actionability):** Các đề xuất thay đổi quy trình RE phải có tính khả thi, giúp các kỹ sư yêu cầu biết mình cần phải học thêm gì và làm gì trong một dự án ML.
* **Mức độ bao phủ (Completeness of Perspectives):** Khung phân tích phải bao quát đủ cả 3 khía cạnh: Đo lường hiệu năng (Performance measures), Thuộc tính chất lượng mới (New quality requirements), và Tích hợp quy trình (Process integration).

---

## 7. Main Results – Kết quả chính

Thông qua phân tích định tính từ các cuộc phỏng vấn, bài báo rút ra **3 kết luận mang tính nền tảng** bắt buộc phải thay đổi trong quy trình RE dành cho các hệ thống Machine Learning:

| Trụ cột kết quả | Chi tiết nội dung chuyển đổi bắt buộc |
|---|---|
| **1. Hiểu sâu sắc các bộ đo hiệu năng ML** | Kỹ sư RE không thể đưa ra các yêu cầu chức năng chung chung nữa. Họ bắt buộc phải hiểu và biết cách sử dụng các bộ đo hiệu năng như *Accuracy, Precision, Recall, F-score, hay ROC-AUC* để viết các yêu cầu chức năng dưới dạng mục tiêu định lượng (Ví dụ: Thay vì yêu cầu "Hệ thống phải phát hiện lỗi", phải viết "Hệ thống phải đạt Recall tối thiểu 95% trên tập dữ liệu kiểm thử chuẩn"). |
| **2. Làm quen với các thuộc tính chất lượng mới** | RE cho ML phải chủ động đưa các thuộc tính phi chức năng mới vào tài liệu đặc tả ngay từ đầu: <br>- *Explainability (Tính giải thích được):* Mô hình đưa ra quyết định dựa trên cơ sở nào?<br>- *Fairness (Tính công bằng):* Đảm bảo dữ liệu huấn luyện không chứa định kiến gây phân biệt đối xử.<br>- *Ràng buộc pháp lý:* Tuân thủ quyền được giải thích của người dùng và các quy định bảo mật dữ liệu toàn cầu (GDPR). |
| **3. Tích hợp đặc thù ML vào quy trình RE** | Quy trình RE phải chấp nhận tính "thử nghiệm" (experimentation). Khách hàng và đội ngũ phát triển không thể biết chắc mục tiêu định lượng có đạt được hay không cho đến khi Data Scientist thực sự lấy được dữ liệu và huấn luyện thử mô hình. Quy trình RE phải chuyển từ thiết kế "đóng băng yêu cầu" sang thiết kế lặp, tiến hóa song song với dữ liệu. |

---

## 8. Limitations – Hạn chế

| # | Hạn chế | Phân tích chi tiết |
|---|---|---|
| 1 | **Cỡ mẫu phỏng vấn nhỏ (Small Sample Size)** | Nghiên cứu mới chỉ tiến hành phỏng vấn chuyên sâu với **4 chuyên gia khoa học dữ liệu**. Mặc dù thông tin thu được rất sâu sắc, nhưng số lượng mẫu này là quá nhỏ để có thể đại diện hoàn toàn cho toàn bộ cộng đồng Data Science trên thế giới. |
| 2 | **Định kiến chủ quan (Subjective Bias)** | Kết quả nghiên cứu phụ thuộc nhiều vào nhận thức, trải nghiệm cá nhân và cách diễn đạt của các đối tượng được phỏng vấn, cũng như quy mô các dự án mà họ từng tham gia (có thể chưa bao phủ hết các miền ứng dụng đặc thù như y tế hay hàng không). |

---

## 9. Future Work – Hướng phát triển tương lai

Nhóm tác giả đề xuất các bước đi tiếp theo để hoàn thiện nghiên cứu:

* **Mở rộng quy mô khảo sát:** Thực hiện các cuộc khảo sát trên diện rộng (Large-scale Surveys) với hàng trăm Data Scientists và Kỹ sư phần mềm để kiểm chứng lại các giả thuyết và thách thức được phát hiện trong bài báo này.
* **Xây dựng Framework RE4ML hoàn chỉnh:** Phát triển một phương pháp luận hoặc một bộ hướng dẫn thực hành kỹ nghệ yêu cầu cụ thể, cung cấp các mẫu tài liệu (templates) đặc tả yêu cầu có sẵn các trường dành cho dữ liệu và chỉ số ML.
* **Nghiên cứu các kỹ thuật thẩm định yêu cầu tự động:** Tìm kiếm giải pháp kiểm thử hoặc thẩm định tự động xem các mô hình ML sau khi ra lò có khớp với các mục tiêu yêu cầu ban đầu của khách hàng hay không.

---

## 10. Possible Research Gaps – Khoảng trống nghiên cứu

| # | Research Gap | Gợi ý cải tiến / Hướng khai thác cho nhóm |
|---|---|---|
| 1 | **Sự thiếu hụt các mẫu đặc tả yêu cầu dữ liệu (Data Requirements Template)** | Bài báo nhấn mạnh RE cho ML là dựa trên dữ liệu, nhưng chưa đưa ra được một cấu trúc tài liệu mẫu để kỹ sư RE viết yêu cầu cho dữ liệu (ví dụ: yêu cầu về độ sạch, phân phối dữ liệu, số lượng nhãn). Nhóm có thể đề xuất một khung framework hoặc một mẫu đặc tả kỹ thuật dữ liệu đầu vào (Data Specification Standard) phục vụ cho dự án. |
| 2 | **Bài toán mâu thuẫn giữa Trade-off các Yêu cầu chất lượng trong ML** | Trong thực tế, có sự mâu thuẫn gay gắt giữa các yêu cầu mới (ví dụ: Mô hình có *Accuracy* càng cao thì thường càng phức tạp, dẫn đến tính *Explainability* càng thấp). Bài báo chưa chỉ ra cách giải quyết mâu thuẫn này. Nhóm có thể nghiên cứu một mô hình ra quyết định (Decision-making model) để giúp tối ưu hóa và cân bằng (trade-off) giữa các thuộc tính NFRs của mô hình ML. |
| 3 | **Cơ chế chuyển dịch tự động từ Ngôn ngữ kinh doanh sang Chỉ số ML** | Khách hàng luôn nói ngôn ngữ kinh doanh, Data Scientist nói ngôn ngữ toán học. Bài báo mới chỉ dừng ở mức khuyên "kỹ sư RE hãy học chỉ số ML đi". Nhóm có thể nghiên cứu ứng dụng LLM (Generative AI) làm công cụ trung gian dịch tự động (Mapping) các yêu cầu nghiệp vụ định tính của khách hàng thành các ngưỡng chỉ số Precision/Recall kỹ thuật tương ứng. |

---

## Relevance to Our Topic – Liên quan đến đề tài nhóm

Bài báo này sở hữu mức độ liên quan **nền tảng và đặc biệt quan trọng** cho các đề tài nhóm về SE4AI / MLOps:

* **Sách gối đầu giường về mặt lý thuyết:** Cung cấp đầy đủ các luận điểm khoa học vững chắc để nhóm đưa vào phần *Tổng quan nghiên cứu (Related Work)* nhằm giải thích vì sao nhóm không dùng các quy trình phần mềm thông thường mà phải đề xuất quy trình mới cho hệ thống AI của mình.
* **Định hướng tư duy thiết kế hệ thống:** Giúp nhóm hiểu cách thiết lập các mục tiêu dự án ngay từ đầu bằng các chỉ số toán học (F1-score, Recall) thay vì các câu mô tả mơ hồ, tránh được việc thất bại khi nghiệm thu sản phẩm.
