---
title : "Phân phối qua CloudFront"
date : 2026-04-03
weight : 4
chapter : false
pre : " <b> 4.3.4. </b> "
---

#### Bảo mật S3 bằng Origin Access Control (OAC)

Vì chúng ta đã khóa quyền truy cập công cộng của S3 ở bước trước, không ai có thể xem được ảnh sản phẩm. Bây giờ, chúng ta sẽ tạo một mạng lưới CloudFront đứng phía trước S3, đồng thời cấp một "thẻ thông hành" đặc biệt (OAC) để CloudFront có quyền lấy ảnh từ S3 và phân phối cho người dùng.

---

#### Bước 1: Khởi tạo CloudFront Distribution

1. Truy cập **AWS Management Console** và tìm kiếm dịch vụ **CloudFront**.
2. Nhấn nút **Create a CloudFront distribution**.
3. Tại phần **Origin domain**, hãy nhấp vào ô trống và chọn tên S3 Bucket mà bạn vừa tạo ở bước 4.3.3 từ danh sách thả xuống.
4. Ngay khi bạn chọn S3, hệ thống sẽ hiển thị cảnh báo về quyền truy cập. Bỏ qua cảnh báo đó và chuyển sang bước tiếp theo.

![Chọn S3 làm Origin cho CloudFront](/images/4-Workshop/4.3-Database-Storage/4.3.4-CloudFront-S3/step1-select-origin.png)

#### Bước 2: Cấu hình Origin Access Control (OAC)

Đây là bước quan trọng nhất để khóa chặt bảo mật.

1. Tại mục **Settings**, hãy chọn **Use recommended origin settings**.
2. Cuộn xuống cuối cùng và nhấn **Create distribution**.

![Cấu hình Origin Access Control](/images/4-Workshop/4.3-Database-Storage/4.3.4-CloudFront-S3/step2-setup-oac.png)

#### Bước 3: Cập nhật Chính sách cho S3 (Bucket Policy)

CloudFront đã được tạo, nhưng S3 vẫn chưa biết CloudFront là ai để cho phép truy cập.

1. Ngay sau khi nhấn Create ở bước trên, AWS sẽ hiển thị một dải ruy-băng màu xanh lam trên cùng màn hình cảnh báo bạn phải cập nhật chính sách S3.
2. Nhấn vào nút **Copy policy** có sẵn trên thanh thông báo đó.
3. Nhấp vào đường dẫn đi tới S3 bucket của bạn (cũng nằm trên thanh thông báo) để mở trang quản lý S3 trong một tab mới.
4. Tại trang S3, chọn tab **Permissions** (Quyền) và cuộn xuống phần **Bucket policy**.
5. Nhấn **Edit**, dán toàn bộ đoạn chính sách bạn vừa copy vào ô trống, và nhấn **Save changes**.

![Cập nhật Bucket Policy cho S3](/images/4-Workshop/4.3-Database-Storage/4.3.4-CloudFront-S3/step3-bucket-policy.png)

#### Bước 4: Kiểm tra kết quả tải ảnh

1. Quay lại tab CloudFront, chờ khoảng 3-5 phút cho đến khi trạng thái (Status) của Distribution chuyển từ "Deploying" sang thời gian cập nhật hoàn tất.
2. Sao chép tên miền do CloudFront cung cấp ở mục **Distribution domain name** (Ví dụ: `d12345abcdef.cloudfront.net`).
3. Mở tab trình duyệt mới, dán tên miền này và thêm tên một bức ảnh bạn đã tải lên S3 ở bước trước vào cuối (Ví dụ: `d12345abcdef.cloudfront.net/son-moi.png`).
4. Nếu bức ảnh hiển thị thành công, chúc mừng bạn! Kiến trúc lưu trữ của bạn đã đạt chuẩn doanh nghiệp.

![Kiểm tra hình ảnh qua CloudFront](/images/4-Workshop/4.3-Database-Storage/4.3.4-CloudFront-S3/step4-verify-image.png)