# Paper 03 Summary

## Citation

**Tên bài:** Modeling Data Requirements for Machine Learning Systems  
**Tác giả:** Wenting Shao, Xi Wang  
**Năm:** 2022  
**Nguồn:** Proceedings of the 2022 IEEE 13th International Conference on Software Engineering and Service Science (ICSESS), trang 97–100  
**DOI:** 10.1109/ICSESS54813.2022.9930317  
**Link:** https://ieeexplore.ieee.org/document/9930317/


## Problem

Bài báo giải quyết vấn đề đặc tả **data requirements** cho các hệ thống Machine Learning.

Trong phần mềm truyền thống, Requirements Engineering thường tập trung vào:

- Chức năng hệ thống.
- Hành vi phần mềm.
- Giao diện.
- Hiệu năng.
- Yêu cầu chất lượng.

Tuy nhiên, trong hệ thống ML, chất lượng và khả năng hoạt động của mô hình phụ thuộc trực tiếp vào dữ liệu. Một mô hình tốt vẫn có thể thất bại nếu dữ liệu:

- Không đủ số lượng.
- Không đại diện cho môi trường thực tế.
- Bị mất cân bằng giữa các lớp.
- Có nhãn sai hoặc không nhất quán.
- Thiếu các trường hợp biên.
- Không đáp ứng yêu cầu về chất lượng.
- Không phản ánh đúng learning context.
- Không bao phủ đầy đủ các đối tượng và mối quan hệ trong miền nghiệp vụ.

Các phương pháp Requirements Engineering hiện tại chưa cung cấp cách biểu diễn có hệ thống mối liên hệ giữa:

- Bối cảnh học của hệ thống.
- Các thành phần xuất hiện trong môi trường.
- Quan hệ giữa các thành phần.
- Các đặc tính mà dataset và từng data sample phải đáp ứng.

Do đó, bài báo đề xuất một phương pháp mô hình hóa hai lớp để xác định data requirements ngay trong giai đoạn requirements analysis, thay vì chỉ xem xét dữ liệu khi bắt đầu huấn luyện mô hình.

## Research Gap

Khoảng trống nghiên cứu chính là các phương pháp Requirements Engineering cho ML vẫn còn ở giai đoạn sơ khai trong việc mô hình hóa data requirements.

Các nghiên cứu và phương pháp trước đó còn một số thiếu sót:

- Tập trung nhiều vào functional requirements và quality requirements nhưng chưa xem dữ liệu là một artifact yêu cầu độc lập.
- Chưa mô hình hóa đầy đủ learning context của hệ thống ML.
- Chưa thể hiện rõ các thành phần, môi trường và mối quan hệ ảnh hưởng đến dữ liệu.
- Nhiều cách đặc tả chỉ tập trung vào các thuộc tính riêng lẻ của dataset.
- Thiếu sự kết nối giữa cấu trúc miền nghiệp vụ và các điều kiện cụ thể mà dữ liệu phải đáp ứng.
- Chưa có phương pháp thống nhất để mô tả đồng thời yêu cầu định tính và định lượng của dữ liệu.
- Khó truy vết từ mục tiêu học của mô hình đến dataset cần thu thập.

Bài báo lấp một phần khoảng trống này bằng phương pháp **two-layer data requirements modeling**, kết hợp feature-oriented modeling với property-based specifications.

## Method

Bài báo đề xuất phương pháp mô hình hóa data requirements gồm hai lớp.

### Layer 1: Modeling the Learning Context

Lớp thứ nhất mô hình hóa **learning context** của hệ thống ML.

Learning context mô tả:

- Các đối tượng mà hệ thống cần nhận biết hoặc dự đoán.
- Môi trường mà dữ liệu được tạo ra.
- Những thành phần liên quan đến quá trình học.
- Quan hệ giữa đối tượng, điều kiện môi trường và dữ liệu.
- Các biến thể có thể xảy ra trong miền ứng dụng.
- Những trường hợp bắt buộc hoặc tùy chọn cần được dataset bao phủ.

Tác giả sử dụng **feature models** để biểu diễn learning context. Feature model phù hợp vì có thể mô tả:

- Feature bắt buộc.
- Feature tùy chọn.
- Các lựa chọn thay thế.
- Quan hệ phụ thuộc.
- Quan hệ loại trừ.
- Commonality và variability trong miền dữ liệu.

Ví dụ, đối với hệ thống phân loại ảnh sản phẩm, learning context có thể bao gồm:

- Loại sản phẩm.
- Danh mục sản phẩm.
- Màu sắc.
- Góc chụp.
- Nền ảnh.
- Điều kiện ánh sáng.
- Độ phân giải.
- Sản phẩm bị che khuất.
- Một ảnh chứa một hoặc nhiều sản phẩm.
- Thiết bị chụp ảnh.

Feature model giúp nhóm phát triển xác định những biến thể nào của thế giới thực cần xuất hiện trong dataset.

### Layer 2: Property-Based Specifications

Lớp thứ hai mô tả các thuộc tính cụ thể mà dữ liệu phải đáp ứng bằng **property-based specifications**.

Các property có thể được sử dụng để đặc tả:

- Số lượng dữ liệu.
- Số lượng mẫu theo từng lớp.
- Tỷ lệ phân phối giữa các lớp.
- Độ cân bằng của dataset.
- Chất lượng hình ảnh.
- Độ đầy đủ của dữ liệu.
- Độ chính xác và nhất quán của nhãn.
- Phạm vi giá trị.
- Tỷ lệ dữ liệu thiếu.
- Mức độ bao phủ learning context.
- Ràng buộc của từng data sample.
- Ràng buộc của toàn bộ dataset.

Đối với hệ thống phân loại sản phẩm, property-based specification có thể được viết theo dạng:

- Mỗi category phải có ít nhất một số lượng ảnh tối thiểu.
- Mỗi sản phẩm phải có ảnh ở nhiều góc chụp.
- Ảnh phải đạt độ phân giải tối thiểu.
- Tỷ lệ ảnh bị mờ không được vượt quá một ngưỡng nhất định.
- Chênh lệch số lượng mẫu giữa các category không được quá lớn.
- Một tỷ lệ nhất định của dữ liệu phải chứa các trường hợp khó.
- Nhãn phải được kiểm tra bởi ít nhất hai người hoặc qua quy trình xác minh.
- Dataset phải bao phủ các điều kiện ánh sáng và nền ảnh quan trọng.

### Mối liên hệ giữa hai lớp

Hai lớp không hoạt động độc lập.

- Layer 1 trả lời câu hỏi: **Dữ liệu phải phản ánh những đối tượng, điều kiện và biến thể nào?**
- Layer 2 trả lời câu hỏi: **Các dữ liệu đó phải đạt những thuộc tính và ngưỡng cụ thể nào?**

Feature model cung cấp cấu trúc và phạm vi miền dữ liệu. Property-based specification cung cấp các điều kiện chi tiết, có thể kiểm tra được.

Quy trình áp dụng có thể được hiểu như sau:

1. Xác định mục tiêu của ML system.
2. Xác định các đối tượng và yếu tố môi trường liên quan.
3. Xây dựng feature model cho learning context.
4. Xác định các biến thể cần được dataset bao phủ.
5. Định nghĩa property cho dataset và data sample.
6. Liên kết property với từng feature hoặc nhóm feature.
7. Dùng mô hình làm cơ sở cho việc thu thập, kiểm tra và quản lý dữ liệu.

## Dataset

Bài báo không sử dụng một dataset lớn để huấn luyện và so sánh mô hình Machine Learning.

Đây là nghiên cứu đề xuất phương pháp Requirements Engineering và mô hình hóa dữ liệu. Vì vậy, “dữ liệu” trong bài chủ yếu là:

- Các khái niệm về learning context.
- Các thành phần của miền ứng dụng.
- Feature models.
- Các property dùng để đặc tả dataset và data sample.
- Ví dụ minh họa cho phương pháp mô hình hóa.

Dataset trong bài không đóng vai trò là tập training, validation hoặc test của một mô hình ML. Thay vào đó, bài tập trung vào cách xác định yêu cầu cho dataset trước khi dataset được xây dựng.

## Evaluation

Bài báo không đánh giá một mô hình ML nên không sử dụng các metric như:

- Accuracy.
- Precision.
- Recall.
- F1-score.
- AU-ROC.

Việc đánh giá chủ yếu mang tính **conceptual và illustrative**, tức là trình bày phương pháp, cấu trúc hai lớp và ví dụ áp dụng để cho thấy phương pháp có thể mô hình hóa data requirements.

Các tiêu chí có thể rút ra để xem xét phương pháp gồm:

- Khả năng biểu diễn learning context.
- Khả năng mô hình hóa variability.
- Khả năng đặc tả thuộc tính của dataset.
- Khả năng đặc tả thuộc tính của từng data sample.
- Mức độ rõ ràng và có cấu trúc của data requirements.
- Khả năng liên kết giữa bối cảnh miền và thuộc tính dữ liệu.
- Khả năng dùng yêu cầu để hướng dẫn thu thập và kiểm tra dữ liệu.

Tuy nhiên, bài báo chưa cung cấp đánh giá thực nghiệm quy mô lớn, user study hoặc so sánh định lượng với các phương pháp khác.

## Results

Kết quả chính của bài báo là phương pháp **two-layer data requirements modeling** dành cho ML systems.

### Kết quả 1: Learning context được mô hình hóa có cấu trúc

Feature model giúp biểu diễn:

- Các thành phần của miền.
- Điều kiện môi trường.
- Commonality và variability.
- Quan hệ giữa các yếu tố ảnh hưởng đến dữ liệu.
- Các trường hợp cần được dataset bao phủ.

Nhờ đó, nhóm phát triển không chỉ thu thập dữ liệu dựa trên số lượng mà còn dựa trên phạm vi và bối cảnh thực tế mà mô hình sẽ hoạt động.

### Kết quả 2: Data requirements trở nên cụ thể hơn

Property-based specifications giúp chuyển các yêu cầu mơ hồ như:

> Dataset phải đủ lớn và có chất lượng tốt.

thành các điều kiện cụ thể hơn như:

- Số lượng mẫu tối thiểu.
- Tỷ lệ mẫu của từng lớp.
- Ngưỡng chất lượng.
- Mức độ bao phủ.
- Tỷ lệ lỗi hoặc thiếu dữ liệu cho phép.
- Điều kiện của từng data sample.

### Kết quả 3: Kết nối domain context với dataset

Điểm quan trọng của phương pháp là không chỉ đặc tả thuộc tính kỹ thuật của dữ liệu mà còn liên kết chúng với learning context.

Điều này giúp trả lời:

- Vì sao cần loại dữ liệu này?
- Feature hoặc điều kiện nào yêu cầu dữ liệu đó?
- Dataset đã bao phủ đầy đủ môi trường vận hành chưa?
- Loại mẫu nào còn thiếu?
- Property nào cần được kiểm tra trong quá trình xây dựng dataset?

### Kết quả 4: Hỗ trợ RE trong giai đoạn đầu

Phương pháp giúp đưa data requirements vào giai đoạn requirements analysis. Điều này có thể giảm nguy cơ đến giai đoạn training mới phát hiện:

- Thiếu dữ liệu.
- Dữ liệu mất cân bằng.
- Không có trường hợp biên.
- Không phản ánh môi trường thật.
- Nhãn không đủ chi tiết.
- Dataset không đáp ứng mục tiêu của mô hình.

## Limitations

Bài báo có một số hạn chế:

- Bài báo ngắn và chủ yếu trình bày ý tưởng phương pháp.
- Chưa có đánh giá thực nghiệm trên dự án công nghiệp quy mô lớn.
- Chưa có user study với requirements engineers, data scientists hoặc ML engineers.
- Chưa so sánh định lượng với các phương pháp data requirements khác.
- Chưa đánh giá chi phí và thời gian áp dụng phương pháp.
- Chưa chứng minh rằng dataset xây dựng từ phương pháp sẽ cải thiện trực tiếp chất lượng mô hình.
- Property-based specifications có thể cần được điều chỉnh cho từng miền.
- Feature model có thể trở nên phức tạp khi learning context có nhiều yếu tố.
- Chưa trình bày đầy đủ cơ chế giải quyết xung đột giữa các data requirements.
- Chưa mô tả rõ cách cập nhật requirements khi môi trường hoặc phân phối dữ liệu thay đổi.
- Chưa có tích hợp hoàn chỉnh với data pipeline, MLOps hoặc công cụ quản lý requirements.
- Việc xác định ngưỡng cụ thể vẫn phụ thuộc nhiều vào chuyên gia miền và nhóm ML.

## Relevance to Our Topic

Bài báo cực kỳ liên quan đến đề tài của nhóm:

> **Requirements Engineering for an AI-assisted E-commerce Product Categorization System from Images using Convolutional Neural Networks.**

Dataset ảnh sản phẩm là thành phần cốt lõi quyết định chất lượng của mô hình phân loại. Phương pháp hai lớp có thể được áp dụng trực tiếp.

### Áp dụng Layer 1: Learning Context Feature Model

Nhóm có thể xây dựng feature model gồm:

**Product-related features**

- Category.
- Subcategory.
- Brand.
- Color.
- Shape.
- Material.
- Packaging.
- Product variant.

**Image-related features**

- Front view.
- Side view.
- Top view.
- Close-up.
- Multiple products.
- Occlusion.
- Blurred image.
- Different backgrounds.
- Different lighting conditions.
- Different resolutions.

**Environment-related features**

- Ảnh từ người bán.
- Ảnh từ điện thoại.
- Ảnh studio.
- Ảnh đã qua chỉnh sửa.
- Ảnh có watermark.
- Ảnh có chữ.
- Ảnh lấy từ nhiều nền tảng thương mại điện tử.

Feature model giúp nhóm xác định dataset cần bao phủ những trường hợp nào, thay vì chỉ thu thập một số lượng lớn ảnh tương tự nhau.

### Áp dụng Layer 2: Property-Based Specifications

Nhóm có thể định nghĩa các yêu cầu như:

- Mỗi category có ít nhất 1.000 ảnh.
- Mỗi subcategory có ít nhất 200 ảnh.
- Không category nào chiếm quá 20% tổng dataset.
- Tỷ lệ ảnh mờ không vượt quá 5%.
- Ít nhất 20% ảnh của mỗi category có nền phức tạp.
- Ít nhất 10% ảnh chứa trường hợp che khuất một phần.
- Mỗi sản phẩm có tối thiểu hai góc chụp nếu dữ liệu cho phép.
- Độ phân giải tối thiểu là 224 × 224 pixel.
- Tỷ lệ nhãn sai sau kiểm tra không vượt quá một ngưỡng xác định.
- Mỗi ảnh phải có category label và nguồn dữ liệu.
- Dataset phải được chia train, validation và test theo cách tránh data leakage.
- Ảnh của cùng một sản phẩm không nên xuất hiện đồng thời trong train và test.

Các con số trên chỉ là ví dụ. Nhóm phải xác định giá trị thực tế dựa trên dataset và nguồn lực của dự án.

Bài báo giúp nhóm xây dựng phần:

- Data requirements.
- Dataset acceptance criteria.
- Data quality requirements.
- Data coverage requirements.
- Labeling requirements.
- Traceability giữa mục tiêu hệ thống và dữ liệu.
- Validation rules cho dataset.

## Possible Improvement

Phương pháp có thể được cải tiến theo các hướng sau:

### 1. Xây dựng công cụ hỗ trợ

Phát triển tool cho phép:

- Vẽ learning context feature model.
- Khai báo property-based specifications.
- Kiểm tra tính hợp lệ của yêu cầu.
- Phát hiện requirement xung đột.
- Sinh checklist thu thập dữ liệu.
- Sinh data validation rules tự động.

### 2. Chuyển property thành kiểm tra tự động

Các property có thể được chuyển thành code để kiểm tra dataset:

- Số lượng ảnh theo category.
- Class distribution.
- Độ phân giải.
- Tỷ lệ ảnh lỗi.
- Missing labels.
- Duplicate images.
- Data leakage.
- Label inconsistency.
- Coverage của các điều kiện môi trường.

### 3. Tích hợp với MLOps

Mô hình data requirements có thể được tích hợp vào:

- Data ingestion pipeline.
- Data validation.
- Model training.
- Model monitoring.
- Data drift detection.
- Model retraining.

### 4. Bổ sung traceability

Xây dựng ma trận:

> Business goal → ML goal → Learning context → Data requirement → Dataset check → Model metric

Ví dụ:

> Phân loại chính xác giày và dép → cần nhận biết sự khác nhau về hình dạng → dataset phải có nhiều góc chụp → kiểm tra coverage góc chụp → đánh giá recall của từng category.

### 5. Đánh giá thực nghiệm

Áp dụng phương pháp trên dataset e-commerce và so sánh:

- Dataset xây dựng theo cách thông thường.
- Dataset xây dựng theo two-layer data requirements modeling.

Sau đó đánh giá:

- Completeness của data requirements.
- Coverage của learning context.
- Class balance.
- Label quality.
- Accuracy, precision, recall và F1-score của mô hình.
- Robustness trên ảnh thực tế.
- Số lỗi dữ liệu phát hiện trước training.
- Thời gian và chi phí xây dựng dataset.
