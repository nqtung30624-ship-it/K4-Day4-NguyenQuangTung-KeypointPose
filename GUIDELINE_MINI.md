# Mini guideline - nhóm: ______  |  người gán: Nguyễn Quang Tùng  |  ngày: 16/09/2026

> Điền file này **trong lúc** gán nhãn, không phải sau khi xong. Mỗi lần bạn dừng lại
> hơn 10 giây để phân vân, đó là một dòng phải ghi vào đây.

## 1. Luật bắt buộc (đã thống nhất cả lớp - không sửa)

- Bộ 17 điểm COCO, đúng tên, đúng thứ tự. Lấy từ file `.SVG` chung.
- Mọi người trong ảnh đều có **đủ 17 điểm**. Điểm không dùng được thì gắn cờ, không xoá.
- Trái/phải tính theo **cơ thể người**, không theo bức ảnh.
- Bị che, còn trong khung -> `v = 1`, **vẫn đặt chấm** ở vị trí ước lượng.
- Ra ngoài mép ảnh -> `v = 0`, **không** đặt chấm.
- Không dùng `Hidden` (`h`) - nó không được lưu vào file.

## 2. Luật của nhóm bạn (phải điền)

| Tình huống | Luật nhóm bạn chọn | Vì sao |
| --- | --- | --- |
| Hông của người mặc quần áo dài | cứ gán vào vị trí nếu không bị che | vẫn sẽ phân biệt được nếu không che |
| Tai bị tóc hoặc mũ bảo hiểm che một phần | bị tóc che thì vẫn coi là nhìn thấy còn mũ che thì gán không thấy | mũ là vật thể che |
| Người bị cắt ở mép ảnh (chỉ thấy từ hông trở lên) | thì xóa phần chân | không thấy chân thì không gán |
| Cổ tay nằm sau tay lái / sau thân mình | vẫn đoán để gán | không bị cắt mép là gán |
| Hai người chồng lên nhau | vẫn đoán bộ phận và gán | vì là còn người nên cần gán |
| Người nhỏ đến mức nào thì không gán nữa | người mờ mà không thể đoán | không nhận diện được |

Với mỗi luật, chèn **một ảnh mẫu** (screenshot từ CVAT) thay vì chỉ viết một câu.
Slide 12 nói rõ: khớp không có bề mặt nhìn thấy được thì phải có ảnh mẫu, không phải
một câu văn chung chung.

## 3. Ba ca mơ hồ đã gặp (bắt buộc, ghi ít nhất 3)

### Ca 1 - ảnh `2`, người thứ `con búp bê`, khớp `không gán`

- Mơ hồ ở chỗ nào: giống hình người 
- Bạn quyết thế nào: không gán
- Vì sao: vì nó đủ bộ phận người nhưng thực chất không phải người
- Nếu người khác quyết ngược lại thì model học sai cái gì: nhận diện vật thể dạng búp bê manocanh thành người

### Ca 2 - ảnh `10`, người thứ `trong ảnh`, khớp `khuỷu tay và cổ tay`

- Mơ hồ ở chỗ nào: bị che bởi con mèo
- Bạn quyết thế nào: đoán tư thế và gán
- Vì sao: ta có thể đoán được
- Nếu người khác quyết ngược lại thì model học sai cái gì: thì sẽ không thành hình người tuy đứng trong giữ hình

### Ca 3 - ảnh `11`, người thứ 'trong `, khớp `hông và chân`

- Mơ hồ ở chỗ nào: bị che mất bởi hàng
- Bạn quyết thế nào: vẫn đoán và gán
- Vì sao: ta có thể đoán được
- Nếu người khác quyết ngược lại thì model học sai cái gì: sẽ không nhận diện được hình người khi ở giữ hình

## 4. Sau khi so visibility report với bạn cùng nhóm

làm cá nhân
