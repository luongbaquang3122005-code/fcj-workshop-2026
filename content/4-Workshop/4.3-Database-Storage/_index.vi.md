---
title : "Thiết lập Lưu trữ & Dữ liệu"
date : 2026-04-03
weight : 3
chapter : true
pre : " <b> 4.3. </b> "
---

#### Tổng quan về Lưu trữ và Cơ sở dữ liệu

Trong chương này, chúng ta sẽ xây dựng nền tảng dữ liệu cho website E-commerce. Một hệ thống thực tế cần phân loại dữ liệu thành hai nhóm chính:
1. **Dữ liệu có cấu trúc**: Thông tin sản phẩm, đơn hàng, người dùng được lưu trữ trong **Amazon RDS (PostgreSQL)**.
2. **Dữ liệu tĩnh (Media)**: Hình ảnh sản phẩm, banner được lưu trữ tại **Amazon S3** và phân phối tốc độ cao qua **Amazon CloudFront**.

Việc tách biệt này giúp hệ thống của bạn đạt hiệu suất tối đa và tiết kiệm chi phí băng thông.

#### Nội dung

- [Thiết lập Database trên RDS](4.3.1-setup-rds/)
- [Config Prisma](4.3.1-config-prisma/)
- [Thiết lập Lưu trữ S3](4.3.2-setup-s3/)
- [Phân phối ảnh qua CloudFront](4.3.3-cloudfront-s3/)

---

### Tại sao kiến trúc này quan trọng?
* **Tối ưu hóa tốc độ (CDN)**: Thay vì tải ảnh trực tiếp từ S3, CloudFront sẽ lưu bản sao tại các điểm gần người dùng nhất (Edge Locations), giúp website tải cực nhanh.
* **Bảo mật truy cập S3**: Bằng cách sử dụng **Origin Access Control (OAC)**, chúng ta có thể khóa quyền truy cập trực tiếp vào S3, buộc mọi yêu cầu phải đi qua CloudFront.
* **Quản lý Prisma**: Giúp mã nguồn Node.js giao tiếp với RDS một cách an toàn và đồng bộ hóa cấu trúc bảng dễ dàng.