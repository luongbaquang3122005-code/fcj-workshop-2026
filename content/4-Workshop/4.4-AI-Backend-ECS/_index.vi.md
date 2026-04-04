---
title : "Triển khai AI Backend"
date : 2026-04-03
weight : 4
chapter : true
pre : " <b> 4.4. </b> "
---

#### Triển khai AI Backend trên AWS

Trong phần này, bạn sẽ thực hiện đóng gói và triển khai mã nguồn Backend AI (bao gồm Node.js và các mô hình Python phân tích da mặt) lên môi trường đám mây. Việc sử dụng kiến trúc Container kết hợp với các dịch vụ phi máy chủ giúp hệ thống cô lập môi trường chạy an toàn và quản lý tài nguyên tính toán một cách linh hoạt.

#### Nội dung

- [Đóng gói với Docker](4.4.1-Docker-Packaging/)
- [Lưu trữ trên Amazon ECR](4.4.2-Amazon-ECR/)
- [Cấu hình Task Definition](4.4.3-Task-Definition/)
- [Khởi chạy ECS Service](4.4.4-ECS-Service/)
- [Tối ưu hóa API với CloudFront](4.4.5-API-CloudFront/)

---

### Tại sao nội dung này quan trọng?
* **Đồng nhất môi trường (Environment Consistency)**: Đóng gói bằng Docker đảm bảo mã nguồn chứa nhiều thư viện phức tạp (như TensorFlow, OpenCV) hoạt động ổn định trên môi trường AWS Cloud giống hệt như máy tính cá nhân.
* **Khả năng mở rộng tự động (Scalability)**: Vận hành trên Amazon ECS Fargate cho phép phân hệ AI tự động cấp phát và mở rộng tài nguyên (RAM/CPU) một cách độc lập khi có nhiều lưu lượng phân tích ảnh tải lên cùng lúc, tránh tình trạng quá tải hoặc sập hệ thống.
* **Bảo mật và Giảm độ trễ API**: Sử dụng CloudFront làm proxy cho ECS giúp ẩn địa chỉ IP thật của máy chủ, định tuyến lưu lượng qua mạng lưới cáp quang nội bộ của AWS và sẵn sàng để gắn tường lửa WAF bảo vệ.