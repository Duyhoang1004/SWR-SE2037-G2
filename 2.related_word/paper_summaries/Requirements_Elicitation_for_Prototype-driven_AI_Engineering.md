# Paper Summary – Requirements Elicitation for Prototype-driven AI Engineering: a Case Study in Police Report Generation

---

## Citation

| Trường | Thông tin |
|---|---|
| **Tên bài báo** | Requirements Elicitation for Prototype-driven AI Engineering: a Case Study in Police Report Generation |
| **Tác giả** | Martijn van Vliet, Wouter Westerkamp, Sjaak Brinkkemper, Sergio España |
| **Năm công bố** | 2025 (April 7) |
| **Loại tài liệu** | Workshop Paper – REFSQ 2025 |
| **Link tài liệu** | https://ceur-ws.org/Vol-3959/PT-paper4.pdf |
| **Cơ quan công tác**| Khoa Khoa học Thông tin và Máy tính, Đại học Utrecht, Hà Lan |

---

## 1. Research Objective – Mục tiêu nghiên cứu

Nghiên cứu này xuất phát từ bối cảnh các hệ thống tích hợp trí tuệ nhân tạo (AI-based systems) đang tạo ra làn sóng chuyển đổi lớn trong khu vực công, điển hình là lĩnh vực thực thi pháp luật nhạy cảm. Tuy nhiên, việc thiếu các quy trình kỹ nghệ phần mềm chuyên biệt đang làm tăng tỷ lệ thất bại của các dự án này.

Mục tiêu cụ thể của nhóm tác giả tập trung vào hai khía cạnh cốt lõi:

* **Tầng lý thuyết và phương pháp:** Giải quyết câu hỏi nghiên cứu chính (MRQ1) về cách khơi gợi các yêu cầu hệ thống cho một giải pháp dựa trên AI nhằm thúc đẩy các nỗ lực phát triển có trách nhiệm, an toàn và tuân thủ pháp lý. Nghiên cứu hướng tới việc xây dựng một phương pháp luận có cấu trúc vững chắc để tích hợp các góc nhìn đa ngành (đạo đức, pháp lý, kỹ thuật) vào chu kỳ phát triển.
* **Tầng thực nghiệm ứng dụng:** Triển khai thử nghiệm phương pháp đề xuất vào một dự án thực tế mang tên Police2Report tại Cảnh sát Hà Lan. Mục tiêu là giúp dự án này thoát khỏi trạng thái làm nguyên mẫu thử nghiệm để định hình các yêu cầu hoàn chỉnh, làm tiền đề thiết kế một sản phẩm có trách nhiệm và có thể mở rộng quy mô trong tương lai.

---

## 2. Main Problem – Vấn đề nghiên cứu

Bài báo chỉ ra chuỗi thách thức và lỗ hổng nghiêm trọng trong việc áp dụng các quy trình phát triển phần mềm truyền thống vào các hệ thống AI:

| # | Vấn đề | Mô tả chi tiết |
|---|---|---|
| 1 | **Sự bất lực của RE truyền thống** | Các kỹ thuật Kỹ nghệ yêu cầu (RE) truyền thống hoàn toàn không hiệu quả trong việc hướng dẫn phát triển hệ thống AI. Chúng bỏ qua bản chất bất định (non-deterministic) của AI—nơi hệ thống có các thành phần đơn giản nhưng hành vi tổng thể lại vô cùng phức tạp và khó dự đoán trước. |
| 2 | **Hội chứng "Tê liệt dự án thử nghiệm"** | Thuật ngữ *Pilot Paralysis* mô tả việc một số lượng lớn các dự án AI bị mắc kẹt vĩnh viễn ở giai đoạn làm nguyên mẫu (prototype) để trình diễn. Các tổ chức không thể thương mại hóa hoặc mở rộng quy mô (scale-up) các giải pháp này do vấp phải các rào cản vô hình về mặt vận hành, đạo đức và pháp lý chưa được tính toán từ đầu. |
| 3 | **Bỏ sót các yêu cầu có trách nhiệm** | Quy trình RE thông thường có xu hướng bỏ qua hoặc chỉ xem xét các nguyên tắc đạo đức và an toàn AI một cách hời hợt ở mức độ lý thuyết vĩ mô chung chung. Điều này tạo điều kiện cho các nhà thực hành "nhắm mắt làm ngơ", dẫn đến việc xây dựng các hệ thống thiếu tính minh bạch, kém tin cậy hoặc vi phạm quyền riêng tư. |
| 4 | **Rủi ro cao trong môi trường nhạy cảm** | Trong bối cảnh cụ thể của Cảnh sát Hà Lan, việc ứng dụng Generative AI để tự động dịch thuật và tóm tắt băng ghi âm thẩm vấn thành báo cáo hành chính chứa đựng các rủi ro rất lớn về mặt pháp lý, sai lệch ngữ cảnh nghiêm trọng và ảnh hưởng trực tiếp đến chuỗi tố tụng tư pháp. |

---

## 3. Proposed Method – Phương pháp đề xuất

Tác giả đề xuất phương pháp **PRE4AIM** (Requirements Elicitation Method for Prototype-driven AI Engineering). Phương pháp này được thiết kế như một cấu phần có thể tái sử dụng trong bất kỳ chu kỳ phát triển phần mềm (SDLC) nào dựa trên khung kiến thức SWEBOK, đặc tả bằng sơ đồ Quy trình - Sản phẩm (Process Deliverable Diagram - PDD) nhằm liên kết hoạt động với kết quả đầu ra.

### 3.1. Cấu trình quy trình tổng thể của PRE4AIM

Quy trình được chia làm hai phần chính với cơ chế lặp Agile chuyển tiếp liên tục:

* **Phần Chuẩn bị (Preparation):** Tập trung vào việc định danh dự án AI, xác định các khía cạnh đa ngành liên quan (User, Organization, Ethics, Legal, Technical...), lựa chọn các nhân sự đại diện phù hợp cho các bên liên quan (stakholders) và xây dựng đề cương phỏng vấn bán cấu trúc đồng nhất.
* **Phần Khơi gợi (Elicitation):** Tiến hành phỏng vấn bán cấu trúc kết hợp với việc trình diễn trực tiếp (live demonstration) phiên bản nguyên mẫu hiện tại để thu thập phản hồi và điều chỉnh kỳ vọng. Quá trình phỏng vấn được thực hiện lũy tiến qua 3 giai đoạn phân rã.

### 3.2. Ba giai đoạn khơi gợi trong PRE4AIM

| Giai đoạn | Đối tượng phỏng vấn | Mục tiêu và Đầu ra hành động |
|---|---|---|
| **Phase 1: Khám phá giá trị** *(Value Exploration)* | Người dùng cuối (Điều tra viên), Quản lý triển khai hệ thống của tổ chức | Xác định các nhu cầu cốt lõi, mong muốn giảm tải gánh nặng hành chính và các yêu cầu hệ thống ban đầu (Functional & Non-functional). |
| **Phase 2: Xác định rào cản & Cơ hội** *(Obstacle & Opportunity Identification)* | Chuyên gia Pháp lý, Cố vấn Đạo đức, Đại diện bên thứ ba, Chuyên gia Môi trường | Đánh giá tập yêu cầu của Phase 1 dưới góc độ tuân thủ. Nhận diện các rào cản (bảo mật, định kiến, bản quyền) và cơ hội phát triển tính năng mới (định danh người nói, sửa lỗi). |
| **Phase 3: Khám phá giải pháp** *(Solution Discovery)* | Nhà khoa học dữ liệu, Kiến trúc sư giải pháp, Chuyên gia An toàn AI, Chuyên gia AI có trách nhiệm | Thảo luận về tính khả thi kỹ thuật nhằm tìm kiếm giải pháp công nghệ cụ thể cho các rào cản đã phát hiện ở Phase 2, làm đầu vào trực tiếp cho vòng lặp thiết kế tiếp theo. |

---

## 4. Dataset Used – Bộ dữ liệu sử dụng

Vì nghiên cứu này áp dụng phương pháp luận Nghiên cứu Hành động Kỹ thuật (Technical Action Research) định tính, cấu trúc dữ liệu không tồn tại dưới dạng các tập dữ liệu số hay benchmark thuật toán.

Đối tượng nghiên cứu thực nghiệm và nguồn dữ liệu đầu vào bao gồm:
* Mô hình nguyên mẫu **Police2Report** (phiên bản 1) sử dụng công nghệ AI tạo sinh thuộc quyền sở hữu của Cảnh sát Hà Lan.
* Dữ liệu định tính trích xuất từ **9 cuộc phỏng vấn bán cấu trúc** được ghi âm và phân tích độc lập bởi hai nhà nghiên cứu. Các chuyên gia cung cấp thông tin thuộc 9 vai trò đa ngành: *điều tra viên, quản lý triển khai, kiến trúc sư miền, nhà đồng sáng lập từ bên thứ ba, kiến trúc sư giải pháp, cố vấn đạo đức, cố vấn pháp lý, nhà khoa học dữ liệu và chuyên gia an toàn AI/AI có trách nhiệm.*

---

## 5. Baselines Compared – Các cơ sở so sánh

Nghiên cứu tuân thủ chặt chẽ phương pháp luận khoa học thiết kế (Design Science Methodology) nên không tiến hành so sánh định lượng trực tiếp các chỉ số toán học với các thuật toán hay công cụ cụ thể.

Thay vào đó, bài báo sử dụng các **thực hành Kỹ nghệ Phần mềm (SE) và Kỹ nghệ Yêu cầu (RE) truyền thống nói chung** làm nền tảng đối chiếu lý thuyết. Tác giả đối chiếu cách tiếp cận đa ngành theo tầng của PRE4AIM với sự thiếu hụt quy trình, tính mơ hồ và sự hời hợt trong việc xử lý các thuộc tính chất lượng đặc thù AI của các phương pháp truyền thống.

---

## 6. Evaluation Metrics – Tiêu chí đánh giá

Hiệu quả và tính khả thi của phương pháp PRE4AIM được đo lường thông qua các tiêu chí đánh giá định tính trong môi trường thực tế bao gồm:

* **Khả năng khai thác yêu cầu:** Đo lường bằng số lượng và chất lượng các yêu cầu hệ thống thu thập được qua các giai đoạn.
* **Tính thực tiễn (Practicability):** Khả năng áp dụng thành công phương pháp luận này vào một môi trường thế giới thực có cấu trúc hành chính phức tạp như cơ quan cảnh sát.
* **Mức độ hữu ích (Usefulness):** Khả năng nâng cao hiểu biết về lĩnh vực (domain understanding), phát hiện sớm các rủi ro hệ thống và định hướng cho nguyên mẫu tiến tới một sản phẩm thực tế phù hợp.
* **Tính cộng tác lũy tiến:** Khả năng tạo điều kiện để các bên liên quan xây dựng luận điểm, kế thừa và phản biện ý kiến của nhau một cách có hệ thống thông qua việc sử dụng nguyên mẫu làm chất xúc tác.

---

## 7. Main Results – Kết quả chính

Kết quả thực nghiệm sau một vòng lặp áp dụng phương pháp PRE4AIM tại Cảnh sát Hà Lan đạt được các chỉ số và phát hiện quan trọng:

| Khía cạnh | Kết quả đạt được thực tế |
|---|---|
| **Số lượng yêu cầu khai thác** | Thu thập thành công **23 yêu cầu hệ thống ban đầu**, bao gồm: 9 yêu cầu chức năng, 4 yêu cầu hiệu năng, 8 yêu cầu về khía cạnh chất lượng đặc thù AI và 2 yêu cầu ràng buộc. |
| **Mức độ làm phong phú** | Có **18 trên tổng số 23 yêu cầu** được đưa vào các giai đoạn tiếp theo một cách mượt mà để làm sâu sắc thêm hiểu biết và xác định hướng giải pháp kỹ thuật. |
| **Nhận diện rào cản cốt lõi** | Phát hiện chính xác **2 rào cản lớn** đe dọa sự sống còn của dự án: (1) Tính pháp lý chưa rõ ràng của văn bản do AI tạo ra trong chuỗi tố tụng; (2) Sự tồn tại của dòng dữ liệu không cho phép chuyển giao cho bên thứ ba trong kiến trúc hiện tại. |
| **Đồng thuận giải pháp kỹ thuật** | (1) Định hình lại hệ thống AI về vai trò **"cố vấn/gợi ý"**, giữ con người luôn trong vòng lặp kiểm soát (*human-in-the-loop*);<br>(2) Thống nhất áp dụng **Đồ thị tri thức (Knowledge Graphs)** để hỗ trợ truy xuất nguồn gốc hiển thị và chạy các bài kiểm tra **benchmark** liên tục nhằm giám sát tính chính xác ngữ cảnh. |

---

## 8. Limitations – Hạn chế

| # | Hạn chế | Phân tích chi tiết |
|---|---|---|
| 1 | **Tính tổng quát hóa thấp** | Nghiên cứu mới chỉ dừng lại ở mô hình **một nghiên cứu điển hình duy nhất (single case study)** trong môi trường hành pháp đặc thù, rất khó để tự động khái quát hóa kết quả cho các lĩnh vực kinh tế - xã hội khác. |
| 2 | **Giới hạn về số vòng lặp** | Thực nghiệm mới chỉ kiểm chứng qua **một vòng lặp duy nhất** của phương pháp PRE4AIM. Chưa có dữ liệu thực tế để khẳng định mức độ hữu ích của thông tin thu về sẽ duy trì ổn định trong các vòng lặp tiếp theo. |
| 3 | **Phụ thuộc vào chất lượng chuyên gia** | Sự thành công vượt trội của tập yêu cầu thu được phụ thuộc hoàn toàn vào kiến thức chuyên sâu và kinh nghiệm phong phú của 9 chuyên gia tham gia phỏng vấn, một nguồn lực chất lượng cao không phải dự án nào cũng sở hữu. |

---

## 9. Future Work – Hướng phát triển tương lai

Nhóm tác giả vạch ra ba hướng đi chính để mở rộng nghiên cứu trong tương lai:

* **Mở rộng phạm vi thực nghiệm:** Áp dụng phương pháp PRE4AIM vào nhiều dự án AI thuộc các lĩnh vực khác nhau, đồng thời tiến hành thực hiện nhiều vòng lặp liên tục trong một khoảng thời gian dài hơn để tinh chỉnh quy trình.
* **Mở rộng kiến trúc phương pháp:** Bổ sung thêm các giai đoạn mới vào quy trình, tích hợp thêm các góc nhìn/khía cạnh chuyên môn chưa có hoặc chủ động thay đổi giao thức phỏng vấn bán cấu trúc để tăng tính linh hoạt.
* **Nghiên cứu tác động hạ nguồn:** Khám phá chuyên sâu tầm ảnh hưởng và cách thức chuyển hóa của các thông tin yêu cầu thu được từ PRE4AIM đối với các hoạt động tiếp theo trong chuỗi RE như phân tích (analysis), đặc tả chi tiết (specification) hoặc thẩm định yêu cầu (validation).

---

## 10. Possible Research Gaps – Khoảng trống nghiên cứu

| # | Research Gap | Gợi ý cải tiến / Hướng khai thác cho nhóm |
|---|---|---|
| 1 | **Thiếu công cụ tự động hóa RE cho AI** | Phương pháp PRE4AIM hiện tại hoàn toàn dựa trên phỏng vấn và phân tích thủ công của con người. Nhóm có thể nghiên cứu ứng dụng chính LLM để tự động phân tích băng ghi âm phỏng vấn chuyên gia, phân loại và trích xuất các yêu cầu theo khung PRE4AIM nhằm tăng tốc quy trình. |
| 2 | **Chưa có độ đo định lượng cho thuộc tính chất lượng AI** | Bài báo nêu ra các yêu cầu chất lượng (tính minh bạch, đạo đức, độ tin cậy) nhưng chỉ ở dạng văn bản định tính. Nhóm có thể phát triển một bộ chỉ số định lượng (metrics) hoặc framework kiểm thử cụ thể để đo lường xem một nguyên mẫu AI đã đáp ứng các yêu cầu đạo đức ở mức độ bao nhiêu phần trăm. |
| 3 | **Sự thiếu hụt công cụ quản lý độ lệch yêu cầu khi AI cập nhật** | Khi mô hình AI thay đổi (ví dụ: cập nhật trọng số, thay thế LLM nền), các rào cản về đạo đức và pháp lý có thể thay đổi theo. Bài báo chưa giải quyết việc quản lý sự thay đổi này. Nhóm có thể đề xuất giải pháp đồng bộ hóa (Traceability Link) giữa mã nguồn AI và tập yêu cầu đa ngành. |
| 4 | **Giới hạn ở góc nhìn chuyên gia nội bộ** | Quy trình mới chỉ lấy ý kiến từ các chuyên gia và cảnh sát, thiếu góc nhìn từ đối tượng chịu tác động gián tiếp (ví dụ: nghi phạm, luật sư bào chữa, người dân). Nhóm có thể mở rộng Phase 2 của phương pháp bằng cách tích hợp góc nhìn của các tổ chức nhân quyền công cộng để đảm bảo tính khách quan tối đa. |

---

## Relevance to Our Topic – Liên quan đến đề tài nhóm

Bài báo này sở hữu mức độ liên quan **đặc biệt cao** nếu đề tài của nhóm tập trung vào các hướng nghiên cứu sau:

* **Kỹ nghệ phần mềm cho AI (AI Engineering):** Cung cấp một quy trình (pipeline) RE hoàn chỉnh, có sơ đồ PDD rõ ràng để nhóm tham khảo làm quy trình chuẩn cho dự án.
* **Ứng dụng Generative AI / LLM vào thực tế:** Đóng vai trò là một case study mẫu mực về các rủi ro và giải pháp (như kết hợp Knowledge Graphs, Human-in-the-loop) khi đưa mô hình ngôn ngữ lớn vào vận hành trong môi trường nhạy cảm, độ chính xác cao.
* **Xây dựng giải pháp AI có trách nhiệm (Responsible AI):** Khai thác trực tiếp các khoảng trống nghiên cứu (Gap 1, Gap 2) để tạo ra các đóng góp khoa học mới cho bài tập lớn hoặc đề tài nghiên cứu của nhóm.
