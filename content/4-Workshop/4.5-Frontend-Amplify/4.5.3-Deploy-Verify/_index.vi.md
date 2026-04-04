---
title : "Triển khai và Kiểm tra"
date : 2026-04-03
weight : 3
chapter : false
pre : " <b> 4.5.3. </b> "
---

#### Bước 1: Theo dõi quá trình Triển khai tự động (CI/CD)

1. Ngay sau khi nhấn **Save and deploy** ở bước trước, AWS Amplify sẽ tự động chuyển bạn đến màn hình quản lý tiến trình của nhánh mã nguồn (ví dụ: nhánh `main`).
2. Tại đây, bạn sẽ thấy một biểu đồ tiến trình gồm 4 bước liên tiếp: **Provision** (Cấp phát) ➔ **Build** (Xây dựng) ➔ **Deploy** (Triển khai) ➔ **Verify** (Xác minh).
3. Quá trình này sẽ mất khoảng 3 đến 5 phút để Amplify tải mã nguồn React của bạn về, chạy lệnh `npm run build` và phân phối các tệp tĩnh lên hệ thống mạng lưới CloudFront toàn cầu.

#### Bước 2: Truy cập trang web trực tuyến

1. Khi cả 4 bước trong biểu đồ tiến trình đều chuyển sang biểu tượng dấu tích màu xanh lá cây, việc triển khai đã hoàn tất thành công.
2. Ở góc trên bên trái màn hình, ngay dưới tên nhánh (Branch), bạn sẽ thấy một đường dẫn liên kết URL công khai do AWS cung cấp (Thường có định dạng: `https://[tên-nhánh].[mã-id].amplifyapp.com`).
3. Hãy nhấp vào đường dẫn này để mở giao diện Frontend trang web E-commerce của bạn trên một tab trình duyệt mới.

![Truy cập Domain Amplify](/images/4-Workshop/4.5-Frontend-Amplify/4.5.3-Deploy-Verify/step2-domain.png)

#### Bước 3: Kiểm tra tích hợp Frontend và Backend

Để chắc chắn rằng toàn bộ hệ thống từ đầu đến cuối đã hoạt động, chúng ta cần kiểm tra luồng kết nối cơ bản nhất: Tải dữ liệu sản phẩm.

1. Trên giao diện trang web vừa mở, hãy điều hướng đến trang danh sách sản phẩm (hoặc trang chủ).
2. Mở cửa sổ **Developer Tools** trên trình duyệt (Nhấn F12) và chuyển sang tab **Network** (Mạng).
3. Tải lại trang web (F5). Bạn sẽ thấy Frontend gửi một yêu cầu (Request) đến địa chỉ IP/Domain của **Amazon ECS** mà bạn đã cấu hình trong Biến môi trường ở phần trước để gọi API lấy sản phẩm.
4. Nếu màn hình trang web hiển thị thông tin sản phẩm thành công (dữ liệu được kéo về từ cơ sở dữ liệu RDS), xin chúc mừng! Giao diện React đã kết nối trơn tru với hệ thống Backend của bạn.
5. 
![Kiểm tra Web E-commerce](/images/4-Workshop/4.5-Frontend-Amplify/4.5.3-Deploy-Verify/step3-verify.png)