---
title : "Thiết lập Bộ quy tắc"
date : 2026-04-03
weight : 2
chapter : false
pre : " <b> 4.7.2. </b> "
---

#### Cấu hình "Vũ khí" cho Tường lửa

Một bức tường lửa sẽ vô tác dụng nếu không có luật lệ. Trong phần này, chúng ta sẽ thêm các bộ quy tắc (Rules) để hướng dẫn WAF cách nhận diện và chặn đứng các luồng truy cập độc hại nhắm vào Application Load Balancer của bạn.

---

#### Bước 1: Thêm Bộ quy tắc do AWS quản lý (Managed Rules)

Thay vì phải tự nghiên cứu các lỗ hổng bảo mật mới nhất, chúng ta sẽ "mượn" danh sách phòng thủ được cập nhật liên tục bởi các chuyên gia bảo mật của AWS.

1. Tại màn hình **Add rules and rule groups**, nhấn vào nút **Add rules** và chọn **Add managed rule groups**.
2. Mở rộng mục **AWS managed rule groups**.
3. Cuộn xuống và bật công tắc (Add to web ACL) cho hai bộ quy tắc sau:
   - **Amazon IP reputation list**: Chặn các địa chỉ IP đã có lịch sử gắn liền với botnet, spam hoặc phần mềm độc hại.
   - **Core rule set**: Bảo vệ chống lại các lỗ hổng web phổ biến nhất (OWASP Top 10) như SQL Injection, Cross-Site Scripting.
4. Cuộn xuống cuối trang và nhấn **Add rules** để quay lại màn hình chính.
5. Tại màn hình Review, kiểm tra lại toàn bộ thông tin và nhấn **Create web ACL**.

![Thêm bộ quy tắc quản lý của AWS](/images/4-Workshop/4.7-Admin-Security/4.7.2-Configure-Rules/step1-managed-rules.png)