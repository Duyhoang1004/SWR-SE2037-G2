# Paper 02 Summary

## Citation

**Tên bài:** AI for Requirements Engineering: Industry Adoption and Practitioner Perspectives  
**Tác giả:** Lekshmi Murali Rani, Richard Berntsson Svensson, Robert Feldt  
**Năm:** 2025  
**Nguồn:** arXiv Preprint, lĩnh vực Software Engineering (cs.SE)  
**Link:** https://arxiv.org/abs/2511.01324

## Problem

Phần lớn nghiên cứu trước về AI trong Requirements Engineering tập trung vào khả năng kỹ thuật của AI, chẳng hạn:

- Sinh requirements bằng LLM.
- Phân loại requirements.
- Phát hiện ambiguity và inconsistency.
- Tạo UML diagram.
- Kiểm tra requirement với specification.
- Tự động hóa một số tác vụ RE.

Tuy nhiên, còn thiếu bằng chứng về cách các chuyên gia phần mềm thực sự sử dụng AI trong công việc hằng ngày.

Bài báo tập trung trả lời ba nhóm câu hỏi:

1. AI hiện được sử dụng đến mức nào trong Requirements Engineering?
2. Cách tích hợp AI có khác nhau giữa elicitation, analysis, specification và validation hay không?
3. Practitioner nhìn nhận thế nào về lợi ích, rủi ro, thách thức và cơ hội của AI trong RE?

Nghiên cứu còn xem xét quyền quyết định giữa con người và AI theo bốn cách tiếp cận:

- Con người tự đưa ra quyết định.
- AI kiểm tra hoặc xác nhận quyết định của con người.
- AI và con người cộng tác.
- AI tự động thực hiện quy trình.

## Research Gap

Các nghiên cứu trước chủ yếu đánh giá thuật toán, mô hình hoặc proof-of-concept. Chúng chưa giải thích đầy đủ cách AI được áp dụng trong môi trường công nghiệp.

Khoảng trống nghiên cứu chính gồm:

- Thiếu dữ liệu thực tế về mức độ practitioner đang sử dụng AI trong RE.
- Chưa rõ việc sử dụng AI khác nhau như thế nào giữa elicitation, analysis, specification và validation.
- Chưa có hiểu biết đầy đủ về cách phân chia quyền quyết định giữa con người và AI.
- Chưa rõ practitioner coi AI là công cụ kiểm tra, cộng tác hay thay thế con người.
- Thiếu bằng chứng về các rào cản liên quan đến domain knowledge, trust, privacy, security, compliance và workflow integration.
- Chưa có cái nhìn hệ thống về Responsible AI practices khi dùng AI cho RE.
- Chưa có framework cụ thể cho Human–AI Collaboration trong Requirements Engineering.

Bài báo lấp một phần khoảng trống này bằng khảo sát 55 software practitioners để mô tả mức độ áp dụng, nhận thức, thách thức và cơ hội của AI trong bốn giai đoạn RE.

## Method

Nghiên cứu sử dụng phương pháp **survey mô tả – khám phá**, kết hợp phân tích định lượng và định tính.

### Thiết kế khảo sát

Khảo sát trực tuyến gồm 39 câu hỏi:

- Multiple-choice questions.
- Likert-scale questions.
- Open-ended questions.

Nội dung khảo sát gồm:

- Thông tin nhân khẩu học và nghề nghiệp.
- Mức độ sử dụng AI trong RE.
- Nhận thức và thái độ đối với AI.
- AI trong elicitation, analysis, specification và validation.
- Rủi ro và rào cản áp dụng.
- Responsible AI practices.
- Cơ hội sử dụng AI trong RE.

Bảng hỏi được pilot test với hai người trước khi triển khai chính thức.

### Thu thập dữ liệu

Khảo sát được thực hiện bằng nền tảng SoSci Survey trong 84 ngày của năm 2025.

Người tham gia được tuyển thông qua:

- Professional Slack groups.
- LinkedIn groups.
- Mối liên hệ cá nhân trong ngành phần mềm.

Nghiên cứu sử dụng convenience sampling và bao gồm cả người đang dùng AI lẫn người chưa dùng AI.

### Phân tích định lượng

Tác giả sử dụng:

- Descriptive statistics.
- Frequency và percentage.
- So sánh giữa AI users và non-AI users.
- So sánh giữa bốn giai đoạn RE.
- Phân tích Responsible AI practices.

Dữ liệu thiếu được loại khỏi phần phân tích liên quan.

### Phân tích định tính

Các câu trả lời mở được phân tích bằng **inductive thematic analysis** theo phương pháp Braun và Clarke.

Các theme được tạo trực tiếp từ dữ liệu thay vì áp dụng một framework có sẵn. Tác giả cũng công bố questionnaire, code phân tích và thematic codebook trong supplementary material.

## Dataset

Dataset gồm câu trả lời khảo sát của **55 software practitioners**.

Trong đó:

- 32 người đang sử dụng AI trong Requirements Engineering.
- 23 người chưa sử dụng AI trong Requirements Engineering.

Vai trò nghề nghiệp chính:

- Software Developer: 17 người, 30,9%.
- Project Lead hoặc Project Manager: 12 người, 21,8%.
- Business Analyst: 3 người.
- Product Manager: 3 người.
- Data Engineer: 3 người.
- Software Architect: 2 người.
- Support Engineer: 2 người.
- Engineering Manager: 2 người.
- Requirements Engineer: 1 người.
- AI Engineer: 1 người.

Kinh nghiệm trung bình là 9,6 năm, trung vị 8 năm, dao động từ 1 đến 35 năm.

Quy mô nhóm trung bình là 19,9 người, trung vị 10 người, dao động từ 2 đến 150 người.

Các ngành được khảo sát gồm:

- Automotive.
- Finance.
- Retail.
- Education.
- Healthcare.
- Manufacturing.
- Technology.
- E-commerce.
- Security.
- Public sector.

Phương pháp phát triển:

- Agile: 81,8%.
- Hybrid: 12,7%.
- Plan-driven: 5,5%.

## Evaluation

Bài báo không đánh giá một mô hình Machine Learning nên không sử dụng accuracy, precision, recall hoặc F1-score làm metric chính.

Các chỉ số đánh giá của nghiên cứu gồm:

- Tỷ lệ người đang sử dụng AI.
- Tần suất sử dụng AI.
- Tỷ lệ thái độ tích cực, trung lập hoặc tiêu cực.
- Tỷ lệ từng mô hình phân chia quyền quyết định.
- Tỷ lệ Human–AI Collaboration trong từng giai đoạn RE.
- Tỷ lệ áp dụng Responsible AI practices.
- Số người đề cập đến từng theme trong câu trả lời mở.

Kết quả chủ yếu được trình bày bằng frequency và percentage. Bài báo không báo cáo kiểm định thống kê suy luận hoặc mô hình nhân quả.

## Results

### Mức độ áp dụng AI

Có **58,2%**, tương ứng 32/55 người tham gia, đang sử dụng AI trong hoạt động Requirements Engineering.

Có **69,1%** người tham gia đánh giá tác động của AI là tích cực hoặc rất tích cực:

- Positive: 45,5%.
- Very positive: 23,6%.
- Neutral: 29,1%.
- Negative: 1,8%.

Người đã sử dụng AI có mức độ tin tưởng tích cực cao hơn người chưa sử dụng.

### Human–AI Collaboration là cách tiếp cận phổ biến nhất

Human–AI Collaboration chiếm trung bình khoảng **54,4%** các kỹ thuật RE được khảo sát.

Tỷ lệ AI cộng tác với con người theo từng giai đoạn:

- Elicitation: 49,2%.
- Analysis: 60,5%.
- Specification: 54,1%.
- Validation: 53,6%.

Analysis có mức cộng tác cao nhất vì AI có khả năng xử lý văn bản, phát hiện pattern, tìm inconsistency và tổng hợp lượng lớn thông tin.

Elicitation vẫn có tỷ lệ quyết định bởi con người cao hơn vì quá trình này đòi hỏi xây dựng niềm tin, hiểu cảm xúc, nhận biết yêu cầu ẩn và xử lý quan hệ stakeholder.

### Full Automation chưa được chấp nhận rộng rãi

Tỷ lệ AI tự thực hiện toàn bộ quy trình chỉ dao động từ 3,8% đến 7,6%:

- Elicitation: 5,4%.
- Analysis: 3,8%.
- Specification: 7,6%.
- Validation: 5,3%.

Chỉ 2% người tham gia cho rằng AI có thể độc lập thực hiện elicitation. Không có người tham gia nào cho rằng AI có thể độc lập thực hiện analysis, specification hoặc validation.

Kết quả cho thấy practitioner coi AI là công cụ hỗ trợ hơn là sự thay thế hoàn toàn cho con người.

### Responsible AI Practices

Trong 32 người sử dụng AI:

- 81,2% có con người xem xét và phê duyệt đề xuất của AI.
- 71,9% cho phép con người sửa hoặc ghi đè kết quả AI.
- 68,8% kiểm tra độ chính xác và độ tin cậy.
- 59,4% đào tạo thành viên sử dụng AI có trách nhiệm.
- 59,4% chú ý đến privacy và GDPR.
- 56,2% chú ý đến explainability và transparency.

Các hoạt động governance có hệ thống còn thấp:

- 37,5% thực hiện đánh giá rủi ro AI.
- 37,5% lưu hồ sơ requirements do AI tạo.
- 37,5% thông báo cho người dùng rằng AI đang hỗ trợ.
- 34,4% bảo vệ công cụ AI và dữ liệu khỏi rủi ro bảo mật.

Điều này cho thấy nhiều tổ chức đang áp dụng **reactive oversight**: con người kiểm tra output ngay lập tức nhưng chưa có governance, audit và risk management dài hạn.

### Các thách thức chính

**Thiếu kiến thức domain và context — 15/55 người:**  
AI khó hiểu kiến thức ngành, yêu cầu ngầm, lịch sử tổ chức và nhu cầu chưa được stakeholder diễn đạt rõ.

**Rào cản kỹ thuật và triển khai — 10/55 người:**  
Khó tích hợp AI vào workflow, token limit, scalability, chi phí, bias và thiếu kỹ năng sử dụng AI.

**Chất lượng và độ chính xác — 8/55 người:**  
AI có thể sinh requirements không chính xác, không đầy đủ, quá chung chung hoặc không phù hợp mục tiêu kinh doanh.

**Governance, security và compliance — 7/55 người:**  
Có nguy cơ rò rỉ requirement, vi phạm privacy và khó giải thích quyết định của AI.

**Giao tiếp và tương tác con người — 6/55 người:**  
AI không thể hoàn toàn thay thế việc xây dựng quan hệ, nhận biết tín hiệu phi ngôn ngữ, xử lý mâu thuẫn và vấn đề nhạy cảm giữa stakeholder.

**Dữ liệu và phương pháp — 4/55 người:**  
Thiếu dữ liệu domain-specific khiến AI bỏ sót yêu cầu đặc thù hoặc tạo kết quả quá chung chung.

### Các cơ hội chính

AI có thể:

- Sinh bản nháp requirements.
- Tóm tắt nội dung phỏng vấn stakeholder.
- Phát hiện requirement thiếu hoặc mâu thuẫn.
- Xác định ambiguity.
- Phân tích dữ liệu dự án trước đó.
- Phân tích user feedback và A/B testing data.
- Sinh use case, persona, journey map và câu hỏi phỏng vấn.
- Hỗ trợ chuẩn bị cuộc họp với khách hàng.
- Xử lý lượng lớn tài liệu nhanh hơn con người.
- Bổ sung kiến thức cho kỹ sư chưa có nhiều kinh nghiệm domain.

Các cơ hội này hiệu quả nhất khi vẫn có human oversight.

## Limitations

- Mẫu khảo sát chỉ gồm 55 người.
- Convenience sampling có thể không đại diện cho toàn bộ cộng đồng RE.
- Người quan tâm hoặc có quan điểm mạnh về AI có thể tham gia nhiều hơn, gây self-selection bias.
- Dữ liệu do người tham gia tự báo cáo nên có thể xuất hiện response bias.
- Nghiên cứu không phân biệt cụ thể ChatGPT, Copilot, Claude hoặc các công cụ AI khác.
- Các công cụ có năng lực khác nhau nhưng được phân tích chung.
- Nghiên cứu mang tính cross-sectional, chỉ phản ánh một thời điểm.
- Không theo dõi thay đổi hành vi sử dụng AI theo thời gian.
- AI phát triển nhanh nên một số kết quả có thể sớm lỗi thời.
- Các tổ chức có thể định nghĩa các giai đoạn RE khác nhau.
- Chủ yếu sử dụng thống kê mô tả, không chứng minh quan hệ nhân quả.
- Chưa đo trực tiếp AI có cải thiện chất lượng requirements, thời gian làm việc hoặc tỷ lệ lỗi dự án hay không.

## Relevance to our topic

Bài báo cung cấp bằng chứng thực tế cho việc sử dụng AI trong Requirements Engineering của hệ thống AI/ML.

Đối với hệ thống phân loại sản phẩm thương mại điện tử, cách tiếp cận phù hợp là **Human–AI Collaboration**:

- AI đề xuất danh mục sản phẩm.
- AI phát hiện hình ảnh hoặc thông tin không rõ ràng.
- AI gợi ý requirement còn thiếu.
- AI tạo bản nháp use case và acceptance criteria.
- Người quản trị kiểm tra và quyết định danh mục cuối cùng.
- Người dùng có thể sửa dự đoán sai.
- Các chỉnh sửa được lưu lại để cải thiện dữ liệu và mô hình.

Bài báo cũng giúp nhóm xác định yêu cầu quản trị AI:

- Mọi kết quả quan trọng phải được con người xác nhận.
- Cần lưu lịch sử output và chỉnh sửa.
- Phải thông báo rõ khi kết quả được AI tạo ra.
- Cần bảo vệ dữ liệu và requirement nội bộ.
- Cần kiểm tra bias và độ chính xác theo từng danh mục.
- Cần có cơ chế override.
- Phải phân chia rõ trách nhiệm giữa AI và người dùng.

Đây là bằng chứng hỗ trợ mạnh cho việc lựa chọn Human-in-the-Loop thay vì full automation.

## Possible Improvement

Nghiên cứu có thể được mở rộng bằng khảo sát lớn hơn và lấy mẫu phân tầng theo:

- Quốc gia.
- Vai trò nghề nghiệp.
- Quy mô tổ chức.
- Lĩnh vực kinh doanh.
- Kinh nghiệm.
- Loại công cụ AI.

Một nghiên cứu dọc có thể theo dõi cùng một nhóm practitioner trong 6–12 tháng để quan sát sự thay đổi của Human–AI Collaboration.

Ngoài survey, có thể thực hiện controlled experiment với ba nhóm:

1. Chỉ sử dụng RE truyền thống.
2. Sử dụng AI nhưng không có governance framework.
3. Sử dụng AI với Human–AI Collaboration và governance framework.

Sau đó so sánh:

- Thời gian hoàn thành requirements.
- Số requirement được phát hiện.
- Số requirement thiếu.
- Ambiguity rate.
- Consistency.
- Correctness.
- Traceability.
- Mức độ hài lòng của stakeholder.
- Số lỗi được phát hiện trong validation.

Nhóm cũng có thể xây dựng prototype AI-assisted RE tool hỗ trợ sinh requirements, kiểm tra ambiguity, đề xuất data requirements và tạo acceptance criteria.

