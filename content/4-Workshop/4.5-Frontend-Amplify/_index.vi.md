---
title : "Triển khai Frontend"
date : 2026-04-03
weight : 5
chapter : true
pre : " <b> 4.5. </b> "
---

#### Triển khai giao diện React lên AWS Amplify

Sau khi đã hoàn tất hệ thống Backend và Cơ sở dữ liệu, bước tiếp theo là đưa giao diện người dùng (Frontend) lên môi trường internet. Dự án của chúng ta sử dụng React kết hợp với công cụ Vite.

Để lưu trữ và phân phối giao diện web này tới người dùng với tốc độ cao nhất, chúng ta sẽ sử dụng **AWS Amplify Hosting**. Dịch vụ này không chỉ cung cấp không gian lưu trữ tĩnh an toàn mà còn tự động thiết lập mạng lưới phân phối nội dung (CloudFront) và tự động hóa quy trình triển khai mã nguồn (CI/CD).

#### Lộ trình triển khai Frontend

Để đưa website của bạn lên mạng thành công, hãy thực hiện theo 3 bước sau:

1. **[Kết nối Mã nguồn](./4.5.1-Connect-Repository/)**: Ủy quyền cho AWS Amplify truy cập vào kho lưu trữ GitHub chứa code React của bạn.
2. **[Cấu hình Build & Môi trường](./4.5.2-Build-Settings/)**: Thiết lập các lệnh đóng gói Vite và khai báo các biến môi trường để Frontend biết cách gọi đến API của Backend (ECS).
3. **[Triển khai & Kiểm tra](./4.5.3-Deploy-Verify/)**: Khởi chạy tiến trình xây dựng tự động và truy cập vào tên miền công khai do AWS cung cấp.