---
title : "Tích hợp AI Chatbot"
date : 2026-04-03
weight : 6
chapter : true
pre : " <b> 4.6. </b> "
---

#### Tích hợp Chatbot thông minh với Amazon Bedrock

Một website thương mại điện tử mỹ phẩm hiện đại không thể thiếu trợ lý ảo để tư vấn sản phẩm và chăm sóc khách hàng. Trong phần này, chúng ta sẽ sử dụng **Amazon Bedrock** – một dịch vụ quản lý toàn phần cung cấp quyền truy cập vào các mô hình nền tảng (Foundation Models) hàng đầu.

Để đảm bảo bảo mật (Security Best Practices), chúng ta tuyệt đối không gọi Bedrock trực tiếp từ phía Frontend (React). Thay vào đó, giao diện người dùng sẽ gửi câu hỏi về **Amazon ECS Backend**. Backend sẽ đóng vai trò kiểm tra quyền truy cập, sau đó mới gọi API của Bedrock để sinh câu trả lời và trả về cho khách hàng.

#### Nội dung

- [Cấu hình Quyền truy cập Bedrock](4.6.1-Bedrock-Permissions/)
- [Tích hợp Bedrock vào Backend](4.6.2-Backend-Integration/)
- [Kiểm tra luồng Chatbot trên Frontend](4.6.3-Frontend-Testing/)

---

### Tại sao nội dung này quan trọng?
* **Bảo mật API Key**: Việc đặt logic gọi AI ở Backend giúp bảo vệ thông tin xác thực AWS của bạn khỏi việc bị lộ trên trình duyệt của người dùng.
* **Serverless AI**: Amazon Bedrock hoạt động hoàn toàn phi máy chủ. Bạn không cần tải hay duy trì các mô hình ngôn ngữ lớn (LLM) nặng nề, chỉ cần trả tiền cho mỗi API request được thực hiện.