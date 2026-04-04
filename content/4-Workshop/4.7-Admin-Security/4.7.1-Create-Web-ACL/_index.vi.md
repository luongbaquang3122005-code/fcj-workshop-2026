---
title : "Khởi tạo Web ACL"
date : 2026-04-03
weight : 1
chapter : false
pre : " <b> 4.7.1. </b> "
---

#### Xây dựng Bức tường lửa đầu tiên

Bước đầu tiên trong việc bảo mật là tạo một danh sách kiểm soát truy cập web (Web Access Control List - Web ACL). Đây là "trạm gác" nơi bạn sẽ gắn các quy tắc bảo mật sau này và liên kết nó trực tiếp với Bộ cân bằng tải (ALB) của máy chủ Backend.

---

#### Bước 1: Truy cập và Chọn loại tài nguyên (Regional)

1. Đăng nhập vào **AWS Management Console** và tìm kiếm dịch vụ **WAF & Shield**.
2. Ở thanh menu bên trái, chọn **Web ACLs** và nhấn nút **Create web ACL**.
3. Tại phần **Resource type**, hãy chọn **Regional resources (Application Load Balancer)**.
4. Tại ô Region ngay bên dưới, hãy chọn đúng khu vực (Region) mà bạn đã tạo máy chủ ECS và ALB trước đó.
5. Tại phần **Name**, nhập tên cho bức tường lửa của bạn (Ví dụ: `ecommerce-waf-acl`).

![Khởi tạo Web ACL khu vực](/images/4-Workshop/4.7-Admin-Security/4.7.1-Create-Web-ACL/step1-create-acl.png)

#### Bước 2: Liên kết với Application Load Balancer

1. Ngay bên dưới phần tên, tìm đến mục **Associated AWS resources** và nhấn nút **Add AWS resources**.
2. Một bảng danh sách các tài nguyên sẽ hiện ra. Tại loại tài nguyên, chọn **Application Load Balancer**.
3. Tìm và đánh dấu chọn vào tên ALB của bạn (Ví dụ: `ecs-nodejs-alb`). 
4. Nhấn **Add** để lưu lại. Lúc này, bức tường lửa đã biết chính xác nó cần bảo vệ tài nguyên ECS Backend nào.
5. Nhấn **Create** để chuyển sang màn hình tiếp theo.

![Liên kết Web ACL với ALB](/images/4-Workshop/4.7-Admin-Security/4.7.1-Create-Web-ACL/step2-associate-alb.png)
