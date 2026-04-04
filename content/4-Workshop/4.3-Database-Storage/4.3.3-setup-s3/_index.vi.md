---
title : "Thiết lập Amazon S3"
date : 2026-04-03
weight : 3
chapter : false
pre : " <b> 4.3.3. </b> "
---

#### Lưu trữ hình ảnh với Amazon S3

Trong hệ thống E-commerce, việc lưu trữ hình ảnh sản phẩm trong cơ sở dữ liệu RDS là một phương pháp không tối ưu, gây tốn kém và làm chậm tốc độ truy vấn. Thay vào đó, chúng ta sẽ sử dụng **Amazon Simple Storage Service (S3)** để lưu trữ toàn bộ các tệp tin tĩnh (hình ảnh, video) một cách độc lập và an toàn.

---

#### Bước 1: Khởi tạo S3 Bucket

1. Đăng nhập vào **AWS Management Console** và tìm kiếm dịch vụ **S3**.
2. Tại màn hình chính của S3, nhấn vào nút **Create bucket** (Tạo bộ nhớ).
3. Trong phần **General configuration**, nhập tên cho bucket của bạn (Ví dụ: `ecommerce-product-images-cuaban`). Lưu ý rằng tên bucket phải là duy nhất trên toàn cầu trên tất cả các tài khoản AWS.
4. Chọn **AWS Region** trùng với khu vực bạn đã triển khai RDS và ECS trước đó để tối ưu hóa tốc độ kết nối nội bộ.

![Khởi tạo S3 Bucket](/images/4-Workshop/4.3-Database-Storage/4.3.3-setup-s3/step1-create-bucket.png)

#### Bước 2: Cấu hình Quyền truy cập công cộng (Bảo mật)

Theo nguyên tắc bảo mật tiêu chuẩn, chúng ta tuyệt đối không mở S3 cho Internet truy cập trực tiếp. Thay vào đó, chúng ta sẽ khóa hoàn toàn S3 và chỉ cho phép CloudFront (ở bước sau) đọc dữ liệu.

1. Cuộn xuống phần **Block Public Access settings for this bucket**.
2. Đảm bảo rằng tùy chọn **Block all public access** (Chặn tất cả quyền truy cập công cộng) đang ĐƯỢC TÍCH CHỌN. Điều này ngăn chặn bất kỳ ai cố tình truy cập vào đường dẫn trực tiếp của hình ảnh S3.
3. Cuộn xuống cuối trang, giữ nguyên các cài đặt mặc định còn lại (như Mã hóa tự động) và nhấn **Create bucket**.

![Khóa quyền truy cập công cộng S3](/images/4-Workshop/4.3-Database-Storage/4.3.3-setup-s3/step2-block-public.png)

#### Bước 3: Tải lên hình ảnh sản phẩm mẫu

Để có dữ liệu kiểm tra cho các bước thiết lập Frontend sau này, chúng ta cần tải lên một vài hình ảnh mỹ phẩm mẫu.

1. Bấm vào tên Bucket bạn vừa tạo trong danh sách.
2. Tại tab **Objects**, nhấn nút **Upload** (Tải lên).
3. Chọn nút **Add files** và tải lên một vài hình ảnh sản phẩm từ máy tính của bạn (đảm bảo định dạng ảnh phổ biến như JPG hoặc PNG).
4. Nhấn nút **Upload** ở cuối trang và đợi quá trình tải lên hoàn tất 100%.

![Tải hình ảnh mẫu lên S3](/images/4-Workshop/4.3-Database-Storage/4.3.3-setup-s3/step3-upload-images.png)