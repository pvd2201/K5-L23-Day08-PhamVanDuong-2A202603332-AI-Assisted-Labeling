# Label contract — Phố châu Á — BỔ SUNG v1.1 — 2A202603332 - Phạm Văn Dương

> Chỉ ghi phần bổ sung so với v1.0. Các thay đổi dưới đây xuất phát từ các ca CAL-01 đến CAL-03.

## 1. Câu hỏi mở đã chốt

| # | Câu hỏi | Quyết định | Ảnh ví dụ | `case_id` |
|---|---|---|---|---|
| 4 | Người trong xe ba bánh có mui và mask phương tiện | Gán người là `person` riêng; không đưa phần người nhìn thấy vào mask phương tiện. Nếu SAM gộp người với xe thì chỉnh mask thủ công. Ngưỡng nhìn thấy 20% của v1.0 không được đo lại trong ca này. | `img_013.jpg` | CAL-02 |

## 2. Ca khó mới

| Ảnh | Tình huống | Máy làm gì (model nào) | Quyết định | Quy tắc mới |
|---|---|---|---|---|
| `img_017.jpg` | Tuk-tuk bị gán nhầm lớp và box còn lỏng | YOLO26 gán thành `car`/`truck`; YOLOE tìm được `three_wheeler` nhưng box lỏng | Dùng YOLOE làm pre-label; người duyệt xác nhận lớp và chỉnh biên box | Mục 2: xác định xe ba bánh theo hình thái, không giữ nhãn do model đề xuất nếu sai; kiểm tra box thủ công |
| `img_029.jpg`, `img_026.jpg` | Hai bẫy `loose` không được phát hiện | Pre-label có box chứa phần nền thừa | Kiểm tra đủ bốn cạnh trước khi chấp nhận | Mục 4.1: kiểm tra độ khít box và loại phần nền thừa |

## 3. Lịch sử thay đổi

| Phiên bản | Thay đổi | Lý do (`case_id`) |
|---|---|---|
| v1.0 | Bản giảng viên | — |
| v1.1 | Làm rõ xử lý mask người lái, kiểm tra lớp/biên box xe ba bánh và kiểm tra độ khít box | CAL-01, CAL-02, CAL-03 |
