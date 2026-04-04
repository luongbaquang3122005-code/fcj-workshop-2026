---
title : "Cấu hình Quyền truy cập"
date : 2026-04-03
weight : 1
chapter : false
pre : " <b> 4.6.1. </b> "
---

#### Bước 1: Cơ chế kích hoạt tự động của Amazon Bedrock

1. Đăng nhập vào **AWS Management Console** và truy cập dịch vụ **Amazon Bedrock**.
2. Ở thanh menu bên trái, chọn **Model catalog** (Danh mục mô hình).
3. Tìm và chọn mô hình bạn muốn sử dụng (Ví dụ: **Claude 3 Haiku**).
4. Nhấn vào nút **Open in playground** (Mở trong không gian thử nghiệm). Nếu tài khoản của bạn là tài khoản mới, AWS sẽ hiện một bảng yêu cầu điền thông tin sử dụng. Hãy điền ngắn gọn mục đích (Ví dụ: "Customer support chatbot for e-commerce website") và gửi đi.
5. Sau khi hoàn tất (hoặc thực hiện lệnh gọi API đầu tiên), mô hình sẽ tự động sẵn sàng cho ứng dụng của bạn.

![Truy cập Model Catalog](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.1-Bedrock-Permissions/step1-model-catalog.png)

#### Bước 2: Tạo IAM User cho Bedrock

Thay vì sử dụng tài khoản gốc (Root Account), chúng ta sẽ tạo một tài khoản con (IAM User) chỉ có duy nhất một quyền: Gọi API của Bedrock. Điều này giúp bảo vệ hệ thống của bạn nếu mã nguồn bị lộ.

1. Tìm kiếm và truy cập dịch vụ **IAM (Identity and Access Management)**.
2. Ở menu bên trái, chọn **Users** và nhấn **Create user**.
3. Đặt tên người dùng là `bedrock-api-user` và nhấn **Next**.
4. Tại phần Set permissions, chọn **Attach policies directly** (Gắn chính sách trực tiếp).
5. Trong ô tìm kiếm, gõ `AmazonBedrockFullAccess`, tích chọn vào chính sách này và nhấn **Next**, sau đó nhấn **Create user**.

![Tạo IAM User](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.1-Bedrock-Permissions/step2-create-user.png)

#### Bước 3: Lấy Access Key và Secret Key

1. Bấm vào tên người dùng `bedrock-api-user` bạn vừa tạo.
2. Chuyển sang tab **Security credentials** (Thông tin xác thực bảo mật).
3. Cuộn xuống phần **Access keys** và nhấn **Create access key**.
4. Chọn **Application running outside AWS** (Ứng dụng chạy ngoài AWS) -> Nhấn **Next** -> Nhấn **Create access key**.
5. **CỰC KỲ QUAN TRỌNG:** AWS sẽ hiển thị `Access key ID` và `Secret access key`. Hãy sao chép ngay lập tức và lưu vào một nơi an toàn. Bạn sẽ không thể xem lại `Secret access key` sau khi đóng cửa sổ này.

#### Bước 4: Thiết lập Biến môi trường trong dự án

Bây giờ, hãy mở mã nguồn Backend Node.js của bạn (nơi chứa file `config.js` để kết nối AWS).

1. Tạo hoặc mở file `.env` ở thư mục gốc của dự án Backend.
2. Thêm các biến sau và dán thông tin bạn vừa lấy được từ Bước 3:

```env
AWS_BEDROCK_AWS_REGION="us-east-1" # Hoặc Region bạn đang sử dụng
AWS_BEDROCK_ACCESS_KEY="Điền-Access-Key-Vào-Đây"
AWS_BEDROCK_SECRET_ACCESS_KEY="Điền-Secret-Key-Vào-Đây"