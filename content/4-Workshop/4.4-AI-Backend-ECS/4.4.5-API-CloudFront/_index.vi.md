---
title : "Tối ưu hóa API"
date : 2026-04-03
weight : 5
chapter : false
pre : " <b> 4.4.5. </b> "
---

#### Sử dụng CloudFront làm lớp bảo vệ cho API (Reverse Proxy)

Thay vì để người dùng gọi trực tiếp vào địa chỉ IP của cụm máy chủ ECS (hoặc Load Balancer), chúng ta sẽ đặt một mạng phân phối CloudFront ở phía trước. Điều này giúp tận dụng mạng lưới máy chủ toàn cầu của AWS để giảm độ trễ kết nối, đồng thời che giấu hoàn toàn địa chỉ IP gốc của Backend khỏi các cuộc tấn công quét mạng.

---

#### Bước 1: Khởi tạo CloudFront Distribution cho API

1. Truy cập vào dịch vụ **CloudFront** trên giao diện AWS Console và nhấn nút **Create a CloudFront distribution**.
2. Tại phần **Origin domain**, dán đường dẫn trực tiếp (DNS hoặc IP) của cụm ECS Fargate (hoặc Application Load Balancer) mà bạn đã có được ở bước 4.4.4.
3. Trong phần **Protocol**, chọn **HTTP only** (vì chúng ta đang truyền nhận dữ liệu nội bộ trên cổng 3500) hoặc tùy thuộc vào cấu hình SSL của bạn trên máy chủ.

![Thiết lập Origin trỏ về ECS Backend](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.5-API-CloudFront/step1-api-origin.png)

#### Bước 2: Tắt tính năng Caching (Cực kỳ quan trọng)

API của chúng ta trả về dữ liệu AI phân tích cá nhân hóa và các nội dung Chatbot sinh động. Nếu chúng ta lưu lại bộ nhớ đệm, người dùng sau có thể nhận được kết quả khám da mặt của người dùng trước! Do đó, bắt buộc phải tắt Cache.

1. Cuộn xuống phần **Default cache behavior**.
2. Dưới mục **Cache key and origin requests**, chọn **Cache policy and origin request policy**.
3. Tại danh sách thả xuống của **Cache policy**, hãy tìm và chọn chính sách có tên là **CachingDisabled** (Tuyệt đối không lưu cache).
4. Tại danh sách thả xuống của **Origin request policy**, chọn **AllViewer** (Chuyển tiếp mọi thông tin về Header, Cookies, Query strings từ người dùng xuống thẳng ECS Backend để xử lý).

![Cấu hình vô hiệu hóa bộ nhớ đệm CachingDisabled](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.5-API-CloudFront/step2-disable-cache.png)

#### Bước 3: Triển khai và Cập nhật Endpoint mới

1. Nhấn nút **Create distribution** ở cuối trang và chờ quá trình khởi tạo hoàn tất.
2. Sau khi trạng thái chuyển sang thành công, hãy sao chép **Distribution domain name** mới này. Đây chính là địa chỉ API siêu an toàn của bạn. Hãy ghi nhớ nó để sử dụng điền vào biến `VITE_API_URL` khi triển khai Frontend ở phần 4.5.2.

![Lưu lại URL API an toàn từ CloudFront](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.5-API-CloudFront/step3-secure-endpoint.png)