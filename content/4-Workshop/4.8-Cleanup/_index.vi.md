---
title : "Dọn dẹp tài nguyên"
date : 2026-04-03
weight : 8
chapter : false
pre : " <b> 4.8. </b> "
---

#### Ngăn chặn chi phí phát sinh (Cực kỳ quan trọng)

Chúc mừng bạn đã hoàn thành xuất sắc Workshop xây dựng hệ thống E-commerce AI trên AWS! Bạn đã tự tay thiết lập một kiến trúc chuẩn doanh nghiệp phức tạp bao gồm Frontend (Amplify), Backend (ECS), Database (RDS, S3), AI (Bedrock), và Security (WAF).

Tuy nhiên, nền tảng điện toán đám mây tính phí theo thời gian thực (Pay-as-you-go). Nếu bạn không có ý định duy trì website này hoạt động liên tục, bạn **bắt buộc** phải xóa các tài nguyên đã tạo để tránh bị trừ tiền oan.

---

#### Hướng dẫn xóa các dịch vụ theo thứ tự an toàn

Việc xóa tài nguyên cần thực hiện ngược lại với quy trình khởi tạo để tránh lỗi phụ thuộc (Dependency errors). Hãy thực hiện xóa theo đúng trình tự sau:

1. **Xóa AWS WAF:** Truy cập WAF & Shield -> Web ACLs -> Chọn ACL của bạn -> Disassociate (Hủy liên kết với ALB) -> Nhấn Delete.
2. **Xóa CloudFront Distributions:** (Bao gồm CloudFront cho S3 và CloudFront cho API). Truy cập CloudFront -> Chọn Distribution -> Nhấn **Disable** (Vô hiệu hóa) -> Chờ trạng thái chuyển sang Disabled (khoảng 3-5 phút) -> Nhấn **Delete**.
3. **Xóa ECS Backend:** Truy cập ECS -> Clusters -> Chọn Cluster của bạn -> Tab Services -> Chọn Service -> Update (Sửa số lượng Task thành 0) -> Sau đó nhấn Delete Service -> Cuối cùng nhấn **Delete Cluster**.
4. **Xóa Load Balancer (ALB):** Truy cập EC2 -> Load Balancers -> Chọn ALB của bạn -> Nhấn Actions -> **Delete**. Đừng quên xóa luôn các Target Groups liên quan.
5. **Xóa Frontend Amplify:** Truy cập AWS Amplify -> All apps -> Chọn ứng dụng của bạn -> Actions -> **Delete app**.
6. **Xóa Cơ sở dữ liệu RDS:** Truy cập RDS -> Databases -> Chọn DB của bạn -> Actions -> **Delete** (Nhớ bỏ chọn tính năng "Create final snapshot" nếu không cần thiết để tránh mất phí lưu trữ snapshot).
7. **Xóa Lưu trữ S3 & ECR:** - Truy cập S3 -> Chọn Bucket chứa ảnh -> Nhấn **Empty** (Xóa sạch toàn bộ ảnh bên trong trước) -> Nhấn **Delete**.
   - Thực hiện tương tự cho kho chứa ảnh Docker trên **Amazon ECR**.

Một lần nữa, cảm ơn bạn đã nỗ lực theo dõi và hoàn thành trọn vẹn khóa thực hành này. Kiến trúc mà bạn vừa xây dựng là nền tảng vững chắc cho bất kỳ dự án đám mây quy mô lớn nào trong thực tế!