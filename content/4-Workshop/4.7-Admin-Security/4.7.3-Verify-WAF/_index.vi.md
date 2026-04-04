---
title : "Kiểm tra Tường lửa"
date : 2026-04-03
weight : 3
chapter : false
pre : " <b> 4.7.3. </b> "
---

#### Giám sát và Xác minh Hệ thống phòng thủ

Bức tường lửa của bạn đã được thiết lập thành công. Bước cuối cùng trong phần bảo mật là xác minh xem các quy tắc (Rules) có đang thực sự hoạt động và chặn các yêu cầu xấu hay không. 

---

#### Bước 1: Theo dõi Bảng điều khiển (Dashboard)

1. Từ giao diện tạo Web ACL thành công ở bước trước, hãy nhấp vào tên Web ACL của bạn (`ecommerce-waf-acl`).
2. Chuyển sang thẻ **Traffic overview** (Tổng quan lưu lượng) hoặc **Bot control** (nếu có).
3. Tại đây, AWS WAF cung cấp một biểu đồ thời gian thực hiển thị tổng số yêu cầu được phép (Allowed requests) và số lượng yêu cầu bị chặn (Blocked requests).
4. Nếu hệ thống mới tạo, biểu đồ này có thể trống. Hãy chờ một vài phút hoặc tiến hành bước tiếp theo để tạo dữ liệu mô phỏng.


#### Bước 2: Thử nghiệm chặn giới hạn tốc độ (Rate-limit Testing)

Để kiểm tra xem quy tắc chống spam AI (`Block-AI-Spam`) có hoạt động không, chúng ta sẽ mô phỏng hành vi của một bot spam.

1. Mở trang web E-commerce của bạn trên trình duyệt.
2. Tìm đến tính năng Chatbot AI tư vấn sản phẩm.
3. Bắt đầu gửi liên tục các tin nhắn ngắn hoặc nhấn F5 (tải lại trang gọi API liên tục) thật nhanh. Mục tiêu là vượt qua con số 100 yêu cầu trong thời gian rất ngắn (như bạn đã cấu hình).
4. Nếu quy tắc hoạt động đúng, sau một số lượng yêu cầu nhất định, trang web của bạn sẽ bắt đầu báo lỗi (thường là lỗi 403 Forbidden). Lúc này, IP của bạn đã bị tường lửa tạm khóa.

#### Bước 3: Phân tích Log yêu cầu bị chặn

1. Quay lại thẻ **Traffic overview** trên AWS WAF console.
2. Lúc này, biểu đồ sẽ xuất hiện các cột màu đỏ (hoặc trạng thái Blocked) tương ứng với hành động spam của bạn.
3. Cuộn xuống phần **Sampled requests** (Yêu cầu lấy mẫu). Tại đây, bạn sẽ thấy danh sách chi tiết các yêu cầu bị chặn, bao gồm địa chỉ IP nguồn, quốc gia, thời gian và quan trọng nhất là **Rule name** (Tên quy tắc) đã thực hiện việc chặn (Trong trường hợp này, nó sẽ hiển thị là `Block-AI-Spam`).
4. Việc tường lửa nhận diện đúng và chặn chính xác quy tắc chứng tỏ hệ thống phòng thủ của bạn đã hoạt động hoàn hảo. 
