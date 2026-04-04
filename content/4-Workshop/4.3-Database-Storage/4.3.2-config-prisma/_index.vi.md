---
title : "Cấu hình và Thực thi Prisma Client"
date : 2026-04-02 
weight : 2
chapter : false
pre : " <b> 4.3.2 </b> "
---

### Cấu hình Prisma Client

Sau khi đã hoàn tất việc đẩy Schema lên Cloud, bước tiếp theo là khởi tạo **Prisma Client**. Đây chính là "cầu nối" cho phép mã nguồn Node.js của bạn có thể hiểu và thao tác với các bảng dữ liệu một cách trực quan.

#### 1. Khởi tạo thư viện Client
Việc khởi tạo giúp Prisma quét lại toàn bộ Schema đã định nghĩa và tạo ra một bộ thư viện riêng biệt, tương ứng hoàn toàn với cấu trúc các bảng như `Customer` trên RDS. Điều này giúp hệ thống tự động gợi ý tên cột và kiểu dữ liệu khi lập trình.

![prisma-generate](/images/4-Workshop/4.3-Database-Storage/prisma-generate.png)

#### 2. Kiểm tra kết cấu thư mục
Sau khi thực thi lệnh khởi tạo, một thư mục đặc biệt sẽ được tạo ra trong `node_modules`. Bạn có thể kiểm tra trạng thái kết nối và cấu trúc dữ liệu thực tế thông qua trình quản lý trực quan của Prisma để đảm bảo mọi thứ đã khớp với AWS RDS.

![prisma-studio](/images/4-Workshop/4.3-Database-Storage/prisma-client-view.png)

---
