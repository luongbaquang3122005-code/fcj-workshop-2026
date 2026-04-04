---
title : "Cấu hình Build và Môi trường"
date : 2026-04-03
weight : 2
chapter : false
pre : " <b> 4.5.2. </b> "
---

#### Bước 1: Kiểm tra cấu hình Build của Vite

1. Ngay sau khi chọn Repository ở bước trước, AWS Amplify sẽ tự động phát hiện mã nguồn của bạn và sinh ra một tệp cấu hình Build (Build settings).
2. Hãy bấm vào nút **Edit** trong khung Build settings để kiểm tra.
3. Vì chúng ta sử dụng React Vite, hãy đảm bảo rằng lệnh build là `npm run build` và thư mục gốc xuất ra (baseDirectory) được đặt là `dist` (không phải là `build`). Nếu đúng, hãy chuyển sang bước tiếp theo.

![Cấu hình Build Vite](/images/4-Workshop/4.5-Frontend-Amplify/4.5.2-Build-Settings/step1-build-config.png)

#### Bước 2: Thiết lập Biến môi trường (Environment Variables)

Mã nguồn React của bạn cần biết địa chỉ của Backend AI đang chạy ở đâu để gửi ảnh lên phân tích. Chúng ta sẽ truyền thông tin này thông qua Biến môi trường.

1. Cuộn xuống phần **Advanced settings** (Cài đặt nâng cao) và nhấp để mở rộng.
2. Tìm đến mục **Environment variables**.
3. Nhấn vào nút **Add variable** để thêm biến mới.
4. Ở cột **Key**, nhập tên biến mà mã nguồn React của bạn đang gọi (Ví dụ: `VITE_API_URL`).
5. Ở cột **Value**, hãy dán địa chỉ IP công khai hoặc tên miền của cụm **Amazon ECS Fargate** mà bạn đã khởi chạy thành công ở phần 4.4.4 (Lưu ý: Đừng quên thêm `http://` và cổng `:3500` ở cuối).

![Thiết lập biến môi trường](/images/4-Workshop/4.5-Frontend-Amplify/4.5.2-Build-Settings/step2-env-vars.png)

#### Bước 3: Lưu cấu hình

1. Nhấn nút **Next** ở dưới cùng để xác nhận.
2. Màn hình sẽ chuyển sang trang Review (Đánh giá). Kiểm tra lại toàn bộ thông tin một lần cuối và nhấn **Save and deploy** (Lưu và triển khai).

![Lưu và Deploy](/images/4-Workshop/4.5-Frontend-Amplify/4.5.2-Build-Settings/step3-save-deploy.png)