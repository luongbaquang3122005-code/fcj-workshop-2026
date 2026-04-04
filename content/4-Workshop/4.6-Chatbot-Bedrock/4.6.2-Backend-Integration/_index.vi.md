---
title : "Tích hợp Bedrock Backend"
date : 2026-04-03
weight : 2
chapter : false
pre : " <b> 4.6.2. </b> "
---

#### Triển khai logic Chatbot trên Backend

Sau khi đã cấu hình xong quyền truy cập ở bước trước, chúng ta sẽ bắt tay vào việc viết mã nguồn Backend để kết nối và điều khiển mô hình trí tuệ nhân tạo trên **Amazon Bedrock**. Phần này tập trung vào việc cài đặt các công cụ cần thiết, khởi tạo kết nối an toàn sử dụng thông tin cấu hình của bạn, và xây dựng một API đơn giản để xử lý tin nhắn từ người dùng.

---

#### Bước 1: Chuẩn bị thư viện cần thiết

Để ứng dụng Node.js của bạn có thể giao tiếp được với dịch vụ Bedrock, bước đầu tiên là bạn cần cài đặt bộ thư viện phát triển tương ứng. Thư viện này cung cấp các công cụ và câu lệnh chuẩn để gửi yêu cầu và nhận phản hồi từ các mô hình AI một cách dễ dàng.


#### Bước 2: Khởi tạo Bedrock Client

Tiếp theo, hãy tạo hoặc mở một file controller thích hợp trong dự án Backend của bạn. Trong file này, bạn sẽ tiến hành import thư viện Bedrock vừa cài đặt và cả file cấu hình `config.js` mà bạn đã thiết lập ở bước trước. Sau đó, bạn cần khởi tạo một đối tượng client mới, đóng vai trò như một "cổng kết nối" an toàn. Khi khởi tạo, bạn hãy chắc chắn truyền vào các giá trị **region**, **credentials** (gồm **accessKeyId** và **secretAccessKey**), và **maxAttempts** lấy trực tiếp từ đối tượng **config** của bạn.

![Khởi tạo Bedrock Client sử dụng thông tin cấu hình](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.2-Backend-Integration/step2-initialize-client.png)

#### Bước 3: Viết hàm xử lý API Chatbot

Cuối cùng, hãy viết một hàm xử lý API chuyên biệt để đảm nhận luồng hội thoại. Hàm này sẽ thực hiện các nhiệm vụ sau: nhận tin nhắn được gửi từ giao diện React Backend (đã mô tả luồng trong phần Giới thiệu); đóng gói tin nhắn này cùng với các tham số cần thiết khác (chọn mô hình AI phù hợp, ví dụ mô hình Claude 3 Haiku, thiết lập số lượng token tối đa) thành một cấu trúc yêu cầu chuẩn mà mô hình AI yêu cầu; sử dụng client đã khởi tạo ở trên để gửi yêu cầu này đến Bedrock và đợi phản hồi; sau khi nhận được phản hồi thành công, hàm sẽ giải mã dữ liệu (thường từ dạng Buffer sang JSON) và trích xuất văn bản phản hồi do AI tạo ra; cuối cùng, trả văn bản phản hồi này về cho giao diện React Frontend để hiển thị cho người dùng.

![Hàm xử lý API Chatbot nhận và trả lời tin nhắn](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.2-Backend-Integration/step3-create-api.png)