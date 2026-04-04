---
title : "Kiểm tra luồng Chatbot"
date : 2026-04-03
weight : 3
chapter : false
pre : " <b> 4.6.3. </b> "
---

#### Hoàn thiện và Kiểm tra hệ thống Chatbot

Với việc Backend đã sẵn sàng tiếp nhận và xử lý tin nhắn bằng Amazon Bedrock, bước cuối cùng của chúng ta là quay trở lại giao diện web trực tuyến trên AWS Amplify để xác minh toàn bộ luồng hoạt động từ góc độ của người dùng cuối. 

Việc kiểm tra này nhằm khẳng định nguyên tắc bảo mật của chúng ta: Giao diện web chỉ giao tiếp với Backend nội bộ, hoàn toàn không để lộ trực tiếp thông tin kết nối AWS ra bên ngoài.

---

#### Bước 1: Truy cập giao diện Chatbot

1. Mở trình duyệt web và truy cập vào đường dẫn công khai của ứng dụng React
2. Điều hướng đến trang hoặc cửa sổ tiện ích chứa tính năng Chatbot tư vấn khách hàng của dự án.
3. Đảm bảo giao diện tải thành công và khung nhập tin nhắn đã sẵn sàng để sử dụng.

![Giao diện tính năng Chatbot trên website](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.3-Frontend-Testing/step1-chatbot-ui.png)

#### Bước 2: Kích hoạt công cụ giám sát mạng

Để quan sát cách hệ thống trao đổi dữ liệu ngầm, chúng ta sẽ sử dụng công cụ dành cho nhà phát triển của trình duyệt.

1. Bấm phím **F12** (hoặc nhấp chuột phải chọn Inspect/Kiểm tra) để mở cửa sổ Developer Tools.
2. Chuyển sang thẻ **Network** (Mạng).
3. Đảm bảo bộ lọc đang hiển thị tất cả các luồng Fetch/XHR để chúng ta có thể theo dõi gói tin API sắp được gửi đi.

![Mở thẻ Network trong Developer Tools](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.3-Frontend-Testing/step2-open-network.png)

#### Bước 3: Gửi yêu cầu và xác minh luồng dữ liệu

1. Tại khung chat trên giao diện web, hãy nhập một câu hỏi tư vấn về sản phẩm mỹ phẩm (Ví dụ: "Da tôi bị khô thì nên dùng loại kem dưỡng nào?") và nhấn nút gửi.
2. Ngay lập tức, hãy quan sát thẻ Network. Bạn sẽ thấy một gói tin gửi đi có đích đến là địa chỉ IP hoặc Tên miền của khối máy chủ **Amazon ECS Backend**, tuyệt đối không phải là địa chỉ trực tiếp của Amazon Bedrock.
3. Chờ đợi trong giây lát để Backend chuyển tiếp yêu cầu đến AI và nhận kết quả.
4. Khi giao diện web hiển thị câu trả lời tự nhiên và chính xác từ Chatbot, quá trình kiểm tra đã thành công mỹ mãn. Hệ thống của bạn đã được tích hợp AI một cách bảo mật và hoạt động hoàn hảo trên đám mây.

![Luồng gọi API và phản hồi thành công từ Chatbot](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.3-Frontend-Testing/step3-verify-flow.png)