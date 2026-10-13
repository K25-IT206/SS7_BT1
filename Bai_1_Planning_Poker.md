# Bài 1 - Phân tích và sửa lỗi Planning Poker cho chức năng đặt xe

## Phần 1 - Phân tích

| Mã | Hợp lý / Chưa hợp lý | Quy tắc bị vi phạm | Hậu quả khi lập kế hoạch Sprint |
|---|---|---|---|
| P1 | Chưa hợp lý | Không được lấy trung bình cho các thẻ lệch nhau; kết quả 4 SP không nằm trên thang điểm của đội (1, 2, 3, 5, 8, 13, 21). | Kế hoạch Sprint bị sai lệch, vì team đang gán một điểm không có trong thang và không phản ánh rủi ro thật sự của công việc. |
| P2 | Chưa hợp lý | Product Owner không được quyết định SP; Developers là người chọn thẻ. Hơn nữa, khi thẻ lệch nhau là dấu hiệu cần làm rõ giả định/rủi ro, không được chốt theo ý PO. | Team sẽ underestimate độ lớn công việc, dẫn đến Sprint không đủ thời gian và xếp ưu tiên sai. |
| P3 | Hợp lý | Đúng quy trình Planning Poker: thẻ lệch nhau được giải thích, rồi chọn lại; cuối cùng cả 4 người đều chọn 5 SP. | Chốt 5 SP phản ánh đúng mức độ tương đối sau khi đã làm rõ giả định, nên lập kế hoạch Sprint ổn định hơn. |
| P4 | Hợp lý (về số điểm, ghi chú sai) | Không vi phạm quy trình vì đã có giải thích và re-vote đồng nhất; tuy nhiên, ghi chú “13 SP = 52 giờ” sai vì SP không quy đổi cố định sang giờ. | Nếu giữ ghi chú sai, đội sẽ hiểu nhầm SP là giờ làm việc, gây lệch kế hoạch và đo lường năng suất. |
| P5 | Chưa hợp lý | PBI chưa đủ rõ và vẫn chốt theo đa số 13 SP, trái với nguyên tắc: thẻ lệch nhau là tín hiệu cần làm rõ thêm; không được chốt khi chưa rõ phạm vi hoặc điều kiện áp dụng. | Team sẽ overestimate công việc, làm kế hoạch Sprint bị quá chặt/chậm và dễ xếp sai ưu tiên. |

## Phần 2 - Sửa lỗi

### P1 - Đăng nhập bằng số điện thoại
- Đội nên dừng ở số 3 hoặc 5 sau khi thảo luận rõ rủi ro tích hợp/OTP/xác thực đa bước. Developers là người chọn lại, không lấy trung bình. 
- Cần hỏi rõ: số điện thoại có dùng cùng cơ chế xác thực hiện tại hay cần tích hợp với SMS/OTP, có trường hợp lỗi xác thực phải xử lý gì không?

### P2 - Thanh toán bằng ví RikkeiPay
- Product Owner chỉ làm rõ giá trị và phạm vi, còn Developers phải chốt SP dựa trên độ lớn công việc, không để PO chọn 5 SP để kịp kế hoạch. 
- Trước khi chọn lại, đội cần làm rõ: có tích hợp với gateway RikkeiPay, có flow hoàn tiền/timeout, có kiểm thử tích hợp và lỗi edge case nào không?

### P5 - Áp mã giới thiệu bạn bè
- Đội nên tạm dừng ước lượng và làm rõ câu hỏi: mã giới thiệu có thể dùng đồng thời với khuyến mãi khác, có giới hạn theo điều kiện nghiệp vụ, có cần xử lý logic ở backend và frontend không? 
- Sau khi làm rõ phạm vi, Developers chọn lại thẻ theo giá trị tương đối, không chốt theo số đông khi thẻ lệch nhau.

---

### Kết luận ngắn
- P3 và P4 là các PBI đã chốt đúng quy trình, dù P4 có ghi chú sai về quy đổi giờ. 
- P1, P2, P5 là các trường hợp bị vi phạm nguyên tắc Planning Poker và cần làm rõ thêm trước khi chốt lại.
