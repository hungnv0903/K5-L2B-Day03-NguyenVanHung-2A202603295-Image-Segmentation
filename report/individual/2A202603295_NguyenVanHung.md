# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu.

- Mã học viên theo lớp: 2A202603295
- Ngày / CVAT local: 12/11/2026 / CVAT local
- Công cụ đã dùng: Polygon, Brush

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | chưa có | 0 / 2 | 30 |
| cp1_holes | chưa có | 0 / 1 | 3 |
| cp2_slice | chưa có | 0 / 1 | 3 |
| cp5_occlusion | chưa có | 0 / 1 | 3 |
| cp3_thin | chưa có | 0 / 1 | 3 |
| cp4_curb | chưa có | 0 / 1 | 3 |
| cp6_coverage | chưa có | 0 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

*Ghi chú:* Do giới hạn thời gian thực hành trên lớp, ưu tiên hoàn thiện kỹ lưỡng và đúng quy chuẩn 2 task chính gồm `easy_semantic` (3 ảnh) và `medium_instance` (3 ảnh). Các task còn lại chưa kịp thực hiện được ghi rõ là "chưa có", không tạo file ZIP rỗng theo đúng quy định.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Ảnh `000000181542.jpg`, chiếc xe ô tô con (`car`) ở vị trí trung tâm làn đường.
- Class và quy tắc tôi dùng để chọn biên: Class `car`. Dùng công cụ Polygon viền sát theo đường bao thân vỏ, nóc xe và mép bánh xe tiếp giáp với mặt đường nhìn thấy được; không vẽ phần gầm xe bị khuất trong bóng rèm và không khoét thủng kính xe hay gương chiếu hậu.
- Nếu dùng gợi ý sau đó: không dùng gợi ý tự động (không dùng SAM/AI), toàn bộ các vật thể đều được vẽ tay bằng Polygon và Brush để đảm bảo kiểm soát chính xác từng instance.
- Quyết định gán nhãn: Đối với các xe đỗ gần nhau, kiên quyết vẽ thành từng đối tượng riêng biệt trong danh sách Objects (`car #1`, `car #2`), không gộp chung vào một mask.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: Task `easy_semantic`, ảnh `7ee6d192-89e2408b.jpg`, ranh giới mép tiếp giáp giữa lòng đường và vỉa hè bên phải.
- Lỗi thuộc loại: sai lớp / biên
- Bằng chứng tôi nhìn thấy: Do ánh sáng mặt trời chiếu nghiêng và bề mặt vỉa hè có màu xám tương đồng với nhựa đường, lúc đầu dùng cọ vẽ to làm mask `road` bị lấn sang phần gạch lát vỉa hè (`sidewalk`).
- Quy tắc và hành động sửa: Theo quy tắc phân định road - sidewalk theo chức năng và mép bó vỉa: Phóng to (zoom) vùng ranh giới, chuyển sang công cụ Eraser/Brush nhỏ để tỉa lại đường biên sát đúng gờ bó vỉa bê tông, trả lại phần vỉa hè cho nhãn `sidewalk`.
- Sau sửa đã Save và export lại chưa? Đã Save (`Ctrl + S`) và export lại file `easy_semantic.zip`.

Kết quả tự đánh giá: chưa có điểm (kiểm tra trực quan bằng mắt trên CVAT để đảm bảo không còn vùng lem giữa 2 lớp).

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1. `medium_instance` - Ảnh `000000373353.jpg`: Xe có thùng phía sau (xe bán tải / light truck) | Có thể gán nhãn `car` (xe con/bán tải cá nhân) hoặc `truck` (xe tải có thùng chở đồ) | Theo quy chuẩn COCO: Xe bán tải cá nhân có cabin và kích thước tương tự SUV thường xếp vào `car`; xe tải thương mại chuyên dụng với cabin tách rời thùng chở hàng xếp vào `truck`. | Quyết định gán `car` vì đầu cabin liền khối và kiểu dáng phương tiện cá nhân; xin thêm hướng dẫn của coach về tiêu chuẩn kích thước thùng xe khi phân định ranh giới giữa pickup và truck. |
| 2. `easy_semantic` - Ảnh `817bca71-00000000.jpg`: Bậc thềm/tam cấp phía trước tòa nhà | Có thể hiểu là `sidewalk` (lối đi bộ) hoặc `building` (phần cấu trúc gắn liền công trình) | Bậc tam cấp gắn liền với móng và cửa ra vào của công trình, không thuộc hành lang vỉa hè công cộng dành cho người đi bộ lưu thông. | Quyết định gán nhãn `building` bao trùm cả bậc thềm; câu hỏi cho coach là liệu các bậc thềm thấp sát vỉa hè có nên cắt riêng vào sidewalk không. |
| 3. `medium_instance` - Ảnh `000000458325.jpg`: Hai xe đỗ nối đuôi nhau, xe trước che khuất một phần đầu xe sau | Vẽ 1 mask lớn bao cả 2 xe hay bắt buộc tách rời từng xe; phần đầu xe sau bị khuất có vẽ phỏng đoán không | Quy tắc Instance Segmentation: Hai cá thể độc lập phải tách thành 2 instance; quy tắc hình học: chỉ vẽ phần pixel nhìn thấy, không tự phỏng đoán vùng bị che. | Quyết định tách thành 2 đối tượng `car` riêng; xe sau chỉ vẽ từ mép đuôi xe trước trở về sau, không vẽ đè lên phần bị che khuất. |
