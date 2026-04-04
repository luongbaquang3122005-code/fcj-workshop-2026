---
title : "Cấu hình Task Definition"
date : 2026-04-03
weight : 3
chapter : false
pre : " <b> 4.4.3. </b> "
---

#### Bước 1: Khởi tạo Task Definition mới

1. Truy cập vào **AWS Management Console** và tìm kiếm dịch vụ **Elastic Container Service (ECS)**.
2. Ở thanh menu bên trái, chọn **Task definitions**.
3. Nhấn vào nút **Create new task definition** (Tạo bản vẽ cấu hình mới).

![Tạo Task Definition](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.3-Task-Definition/step1-create-task.png)

#### Bước 2: Cấu hình Môi trường và Tài nguyên

1. Trong phần **Task definition family**, đặt tên cho bản cấu hình (Ví dụ: `ecommerce-ai-task`).
2. Tại mục **Infrastructure requirements**, chọn **AWS Fargate** làm nền tảng tính toán.
3. Kéo xuống phần cấu hình tài nguyên (Task size). Vì hệ thống AI chạy TensorFlow khá nặng, hãy chọn **1 vCPU** và **2 GB Memory** để đảm bảo quá trình xử lý không bị gián đoạn.

![Cấu hình Tài nguyên Fargate](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.3-Task-Definition/step2-task-size.png)

#### Bước 3: Cấu hình Container và Cổng kết nối

1. Cuộn xuống phần **Container - 1**.
2. **Name**: Nhập tên cho container (Ví dụ: `ai-backend-container`).
3. **Image URI**: Dán đường dẫn URI mà bạn đã copy từ ECR ở bước trước (Ví dụ: `[ID-Của-Bạn].dkr.ecr.[Region].amazonaws.com/ecommerce-backend-cua-ban:latest`).
4. Tại mục **Port mappings**, nhập **3500** vào ô Container port (Đây là cổng chúng ta đã mở trong file Docker). Giữ nguyên Protocol là **TCP**.

![Cấu hình Container URI và Port](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.3-Task-Definition/step3-container-port.png)

#### Bước 4: Hoàn tất tạo Task

1. Giữ nguyên các thông số môi trường mặc định khác.
2. Cuộn xuống cuối cùng và nhấn **Create**. Bản vẽ hệ thống của bạn đã sẵn sàng để được khởi chạy.

![Hoàn tất tạo Task](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.3-Task-Definition/step4-create-success.png)