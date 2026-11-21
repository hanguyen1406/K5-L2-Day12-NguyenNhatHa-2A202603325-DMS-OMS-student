# Danh sách lớp v0 - G06

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: model cần nhận ra cái này để làm gì?

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_state | open / closed / unknown | Phát hiện buồn ngủ hoặc nhắm mắt kéo dài | Có, trừ khi phản xạ hoặc kính che mắt |
| 2 | gaze_zone | road / mirror / cluster / lap / other | Đánh giá tài xế có nhìn đường hay đang mất tập trung | Có thể nhận nhưng chính xác phụ thuộc chất lượng khuôn mặt |
| 3 | glasses | unknown / none / clear / sun | Ước lượng độ che mắt và điều chỉnh độ tin cậy trạng thái mắt | Có, nhưng bề mặt kính có thể tạo phản xạ |
| 4 | hand | có / không, whose / side / on_wheel | Phát hiện thao tác lái xe hoặc tay rời vô lăng | Có ở điều kiện ánh sáng đủ |
| 5 | phone | held / mounted / lap | Phát hiện tài xế dùng điện thoại để cảnh báo mất tập trung | Thường có, nhưng vật nhỏ có thể khó nhận |
| 6 | face13 | 13 điểm khuôn mặt | Ước lượng pose, yaw, pitch và hướng nhìn | Có với ảnh NIR trong điều kiện mặt đủ lớn |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person | có / không, theo ghế | Nhận diện người trên từng ghế để quản lý khoang hành khách | Có |
| 2 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Cảnh báo người chưa thắt dây hoặc trạng thái dây không xác định | Thường khó nhìn; có thể mất trong IR |
| 3 | child_seat | occupied unknown / no / yes, theo ghế | Nhận biết ghế trẻ em đang dùng để kích hoạt quy tắc an toàn | Có nếu hình dạng và phần trẻ ngồi nhìn rõ |
| 4 | infant_seat | rear / front, theo ghế | Nhận diện ghế em bé và hướng quay để nhắc quy tắc an toàn | Có |
| 5 | object | bag / box / cup / other | Phân loại đồ vật để phát hiện vật để quên hoặc an toàn cabin | Có, tùy kích thước và độ tương phản |
| 6 | face | có / không | Xác định khuôn mặt người trên ghế để hỗ trợ nhãn OMS hoặc DMS | Có trong điều kiện đủ ánh sáng NIR |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: Child seat có được ghi `yes` khi trong ảnh chỉ nhìn thấy trẻ hoặc chỉ nhìn thấy cấu trúc ghế không rõ?
   Khung ví dụ: S03_rgb / S03_ir
   Bạn tạm gán thế nào và vì sao: Dùng `yes` khi thấy trẻ ngồi rõ; dùng `unknown` nếu không xác định được tình trạng bên trong.

2. Câu hỏi: Điện thoại nhỏ bị che một phần có tính là phone nếu không nhìn thấy màn hình và cạnh toàn bộ?
   Khung ví dụ: D03 hoặc khung DMS tương tự
   Bạn tạm gán thế nào và vì sao: Chỉ gán `phone` khi thấy đủ đặc trưng; nếu không chắc thì không vẽ.
