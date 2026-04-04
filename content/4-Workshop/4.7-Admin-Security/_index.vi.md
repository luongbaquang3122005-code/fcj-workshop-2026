---
title : "Quản trị và Bảo mật"
date : 2026-04-03
weight : 7
chapter : true
pre : " <b> 4.7. </b> "
---

#### Bảo vệ hệ thống với AWS WAF

Dù hệ thống đám mây tự động mở rộng (Serverless/ECS) rất mạnh mẽ, nhưng nếu không có lớp lá chắn bảo vệ, bạn có thể phải trả những hóa đơn khổng lồ do bị kẻ xấu tấn công từ chối dịch vụ (DDoS) hoặc spam gọi API AI (Bedrock). 

Trong chương này, chúng ta sẽ thiết lập **AWS WAF (Web Application Firewall)** để phân tích từng luồng truy cập và chặn đứng các yêu cầu độc hại ngay từ ngoài biên mạng lưới (Edge Network) của CloudFront, trước khi chúng kịp chạm vào máy chủ Backend của bạn.

#### Nội dung

- [Khởi tạo Web ACL](4.7.1-Create-Web-ACL/)
- [Thiết lập Bộ quy tắc (Rules)](4.7.2-Configure-Rules/)
- [Kiểm tra Tường lửa](4.7.3-Verify-WAF/)

---

### Tại sao nội dung này quan trọng?
* **Chống cạn kiệt tài nguyên**: Ngăn chặn bot spam gọi API lấy dữ liệu sản phẩm hoặc spam Chatbot AI.
* **Bảo vệ lỗ hổng SQL**: Chặn đứng các hành vi chèn mã độc (SQL Injection) nhắm vào cơ sở dữ liệu RDS của bạn.
* **Bảo mật biên mạng**: Gắn WAF trực tiếp lên CloudFront giúp loại bỏ các truy cập xấu từ toàn cầu mà không làm chậm hệ thống Backend.