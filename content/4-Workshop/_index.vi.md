---
title: "Workshop E-commerce AI"
date: 2026-04-03
weight: 4
chapter: true
pre: " <b> 4. </b> "
---

# Xây dựng Website Thương Mại Điện Tử Tích Hợp AI trên AWS

#### Tổng quan

Hệ thống thương mại điện tử hiện đại đòi hỏi sự kết hợp giữa trải nghiệm người dùng mượt mà và khả năng xử lý dữ liệu phức tạp phía sau. 

Trong bài lab này, chúng ta sẽ học cách triển khai một dự án thực tế tách biệt hoàn toàn giữa **Frontend** (React Vite) và **Backend** (Node.js & Python). Thay vì sử dụng máy chủ truyền thống, chúng ta sẽ tận dụng kiến trúc phi máy chủ (Serverless) của AWS để tự động mở rộng hệ thống. Chúng ta sẽ sử dụng **Amazon ECS Fargate** để xử lý các mô hình AI phân tích da mặt, **AWS Amplify** để phân phối web tĩnh tốc độ cao, và **Amazon Bedrock** để cung cấp tính năng Chatbot tư vấn khách hàng.

#### Nội dung

1. [Giới thiệu kiến trúc hệ thống](4.1-Overview/)
2. [Điều kiện tiên quyết](4.2-Prerequisites/)
3. [Thiết lập Cơ sở dữ liệu RDS](4.3-Database-Storage/)
4. [Triển khai AI Backend với ECS](4.4-AI-Backend-ECS/)
5. [Triển khai Frontend với Amplify](4.5-Frontend-Amplify/)
6. [Tích hợp AI Chatbot Bedrock](4.6-Chatbot-Bedrock/)
7. [Bảo mật WAF và Quản trị](4.7-Admin-Security/)
8. [Dọn dẹp tài nguyên](4.8-Cleanup/)