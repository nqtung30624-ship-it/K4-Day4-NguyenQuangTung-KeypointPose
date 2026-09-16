# Báo cáo Ngày 4 - Keypoint & Pose

Họ tên: Nguyễn Quang Tùng   Nhóm:    Ngày: 16/09/2026

> Cách dùng: copy file này thành `reports/REPORT.md`. Điền bằng số liệu do công cụ sinh ra;
> không tự ước lượng hoặc sửa số trong file JSON.

## 1. Nhãn của tôi

<!-- Lấy số từ reports/visibility_report.md hoặc outputs/visibility_report.json sau Chặng 4.
Số ảnh phải là 20; số skeleton là tổng số người trong 20 ảnh. Thời gian trung bình = tổng
thời gian gán / 20. -->

| Chỉ số | Giá trị |
| --- | ---: |
| Số ảnh đã gán | 20 |
| Số skeleton | 29 |
| v=2 / v=1 / v=0 | 387 / 72 / 0  |
| Thời gian trung bình mỗi ảnh | 3.5 phút |

Ba khớp có `%v=1` cao nhất (chép từ `reports/visibility_report.md`):

1.left_ear
2.right_ear
3.right_ear

Chúng có đúng là những khớp bạn thấy khó gán nhất không? Nếu không, giải thích.
không , vì các khớp tay rất dễ gán , chỉ có phẩn bị ngược so với model
<!-- Trả lời 2–4 câu. Phân biệt “hay bị che” với “khó xác định vị trí giải phẫu”; nêu bằng
chứng nhìn thấy thay vì chỉ nêu cảm giác. -->

## 2. Chấm với gold

<!-- Lấy hai cột từ outputs/eval_vs_gold.json: một lần ngay khi protected release mở và một
lần sau rework. Đếm số phần tử trong từng danh sách lỗi, không tự làm tròn. -->

| Chỉ số | Trước rework | Sau rework |
| --- | ---: | ---: |
| OKS trung bình | 0.945 | 0.944  |
| OKS@0.50 | 0.931 | 1 |
| OKS@0.75 | 0.931 | 1 |
| Lỗi `dao_trai_phai` | 4 | 0 |
| Lỗi `nham_nguoi` | 2 | 0 |
| Lỗi `xoa_khop_bi_che` | 0 | 0 |

**Tôi đã sửa gì giữa hai lần chạy** (ghi cụ thể: ảnh nào, người thứ mấy, khớp nào):

<!-- Mỗi dòng phải có: tên ảnh + người thứ mấy + keypoint + thao tác sửa. Không viết “đã sửa
lại một số lỗi”. -->

-ảnh 13 
-người thứ 2,3
- thiếu 2 người đã bổ sung

**Lỗi đảo trái/phải của tôi xảy ra ở ảnh nào?** Ảnh đó dễ hay khó? Nếu là ảnh dễ,
bạn nghĩ vì sao mình vẫn sai?
không có
<!-- Nếu không có lỗi, ghi rõ “Không có lỗi đảo trái/phải trong toàn bộ 20 ảnh.” -->

## 3. Kiểm chéo

Bạn cùng nhóm: không

Khớp lệch `%v=1` nhiều nhất giữa hai bảng đếm:

| Khớp | Bạn | Họ | Lệch | Nguyên nhân (guideline hay gán sai?) |
| --- | ---: | ---: | ---: | --- |
| | | | | |
| | | | | |

Luật mới đã bổ sung vào `GUIDELINE_MINI.md` sau khi thống nhất:

<!-- Viết một rule kiểm chứng được: điều kiện nhìn thấy/căn cứ vị trí → chọn v=1 hoặc v=0.
Không chỉ ghi “cẩn thận hơn khi gán”. -->

-

## 4. Model

<!-- Chép số từ outputs/eval_model.json sau Chặng 6. “Chênh” = sau fine-tune trừ baseline;
đây là quan sát trên tập test, không phải chất lượng sản phẩm. -->

| Chỉ số | yolo26n-pose gốc | Sau fine-tune | Chênh |
| --- | ---: | ---: | ---: |
| pose_mAP50 | 0.8450 | 0.8450 | +0.0000 |
| pose_mAP50-95 | 0.6853 | 0.6908 | +0.0055 |
| pose_precision | 0.9734 | 0.9792 | +0.0058 |
| pose_recall | 0.8462 | 0.8462 | +0.0000 |
| box_mAP50 | 0.9785 | 0.9600 | -0.0185 |
| box_mAP50-95 | 0.8119 | 0.8041 | -0.0078 |

### Trả lời năm câu hỏi ở cuối notebook

> Mỗi câu cần trỏ tới ảnh/chỉ số cụ thể. Một con số thấp không tự chứng minh nhãn sai;
> kiểm lại bằng bằng chứng thị giác và kết quả gold.

1. `pose_mAP50-95` thay đổi bao nhiêu? Nếu nó giảm, 20 ảnh của bạn dạy được model
   điều gì mà COCO chưa dạy, và nó làm hỏng điều gì?

`pose_mAP50-95` tăng 0.0055, từ 0.6853 lên 0.6908. Điều này cho thấy sau fine-tune,
model có cải thiện nhẹ về độ chính xác định vị keypoint trên nhiều ngưỡng IoU/OKS.
Với bộ 20 ảnh, có thể thấy model học thêm các đặc điểm về pose và vị trí keypoint
trong dữ liệu được gán, nhưng đồng thời không có bằng chứng từ chỉ số này cho thấy
model học được một đặc điểm mới cụ thể mà COCO chưa có. Tuy nhiên, `box_mAP50` giảm
0.0185 và `box_mAP50-95` giảm 0.0078, cho thấy phần phát hiện bounding box bị giảm
trên tập test.

2. `box_mAP` và `pose_mAP` chênh nhau bao nhiêu? Model tìm *người* dễ hơn hay tìm
   *khớp* dễ hơn? Vì sao?

Ở mAP50-95, `box_mAP50-95` của model gốc là 0.8119, cao hơn `pose_mAP50-95` là
0.6853, chênh 0.1266. Sau fine-tune, box mAP50-95 là 0.8041 và pose mAP50-95 là
0.6908, chênh 0.1133. Điều này cho thấy trên tập test, việc xác định bounding box
của người có kết quả cao hơn việc định vị chính xác các keypoint. Lý do là bounding
box chỉ cần bao quanh người, trong khi pose yêu cầu vị trí từng khớp được xác định
chính xác, đặc biệt với các bộ phận bị che khuất hoặc có tư thế khó.

3. Một ảnh test model đoán sai - gọi tên lỗi theo bốn loại của slide 43
   (lệch nhẹ / đảo trái/phải / nhầm người / trượt hẳn): test 04 thiếu bộ phận chân

Ảnh `test_04` có lỗi **trượt hẳn**, vì model không xác định được đầy đủ phần chân.
Đây không chỉ là trường hợp keypoint lệch nhẹ mà là thiếu hẳn bộ phận chân trong
kết quả dự đoán. Nguyên nhân có thể liên quan đến việc phần chân trong ảnh bị che
khuất hoặc khó quan sát.

4. Ảnh nào có OKS thấp nhất giữa nhãn của bạn và model? Ai đúng, và bạn dựa vào đâu?
TRAIN_04 , nhãn đúng vì tôi gán lệch

5. Ảnh bạn gán tệ nhất có *cũng* là ảnh model đoán tệ nhất không? Nếu có, điều đó
   nói gì về bức ảnh đó?
đúng, bức ảnh đó bị che khuất 
## 5. Một rule evidence bạn đã dùng

Chọn một keypoint trong ảnh core mà bạn phải quyết định giữa `v=1` và `v=0`. Nêu ảnh, người,
khớp, bằng chứng nhìn thấy và lý do chọn trạng thái đó trong 3-5 câu.

<!-- Cấu trúc gợi ý: (1) train_XX + người thứ mấy + keypoint; (2) căn cứ thị giác như phần cơ
thể liền kề, trang phục hoặc vật che; (3) vì sao khớp còn trong khung (v=1) hay đã ra khỏi
khung (v=0). -->

Trong ảnh `TRAIN_04`, với người thứ 2 và keypoint ở chân, tôi chọn `v=1` khi phần chân vẫn còn nhìn thấy trong ảnh dù một phần bị che khuất. Căn cứ vào phần cơ thể liền kề và hướng của chân, tôi vẫn xác định được vị trí giải phẫu của khớp. Vì vậy, khớp vẫn nằm trong khung hình và có đủ bằng chứng để gán vị trí, nên không chọn `v=0`. Rule tôi sử dụng là: nếu còn bằng chứng thị giác đủ để xác định vị trí giải phẫu của khớp thì giữ `v=1`, chỉ chọn `v=0` khi khớp bị che hoàn toàn hoặc không thể xác định vị trí một cách đáng tin cậy.
