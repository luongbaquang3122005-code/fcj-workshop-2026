---
title : "Khởi chạy ECS Service"
date : 2026-04-03
weight : 4
chapter : false
pre : " <b> 4.4.4. </b> "
---

#### Bước 1: Tạo Cluster (Cụm máy chủ)

1. Tại màn hình của dịch vụ **ECS**, chọn mục **Clusters** ở menu bên trái.
2. Nhấn nút **Create cluster**.
3. Nhập tên Cluster (Ví dụ: `Ecommerce-AI-Cluster`).
4. Tại phần **Infrastructure**, đảm bảo tùy chọn **AWS Fargate (serverless)** đã được chọn. Nhấn **Create** và chờ khoảng 1 phút để cụm được tạo.

![Tạo ECS Cluster](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.4-ECS-Service/step1-create-cluster.png)

#### Bước 2: Tạo Dịch vụ (Service) trong Cluster

1. Bấm vào tên Cluster bạn vừa tạo.
2. Tại tab **Services**, nhấn nút **Create**.
3. Tại phần **Compute options**, đảm bảo chọn **Fargate**.
4. Tại phần **Deployment configuration**:
   * **Task definition**: Mở danh sách thả xuống và chọn `ecommerce-ai-task` mà bạn đã tạo ở bước 4.4.3.
   * **Service name**: Nhập tên cho dịch vụ này (Ví dụ: `ai-backend-service`).

![Cấu hình ECS Service](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.4-ECS-Service/step2-config-service.png)

#### Bước 3: Cấu hình Mạng (Networking & Security Group)

1. Cuộn xuống phần **Networking**. Mục VPC và Subnets bạn có thể giữ nguyên mặc định.
2. Tại phần **Security group**, chọn **Create a new security group**.
3. Đặt tên là `ai-backend-sg`.
4. Trong phần **Inbound rules**, cấu hình như sau để cho phép lưu lượng truy cập gọi vào API của bạn:
   * **Type**: Custom TCP
   * **Port range**: 3500
   * **Source**: Anywhere (0.0.0.0/0)

![Cấu hình Security Group Port 3500](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.4-ECS-Service/step3-network-sg.png)

#### Bước 4: Triển khai và Kiểm tra

1. Cuộn xuống cuối trang và nhấn **Create**.
2. AWS sẽ bắt đầu cấp phát tài nguyên và tải Image từ ECR về để chạy. Quá trình này mất khoảng 2-3 phút.
3. Khi cột trạng thái (Status) của dịch vụ chuyển sang màu xanh lá với chữ **Active** (hoặc Running), dịch vụ AI của bạn đã chính thức trực tuyến!

![Dịch vụ chạy thành công](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.4-ECS-Service/step4-service-running.png)