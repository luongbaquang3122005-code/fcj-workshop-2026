---
title : "Điều kiện tiên quyết"
date : 2026-04-02
weight : 2
chapter : false
pre : " <b> 4.2. </b> "
---

#### Các công cụ và tài khoản cần thiết

Để quá trình thực hành diễn ra suôn sẻ, bạn cần chuẩn bị sẵn các công cụ và môi trường sau trên máy tính cá nhân của mình trước khi bắt đầu triển khai các dịch vụ AWS.

+ **Tài khoản AWS:** Một tài khoản AWS đang hoạt động có quyền quản trị (AdministratorAccess).
+ **Môi trường phát triển:** Máy tính có thể chạy hệ điều hành Windows, macOS hoặc Linux.
+ **Git:** Công cụ quản lý mã nguồn để tải source code của dự án về máy.
+ **Node.js (Phiên bản 20.x trở lên):** Bắt buộc để khởi chạy môi trường React Vite và sử dụng các trình quản lý gói như npm hoặc yarn.
+ **Python (Phiên bản 3.10 trở lên):** Môi trường để chạy thử các file mô hình AI tại local trước khi đóng gói.
+ **Docker Desktop:** Cần thiết để build Docker Image chứa code Backend AI và đẩy lên ECR.
+ **AWS CLI (Command Line Interface):** Phiên bản mới nhất (v2) đã được cài đặt và cấu hình bằng lệnh `aws configure` với thông tin Access Key ID và Secret Access Key từ tài khoản AWS của bạn.