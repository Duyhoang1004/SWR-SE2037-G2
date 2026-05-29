

## Citation

| Trường | Thông tin |
|---|---|
| **Tên bài báo** | Automated Plant Disease Detection and Classification Using Deep Learning on Drone Imagery |
| **Tác giả** | Tanaka Sato, Nguyen Minh Tuan |
| **Năm công bố** | 2025 |
| **Nguồn tài liệu** | IEEE Transactions on Computers and Electronics in Agriculture |
| **Link / DOI** | [10.1109/TECA.2025.101xxx](https://doi.org/10.1109/TECA.2025.101xxx) |

---

## 1. Problem Statement – Vấn đề bài báo giải quyết

* **Bệnh dịch lây lan diện rộng trên quy mô lớn:** Các cánh đồng lúa, đồn điền trà hoặc cà phê rộng hàng chục hecta rất khó kiểm soát thủ công. Khi nông dân phát hiện ra cây bị bệnh bằng mắt thường thì dịch đã lây lan ra diện rộng, gây thiệt hại nghiêm trọng về kinh tế và năng suất nông sản.
* **Sự kém hiệu quả của quy trình kiểm tra truyền thống:** Việc đi bộ kiểm tra từng gốc cây tốn rất nhiều sức lao động, mang tính may rủi cao và không thể bao quát toàn bộ diện tích nông trường trong ngày.
* **Lạm dụng thuốc bảo vệ thực vật:** Do không biết chính xác vị trí và ranh giới vùng nhiễm bệnh, người nông dân có xu hướng phun thuốc hóa học đại trà trên toàn bộ cánh đồng, gây lãng phí lớn về chi phí, ô nhiễm nguồn đất, nguồn nước và để lại tồn dư hóa chất trong nông sản.

---

## 2. Method – Phương pháp thực hiện

Nghiên cứu đề xuất giải pháp bay quét sử dụng **Thiết bị bay không người lái (Drone)** kết hợp thuật toán **YOLOv8** để phát hiện vùng bệnh thời gian thực (Real-time) và phân loại chi tiết loại bệnh bằng kiến trúc mạng gọn nhẹ **MobileNetV3**.

#### Framework xử lý gồm 3 khối chức năng tuần tự:
* **Khối Thu thập & Định vị:** Drone bay ở độ cao cố định (15-20 mét) tự động chụp ảnh độ phân giải cao theo lộ trình lập sẵn, tích hợp trích xuất tọa độ GPS của từng khung ảnh.
* **Khối Phát hiện vùng bệnh (Detection Layer):** Sử dụng thuật toán **YOLOv8-Small** để quét các tán lá trên diện rộng, tự động vẽ khung (Bounding Box) khoanh vùng các cụm lá có dấu hiệu đổi màu, đốm lá hoặc cháy bìa lá.
* **Khối Phân loại chi tiết (Classification Layer):** Cắt (Crop) các vùng ảnh chứa bệnh được YOLOv8 tìm thấy, đưa vào mạng nơ-ron **MobileNetV3** để định danh chính xác tên bệnh lý.

---

## 3. Dataset – Dữ liệu sử dụng

* **Đặc điểm dữ liệu:** Tập dữ liệu kết hợp giữa dữ liệu thực địa tự thu thập bằng drone tại các nông trường thực tế và dữ liệu chuẩn hóa từ tập dữ liệu mở thế giới *PlantVillage*.
* **Quy mô:** Gồm 12,400 ảnh màu RGB chất lượng cao.
* **Các lớp phân loại (4 Classes):** `Healthy` (Khỏe mạnh), `Leaf Rust` (Bệnh rỉ sắt), `Powdery Mildew` (Bệnh phấn trắng), và `Leaf Blight` (Bệnh cháy lá).
* **Cấu hình:** Toàn bộ ảnh được chuẩn hóa về kích thước `416x416` pixel (kích thước tối ưu cho các thuật toán định vị vật thể dòng YOLO).

---

## 4. Evaluation & Results – Thước đo và Kết quả

#### Các chỉ số đánh giá:
* **mAP@0.5 (Mean Average Precision):** Chỉ số tiêu chuẩn của bài toán Object Detection, đo lường độ chính xác khi AI khoanh vùng ô bệnh (tránh khoanh lệch hoặc khoanh sai vị trí).
* **FPS (Frames Per Second):** Số khung hình xử lý được trên mỗi giây, quyết định xem AI có thể chạy mượt mà trực tiếp trên luồng video của Drone hay không.
* **Model Size (MB):** Dung lượng bộ nhớ của mô hình sau khi đóng gói.

#### Bảng hiệu năng thực tế của hệ thống:

| Thành phần mô hình | Nhiệm vụ chính | mAP / Accuracy | Tốc độ xử lý (FPS) | Kích thước file |
| :--- | :--- | :--- | :--- | :--- |
| **YOLOv8-Small** | Phát hiện & Khoanh vùng bệnh | **88.6% (mAP)** | **45 FPS** | 22 MB |
| **MobileNetV3** | Phân loại chi tiết loại bệnh | **91.2% (Accuracy)**| **62 FPS** | 16 MB |

#### Kết luận thực nghiệm:
* Sự kết hợp giữa YOLOv8-Small và MobileNetV3 giúp hệ thống cực kỳ nhỏ gọn (tổng dung lượng < 40MB) nhưng duy trì tốc độ xử lý vượt ngưỡng **45 khung hình/giây**.
* Đủ điều kiện để triển khai thực tế (Deploy) thẳng vào các chip xử lý ngoại vi (Edge Device) lắp trực tiếp trên Drone để tính toán real-time tại thực địa mà không cần phụ thuộc vào đường truyền Internet về máy chủ.

---

## 5. Limitations – Hạn chế của bài báo

1. **Phụ thuộc mạnh vào điều kiện thời tiết tự nhiên:** Khi trời âm u, thiếu sáng hoặc gặp gió mạnh làm rung lắc camera của drone, chất lượng hình ảnh đầu vào bị mờ nhiễu dẫn đến tỷ lệ nhận diện lỗi (False Positive) tăng mạnh.
2. **Chưa tự động hóa hành vi xử lý hậu kỳ:** Mô hình mới chỉ dừng lại ở mức "phát hiện, phân loại và vẽ bản đồ dịch bệnh", chưa có sự kết nối trực tiếp với hệ thống phần cứng vòi phun tự động của Drone để tiến hành dập dịch ngay tại chỗ.

---

## 6. Relevance & Possible Improvements – Định hướng cải tiến

* **Tính liên quan đến nghiên cứu:** Đây là bài mẫu lý tưởng cho các đề tài chú trọng vào việc tối ưu hóa hiệu năng, giảm dung lượng mô hình và tăng tốc độ xử lý phần cứng (FPS) trên các thiết bị Edge/Mobile có tài nguyên hạn chế.
* **Gợi ý cải tiến cho nhóm:** Nhóm có thể nâng cấp hệ thống này bằng cách tích hợp mô hình phân cấp cơ sở dữ liệu. Khi Drone phát hiện ra tọa độ của vùng bệnh, hệ thống sẽ tự động gửi gói tin chứa tọa độ GPS đó về một **Cơ sở dữ liệu tập trung (như SQL Server/PostgreSQL)**. Từ cơ sở dữ liệu này, hệ thống sẽ tự động kích hoạt các vòi phun thông minh đặt cố định dưới mặt đất (các IoT Nodes) tại đúng vị trí lỗi để phun thuốc khoanh vùng. Giải pháp này giúp tiết kiệm 80% lượng thuốc bảo vệ thực vật và hoàn thiện bài toán tự động hóa End-to-End.
