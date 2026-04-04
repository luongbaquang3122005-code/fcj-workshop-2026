---
title : "Kết nối Mã nguồn"
date : 2026-04-03
weight : 1
chapter : false
pre : " <b> 4.5.1. </b> "
---

#### Bước 1: Truy cập dịch vụ AWS Amplify

1. Đăng nhập vào **AWS Management Console** và tìm kiếm dịch vụ **AWS Amplify**.
2. Tại trang chủ của Amplify, cuộn xuống phần **Amplify Hosting** (Lưu trữ web tĩnh).
3. Nhấn vào nút **Get started** (Bắt đầu) hoặc **Host your web app** tùy thuộc vào giao diện hiển thị của bạn.

![Truy cập Amplify Hosting](/images/4-Workshop/4.5-Frontend-Amplify/4.5.1-Connect-Repository/step1-navigate.png)

#### Bước 2: Chọn nhà cung cấp mã nguồn (GitHub)

Để Amplify có thể tự động lấy code và triển khai, bạn cần cấp quyền truy cập vào kho lưu trữ của mình.

1. Tại màn hình lựa chọn kho lưu trữ, hãy đánh dấu chọn vào **GitHub** (hoặc GitLab/Bitbucket tùy thuộc vào nơi bạn đang lưu trữ mã nguồn React Vite).
2. Nhấn nút **Continue** (Tiếp tục).
3. Một cửa sổ ủy quyền của GitHub sẽ bật lên. Hãy đăng nhập tài khoản GitHub của bạn và nhấn nút **Authorize AWS Amplify** để cấp quyền cho AWS đọc mã nguồn.

![Ủy quyền kết nối GitHub](/images/4-Workshop/4.5-Frontend-Amplify/4.5.1-Connect-Repository/step2-github-auth.png)

#### Bước 3: Lựa chọn Repository và Branch

1. Sau khi ủy quyền thành công, bạn sẽ được tự động chuyển hướng trở lại giao diện màn hình của AWS Amplify.
2. Tại mục **Recently updated repositories** (Kho lưu trữ cập nhật gần đây), hãy mở danh sách thả xuống và chọn đúng kho lưu trữ chứa mã nguồn Frontend React của bạn (Ví dụ: `ecommerce-react-frontend`).
3. Tại mục **Branch** (Nhánh), chọn nhánh mà bạn muốn cấu hình triển khai tự động (thông thường là nhánh `main` hoặc `master`).
4. Đảm bảo hộp thoại "Connecting a monorepo" KHÔNG được đánh dấu (vì dự án của chúng ta đã tách riêng Frontend và Backend).
5. Nhấn **Next** để chuyển sang bước thiết lập cấu hình Build.

![Chọn Repository và Branch](/images/4-Workshop/4.5-Frontend-Amplify/4.5.1-Connect-Repository/step3-select-repo.png)