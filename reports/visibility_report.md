# Visibility report

- Thư mục nhãn: `dataset/labels/train`
- 20 ảnh, 27 skeleton, trung bình 17.0 khớp có v > 0 mỗi người
- Tổng: v=2 387 | v=1 72 | v=0 0

| # | Khớp | v=2 | v=1 | v=0 | %v=1 |
| ---: | --- | ---: | ---: | ---: | ---: |
| 0 | nose | 24 | 3 | 0 | 11% |
| 1 | left_eye | 20 | 7 | 0 | 26% |
| 2 | right_eye | 23 | 4 | 0 | 15% |
| 3 | left_ear | 15 | 12 | 0 | 44% |
| 4 | right_ear | 16 | 11 | 0 | 41% |
| 5 | left_shoulder | 26 | 1 | 0 | 4% |
| 6 | right_shoulder | 27 | 0 | 0 | 0% |
| 7 | left_elbow | 23 | 4 | 0 | 15% |
| 8 | right_elbow | 25 | 2 | 0 | 7% |
| 9 | left_wrist | 25 | 2 | 0 | 7% |
| 10 | right_wrist | 22 | 5 | 0 | 19% |
| 11 | left_hip | 24 | 3 | 0 | 11% |
| 12 | right_hip | 23 | 4 | 0 | 15% |
| 13 | left_knee | 24 | 3 | 0 | 11% |
| 14 | right_knee | 22 | 5 | 0 | 19% |
| 15 | left_ankle | 24 | 3 | 0 | 11% |
| 16 | right_ankle | 24 | 3 | 0 | 11% |

## Đọc bảng này thế nào

1. Khớp nào có **%v=1 cao**: khớp hay bị che. Cổ tay và hông thường là hai vị trí cần xem lại guideline trước khi kết luận.
2. Khớp nào có **v=0 cao bất thường**: mọi người đang dùng Outside ở chỗ đáng lẽ là Occluded. Đó là lỗi số 3 của slide 46, và nó xoá thẳng khớp đó khỏi bảng điểm OKS.
3. Khi so hai người: **lệch lớn = bất đồng về guideline**, không phải về bức ảnh. Sửa guideline trước, sửa nhãn sau.
