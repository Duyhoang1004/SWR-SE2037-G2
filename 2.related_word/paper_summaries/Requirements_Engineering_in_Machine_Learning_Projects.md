# Paper Summary – Requirements Engineering in Machine Learning Projects

---

## Citation

| Trường | Thông tin |
|---|---|
| **Tên bài báo** | Requirements Engineering in Machine Learning Projects |
| **Tác giả** | Ana Gjorgjevikj, Kostadin Mishev, Ljupcho Antovski, Dimitar Trajanov |
| **Năm công bố** | 2023 (July 12) |
| **Loại tài liệu** | Journal Paper – IEEE Access |
| **DOI** | 10.1109/ACCESS.2023.3294840 |
| **Link tài liệu** | https://ieeexplore.ieee.org/document/10182245 |
| **Cơ quan công tác**| Khoa Khoa học Máy tính và Kỹ nghệ, Đại học Ss. Cyril and Methodius tại Skopje, Bắc Macedonia |

---

## 1. Research Objective – Mục tiêu nghiên cứu

Nghiên cứu này xuất phát từ thực trạng việc phát triển và bảo trì các hệ thống Học máy (Machine Learning - ML) cấp độ vận hành (production-level) đang gặp khủng hoảng do thiếu các quy trình kỹ nghệ phần mềm (Software Engineering - SE) và thực hành tốt (best practices) chuẩn hóa. 

Mục tiêu cụ thể của nhóm tác giả tập trung vào hai phương diện cốt lõi:
* **Tầng hệ thống hóa:** Thực hiện một nghiên cứu tổng quan văn liệu có hệ thống (Systematic Literature Review - SLR) để thiết lập một bức tranh toàn cảnh, phân loại và cấu trúc lại toàn bộ các thách thức, thực hành tốt (best practices), phương pháp và công cụ hiện có trong kỹ nghệ yêu cầu dành cho ML (RE4ML).
* **Tầng đề xuất quy trình:** Xây dựng một quy trình Kỹ nghệ Yêu cầu tích hợp chuyên biệt cho các dự án ML (gọi là **Integrated ML RE Process Model**), ánh xạ trực tiếp từ các giai đoạn kỹ nghệ yêu cầu truyền thống sang các giai đoạn đặc thù trong vòng đời phát triển hệ thống ML (từ thu thập dữ liệu, huấn luyện đến vận hành).

---

## 2. Main Problem – Vấn đề nghiên cứu

Bài báo mổ xẻ sâu sắc bản chất khác biệt cốt lõi giữa phần mềm truyền thống và hệ thống ML, từ đó chỉ ra những điểm sụp đổ của quy trình RE cũ:

| # | Vấn đề | Mô tả chi tiết |
|---|---|---|
| 1 | **Sự phụ thuộc vào dữ liệu (Data Dependency)** | Hành vi của hệ thống phần mềm truyền thống được định nghĩa bằng mã nguồn logic tường minh. Ngược lại, hành vi của hệ thống ML hoàn toàn do dữ liệu và cấu trúc mô hình quyết định. Sự thay đổi nhỏ về phân phối dữ liệu đầu vào có thể làm đảo lộn hành vi hệ thống, khiến việc đóng băng các yêu cầu chức năng từ đầu trở nên bất khả thi. |
| 2 | **Sự bùng nổ của các Yêu cầu Phi chức năng (NFRs) đặc thù** | Hệ thống ML đòi hỏi khắt khe các thuộc tính chất lượng phi chức năng hoàn toàn mới mà phần mềm truyền thống chưa bao giờ phải đặc tả chi tiết như: *Explainability (Tính giải thích được), Fairness (Tính công bằng/Không định kiến), Robustness (Tính bền vững trước dữ liệu nhiễu), Transparency (Tính minh bạch), và Data Privacy (Quyền riêng tư dữ liệu).* |
| 3 | **Sự bất định của kết quả đầu ra (Non-determinism)** | Đầu ra của mô hình ML mang tính xác suất và không bao giờ chính xác 100%. Các bên liên quan (khách hàng, quản lý) thường áp đặt tư duy tất định (deterministic) của phần mềm cũ vào ML, tạo ra những kỳ vọng phi thực tế và không thể nghiệm thu dự án. |
| 4 | **Sự đứt gãy vòng đời phát triển (Lifecycle Disconnection)** | Quy trình RE truyền thống kết thúc sau khi đặc tả xong yêu cầu phần mềm. Trong khi đó, vòng đời ML là một chuỗi lặp không ngừng nghỉ (từ thu thập dữ liệu -> thử nghiệm mô hình -> triển khai -> giám sát độ lệch mô hình - data/concept drift). RE truyền thống hoàn toàn bị ngắt kết nối khỏi chu trình động này. |

---

## 3. Proposed Method – Phương pháp đề xuất

Để giải quyết triệt để vấn đề, nhóm tác giả đề xuất **Mô hình Quy trình Kỹ nghệ Yêu cầu tích hợp cho các dự án Học máy (Integrated ML RE Process Model)**. Quy trình này phân rã và tái cấu trúc các hoạt động RE truyền thống thành các hành động kỹ thuật tương thích với vòng đời ML.

### 3.1. Cấu trúc Mô hình Quy trình Tích hợp

Quy trình được thiết kế lặp vòng tròn (Iterative) bao gồm 4 giai đoạn cốt lõi:

* **1. Khơi gợi yêu cầu ML (ML Requirements Elicitation):** Tập trung vào việc xác định mục tiêu kinh doanh, hiểu bối cảnh bài toán, và quan trọng nhất là khơi gợi các yêu cầu về **Dữ liệu khả dụng** (nguồn dữ liệu, số lượng, chất lượng, nhãn dữ liệu) song song với các yêu cầu chức năng.
* **2. Phân tích và Thương lượng yêu cầu (Analysis & Negotiation):** Đánh giá tính khả thi của dự án dựa trên dữ liệu hiện có, thực hiện phân tích các điểm đánh đổi (*Trade-off Analysis*) giữa độ chính xác (Accuracy) và các thuộc tính khác như tính giải thích được (Explainability) hoặc tài nguyên tính toán cần thiết.
* **3. Đặc tả yêu cầu ML (ML Requirements Specification):** Tài liệu hóa các yêu cầu thành 3 nhóm rõ rệt: *Yêu cầu hệ thống*, *Yêu cầu phần mềm* và *Yêu cầu về Dữ liệu* (Data Requirements Specification). Đặc tả cụ thể các ngưỡng chỉ số hiệu năng (KPIs toán học) và các ràng buộc phi chức năng (NFRs).
* **4. Thẩm định yêu cầu ML (ML Requirements Validation):** Đảm bảo tập yêu cầu đã định hình là chính xác và có thể kiểm thử được thông qua việc xây dựng các bộ dữ liệu test chuẩn (Gold Standard Datasets) và các kịch bản kiểm thử mô hình liên tục.

---

## 4. Dataset Used – Bộ dữ liệu sử dụng

Bài báo này thuộc dạng nghiên cứu tổng quan hệ thống kết hợp đề xuất khung lý thuyết khoa học thiết kế (Design Science Framework):
* **Dữ liệu đầu vào cho nghiên cứu (SLR Dataset):** Nhóm tác giả đã tiến hành rà soát, sàng lọc một tập dữ liệu gồm **103 bài báo nghiên cứu khoa học cốt lõi** xuất bản trong giai đoạn từ năm 2011 đến năm 2022 từ các cơ sở dữ liệu lớn (Scopus, IEEE Xplore, ACM Digital Library, Web of Science) liên quan trực tiếp đến chủ đề Kỹ nghệ Yêu cầu cho Học máy để trích xuất dữ liệu thực trạng.
* **Kiểm chứng thực nghiệm:** Khung quy trình tích hợp sau đó được tác giả đối chiếu và chứng minh tính đúng đắn dựa trên các kịch bản dự án ML thế giới thực được vận hành trong công nghiệp phần mềm.

---

## 5. Baselines Compared – Các cơ sở so sánh

Bài báo tiến hành đối chiếu toàn diện mô hình đề xuất với hai nhóm cơ sở so sánh (Baselines):
* **Baseline 1: Khung Kỹ nghệ Yêu cầu Phần mềm truyền thống (Traditional SE RE - ví dụ: ISO/IEC/IEEE 29148):** Để chỉ ra sự thiếu hụt các thành phần quản lý dữ liệu, sự bất lực khi đối mặt với tính chất bất định và vòng đời lặp liên tục của ML.
* **Baseline 2: Các quy trình phát triển ML công nghiệp hiện tại (như CRISP-DM, SEMMA):** Tác giả chỉ ra rằng mặc dù các quy trình này quản lý tốt vòng đời dữ liệu và mô hình thuật toán, nhưng chúng hoàn toàn **bỏ trống giai đoạn Kỹ nghệ Yêu cầu (RE)** ở mức độ kỹ thuật hệ thống, dẫn đến việc thiếu định hướng mục tiêu kinh doanh và không kiểm soát được các rủi ro phi chức năng ngay từ đầu.

---

## 6. Evaluation Metrics – Tiêu chí đánh giá

Khung quy trình được đánh giá và chứng minh tính hiệu quả thông qua các tiêu chí hệ thống hóa nghiêm ngặt:

* **Mức độ bao phủ thách thức (Challenge Coverage):** Khả năng giải quyết trọn vẹn bao nhiêu phần trăm trong tổng số các rào cản kỹ thuật/vận hành đã được tìm thấy trong nghiên cứu SLR.
* **Tính toàn vẹn của thuộc tính chất lượng (NFR Integrity):** Khả năng định nghĩa và chuyển hóa các yêu cầu phi chức năng (Fairness, Robustness, Explainability) từ dạng định tính mơ hồ thành các tiêu chí có thể đo lường kỹ thuật.
* **Tính liên tục của vòng đời (Lifecycle Continuity):** Khả năng duy trì sự gắn kết (Traceability Links) giữa tập yêu cầu ban đầu với các hoạt động kiểm thử, giám sát mô hình ở giai đoạn vận hành sau này (MLOps).

---

## 7. Main Results – Kết quả chính

Bài báo mang lại các đóng góp có giá trị ứng dụng rất cao cho cộng đồng AI Engineering:

| Khía cạnh kết quả | Nội dung chi tiết |
|---|---|
| **Bản đồ phân loại thách thức (Taxonomy)** | Cấu trúc hóa thành công danh mục các thách thức RE4ML lớn nhất hiện nay, phân chia rõ rệt thành các nhóm: Thách thức về mặt dữ liệu, Thách thức về mô hình/thuật toán, Thách thức về nguồn nhân lực/giao tiếp và Thách thức về quy trình tổ chức. |
| **Bảng ánh xạ quy trình tích hợp** | Xây dựng thành công **Mô hình Quy trình Tích hợp** giúp định hướng cho kỹ sư phần mềm biết chính xác tại mỗi bước của quy trình RE truyền thống thì cần phải thực hiện hành động kỹ thuật tương ứng nào cho ML (Ví dụ: Khi viết đặc tả phần mềm, bắt buộc phải viết kèm *Data Specification* như độ mất cân bằng nhãn được phép, độ nhiễu tối đa của dữ liệu). |
| **Hệ thống hóa giải pháp và công cụ** | Tổng hợp và phân loại một bộ công cụ trợ giúp cùng các thực hành tốt (Best Practices) cho từng giai đoạn, giúp các đội ngũ dự án MLOps có thể áp dụng ngay để giải quyết các mâu thuẫn yêu cầu hệ thống. |

---

## 8. Limitations – Hạn chế

| # | Hạn chế | Phân tích chi tiết |
|---|---|---|
| 1 | **Tính kiểm chứng thực tế diện rộng** | Mặc dù quy trình đề xuất được xây dựng dựa trên dữ liệu tổng quan vững chắc từ 103 nghiên cứu, mô hình tích hợp này vẫn cần được triển khai thực nghiệm sâu rộng hơn trong các dự án công nghiệp quy mô lớn (Large-scale Industrial Evaluation) để đo lường chính xác chi phí overhead về thời gian/nhân lực mà nó tạo ra cho đội ngũ. |
| 2 | **Sự thay đổi quá nhanh của công nghệ AI** | Dữ liệu SLR thu thập chủ yếu từ giai đoạn 2011 - 2022, thời điểm mà các mô hình Học máy truyền thống (Deep Learning, CNN, RNN) chiếm ưu thế. Sự bùng nổ của Mô hình ngôn ngữ lớn (LLM) và Generative AI từ cuối năm 2022 trở đi có thể sinh ra thêm một số thuộc tính chất lượng và thách thức RE mới chưa được bao phủ hoàn toàn trong bài báo này. |

---

## 9. Future Work – Hướng phát triển tương lai

Các tác giả đề xuất ba hướng nghiên cứu tiếp theo:

* **Công cụ hóa quy trình (Tool Support):** Phát triển các phần mềm hoặc plugin hỗ trợ tự động hóa việc quản lý và theo dõi các yêu cầu trong dự án ML (ML Requirements Management Tools), tích hợp trực tiếp vào các nền tảng MLOps hiện có.
* **Mở rộng sang Generative AI / LLMs:** Tinh chỉnh và cập nhật mô hình quy trình tích hợp để thích ứng với các thách thức đặc thù của kỹ nghệ prompt và kiểm thử hệ thống dựa trên mô hình nền tảng (Foundation Models).
* **Xây dựng bộ chỉ số đánh giá chuẩn hóa (Standardized Metrics Framework):** Nghiên cứu sâu hơn để đưa ra một bảng các ngưỡng chỉ số hiệu năng chuẩn cho từng miền ứng dụng (ví dụ: y tế, tài chính, xe tự lái) để làm tài liệu tham khảo cố định cho kỹ sư RE khi thương lượng yêu cầu với khách hàng.

---

## 10. Possible Research Gaps – Khoảng trống nghiên cứu

Đây là các lỗ hổng nghiên cứu lớn được trích xuất từ bài báo mà bạn và nhóm có thể khai thác trực tiếp cho đề tài nghiên cứu của mình:

| # | Research Gap | Gợi ý cải tiến / Hướng khai thác cho nhóm |
|---|---|---|
| 1 | **Sự thiếu hụt các phương pháp Thẩm định Yêu cầu Dữ liệu tự động (Automated Data Requirements Validation)** | Bài báo chỉ ra tầm quan trọng của việc đặc tả yêu cầu dữ liệu, nhưng chưa có công cụ tự động kiểm tra xem tập dữ liệu thực tế thu thập về có thỏa mãn đúng các đặc tả yêu cầu đó hay không. Nhóm có thể nghiên cứu xây dựng một pipeline tự động (gắn liền với công cụ như Great Expectations hoặc TFX) để kiểm tra độ lệch cấu trúc dữ liệu so với tài liệu yêu cầu ban đầu. |
| 2 | **Quy trình RE dành riêng cho Foundation Models / LLM-based Systems** | Như đã nêu ở phần hạn chế, các tài liệu RE cũ chưa tối ưu cho LLM (nơi rủi ro về ảo tưởng - Hallucination, Prompt Injection, hay tính ngẫu nhiên của mô hình rất khó kiểm soát). Nhóm có thể phát triển một phiên bản tinh chỉnh của mô hình tích hợp, tập trung hoàn toàn vào việc khơi gợi và đặc tả các yêu cầu an toàn chống độc hại cho các ứng dụng tích hợp LLM. |
| 3 | **Cơ chế theo dõi vết yêu cầu động (Dynamic Traceability Links) trong MLOps** | Khi mô hình bị suy giảm hiệu năng trong quá trình vận hành (Model Drift) và kích hoạt cơ chế tự động huấn luyện lại (Retraining pipeline), làm thế nào để liên kết sự thay đổi của mô hình này quay trở lại với tài liệu yêu cầu ban đầu? Nhóm có thể đề xuất một kiến trúc hệ thống quản lý siêu dữ liệu (Metadata Management) giúp tự động cập nhật trạng thái đáp ứng yêu cầu hệ thống theo thời gian thực. |

---

## Relevance to Our Topic – Liên quan đến đề tài nhóm

Bài báo này là một tài liệu có giá trị **cực kỳ cao và mang tính toàn diện nhất (State-of-the-art)** cho các đề tài về Kỹ nghệ Phần mềm cho AI (Software Engineering for AI):

* **Kho tư liệu khổng lồ cho chương Tổng quan (Related Work):** Thay vì nhóm phải tự tìm và đọc hàng chục bài báo nhỏ lẻ về thách thức RE cho AI, bài báo này đã hệ thống hóa sẵn tất cả các nghiên cứu lớn trên thế giới thành các bảng phân loại cực kỳ khoa học. Nhóm có thể trích dẫn trực tiếp các số liệu và phân loại này vào báo cáo.
* **Khung quy trình mẫu để áp dụng:** Cung cấp một lộ trình 4 bước hoàn chỉnh giúp nhóm của bạn biết cách triển khai thiết lập tài liệu đặc tả yêu cầu cho dự án phần mềm tích hợp AI của mình một cách chuyên nghiệp và đúng chuẩn IEEE Access.
