---
title : "Giới thiệu"
date : 2026-04-02
weight : 1
chapter : false
pre : " <b> 4.1. </b> "
---

#### Giới thiệu về Kiến trúc Hệ thống

+ Các hệ thống thương mại điện tử tích hợp AI hiện đại yêu cầu sự tách biệt rõ ràng giữa giao diện tương tác và bộ phận xử lý tính toán để đảm bảo hiệu suất.
+ Trong dự án này, hệ thống sẽ phân tách hoàn toàn mã nguồn **Frontend** (giao diện React) và **Backend AI** (Pipeline Python và Controller Node.js). Mọi thành phần đều tận dụng các dịch vụ phi máy chủ (Serverless) và dịch vụ quản lý toàn phần (Managed Services) của AWS để quá trình vận hành được tự động hóa, giảm thiểu rủi ro quá tải khi phân tích AI.

#### Tổng quan về workshop

Trong workshop này, bạn sẽ từng bước triển khai và kết nối hai phân hệ chính của dự án:

+ **Phân hệ Frontend (Tương tác người dùng):** Mã nguồn Reactsẽ được lưu trữ và tự động triển khai thông qua **AWS Amplify**. Các hình ảnh sản phẩm, ảnh chân dung người dùng tải lên sẽ được lưu tại **Amazon S3** và truyền tải siêu tốc qua mạng lưới **Amazon CloudFront**. Giao diện website cũng là nơi tiếp nhận câu hỏi của khách hàng dành cho Chatbot và chuyển tiếp yêu cầu về phía Backend để xử lý.
+ **Phân hệ Backend & AI (Xử lý tác vụ nặng):** Mã nguồn xử lý AI phân tích da mặt (gồm 4 models) cùng với các API nội bộ sẽ được đóng gói thành một Docker Image duy nhất. Image này sẽ được tải lên **Amazon ECR** và vận hành trên nền tảng **Amazon ECS Fargate**.Đối với tính năng Chatbot, Backend sẽ đóng vai trò trung gian: tiếp nhận yêu cầu từ người dùng, kiểm tra điều kiện truy cập hợp lệ, sau đó mới gửi dữ liệu tới **Amazon Bedrock** để sinh câu trả lời và phản hồi lại cho khách hàng. Cách tiếp cận này giúp hệ thống cấp phát tài nguyên tính toán mạnh mẽ một cách độc lập mà không cần duy trì máy chủ vật lý. Dữ liệu sản phẩm, doanh thu và kết quả phân tích AI sẽ được truy xuất và lưu trữ an toàn trong **Amazon RDS** thông qua Prisma ORM.
+ Để đảm bảo an toàn cho dự án, một lớp bảo mật **AWS WAF** sẽ được thiết lập ở ngoài cùng để chặn các lưu lượng truy cập bất thường và bảo vệ dữ liệu khách hàng.

![Tổng quan kiến trúc hệ thống AI E-commerce](/images/4.1-Workshop-overview/architecture-diagram.png)