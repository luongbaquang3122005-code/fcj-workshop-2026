---
title : "Lưu trữ trên Amazon ECR"
date : 2026-04-03
weight : 2
chapter : false
pre : " <b> 4.4.2. </b> "
---

#### Bước 1: Truy cập Amazon ECR và Tạo kho lưu trữ

1. Đăng nhập vào **AWS Management Console** và tìm kiếm dịch vụ **Elastic Container Registry (ECR)**.
2. Tại màn hình chính của ECR, nhấn vào nút **Create repository** để bắt đầu tạo kho lưu trữ mới.

![Truy cập ECR](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.2-Amazon-ECR/step1-navigate.png)
#### Bước 2: Cấu hình thông tin Repository

1. Trong phần **Repository name**, hãy nhập một tên gợi nhớ do bạn tự đặt (Ví dụ: `ecommerce-backend-cua-ban`).
2. Trong phần **Image tag settings**, bạn chọn **Mutable**.
3. Giữ nguyên các cài đặt mặc định còn lại, cuộn xuống cuối trang và nhấn nút **Create repository**.

![Cấu hình Repository](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.2-Amazon-ECR/step2-config-repo.png)

#### Bước 3: Lấy danh sách câu lệnh thực thi

1. Sau khi tạo thành công, kho lưu trữ của bạn sẽ xuất hiện trong danh sách. Hãy nhấp chọn vào tên repository bạn vừa tạo.
2. Ở góc trên cùng bên phải, nhấn vào nút **View push commands**.

![Nút View Push Commands](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.2-Amazon-ECR/step3-view-btn.png)

#### Bước 4: Thực thi lệnh đẩy Image từ Terminal

1. Lúc này, AWS sẽ hiển thị một bảng Popup chứa 4 bước thực hiện tương ứng với 4 câu lệnh. Các câu lệnh này đã được AWS tự động điền sẵn **ID Tài khoản AWS của bạn**, **Region** và **Tên Repository** mà bạn vừa đặt.
2. Mở Terminal (hoặc Command Prompt) trên máy tính cá nhân của bạn, di chuyển đến thư mục chứa file thiết lập Docker.
3. Lần lượt sao chép từng câu lệnh trên màn hình console và dán vào Terminal để chạy. Quá trình này bao gồm: Đăng nhập, Xây dựng (Build) Image, Gắn thẻ (Tag) và Đẩy (Push) lên Cloud.

#### Bước 5: Kiểm tra kết quả trên ECR

1. Sau khi lệnh cuối cùng chạy xong 100% trên Terminal, hãy đóng bảng Popup và tải lại trang web (Refresh) kho lưu trữ ECR của bạn.
2. Bạn sẽ thấy một bản ghi mới xuất hiện với thẻ (Image tag) là `latest`. 
3. Hãy chú ý và sao chép lại cột **URI** ở tab Repositories (Nó sẽ có định dạng `[ID-Của-Bạn].dkr.ecr.[Region-Của-Bạn].amazonaws.com/[Tên-Repo-Của-Bạn]:latest`). Chúng ta sẽ dùng đoạn URI này cho bước cấu hình máy chủ tiếp theo.

![Kết quả Image trên ECR](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.2-Amazon-ECR/step4-result-uri.png)