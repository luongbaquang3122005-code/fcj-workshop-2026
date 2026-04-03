---
title: "Bản đề xuất"
date: 2026-31-03
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# E-commerce Cosmetic Platform  
<div style="text-align: center;">

## Nền tảng thương mại điện tử chăm sóc da tích hợp AI & AWS Cloud

</div>  

---

## 1. Tóm tắt điều hành  

E-commerce Cosmetic Platform là một hệ thống web thương mại điện tử được phát triển nhằm cung cấp các sản phẩm chăm sóc da và làm đẹp cho người dùng. Nền tảng không chỉ hỗ trợ mua sắm trực tuyến mà còn tích hợp tính năng gợi ý sản phẩm dựa trên phân tích da mặt, giúp cá nhân hóa trải nghiệm người dùng.

Hệ thống được triển khai trên nền tảng AWS Cloud với kiến trúc hiện đại, bao gồm frontend sử dụng React, backend Node.js, cơ sở dữ liệu PostgreSQL, cùng với các dịch vụ như CloudFront,Amplify, S3, RDS và ECS Fargate.

Ngoài ra, hệ thống còn tích hợp các cơ chế bảo mật như AWS WAF để nâng cao khả năng phát hiện và phản ứng với các mối đe dọa bảo mật.

---

## 2. Tuyên bố vấn đề  

### *Vấn đề hiện tại*  
Các Website bán hàng trực tuyến hiện nay thường:
- Thiếu khả năng cá nhân hóa sản phẩm theo nhu cầu người dùng  
- Không tích hợp phân tích da hoặc tư vấn thông minh  
- Khó mở rộng hệ thống khi lượng người dùng tăng cao  
- Đối mặt với nhiều rủi ro bảo mật như SQL Injection, DDoS  

### *Giải pháp*  
Hệ thống được xây dựng nhằm:
- Cung cấp nền tảng mua sắm trực tuyến thân thiện  
- Tích hợp tính năng quét da mặt để gợi ý sản phẩm  
- Sử dụng AWS để đảm bảo khả năng mở rộng và hiệu suất  

### *Lợi ích*  
- Cá nhân hóa trải nghiệm người dùng  
- Tăng hiệu suất và độ ổn định hệ thống  
- Dễ dàng mở rộng khi có nhiều người dùng  
- Tăng cường bảo mật  

---

## 3. Kiến trúc giải pháp  

Hệ thống sử dụng kiến trúc Cloud-based, phân chia rõ ràng giữa frontend, backend và database.

### *Luồng hoạt động chính*  
1. Người dùng truy cập hệ thống thông qua CloudFront  
2. Request được kiểm tra bởi WAF  
3. Frontend (React) được host trên AWS Amplify  
4. API request đi qua CloudFront → ALB → ECS Fargate  
5. Backend xử lý logic và kết nối tới RDS (PostgreSQL)  
6. File (image, asset) được lưu trên S3  
7. CloudWatch dùng để logging và monitoring   


![Architecture-Diagram](/images/2-Proposal/architecture-diagram.jpg)


### *Dịch vụ AWS sử dụng*  
- *AWS Amplify*: Host frontend React  
- *Amazon CloudFront*: CDN tăng tốc truy cập  
- *AWS WAF*: Bảo vệ chống tấn công web  
- *Application Load Balancer*: Điều phối traffic  
- *Amazon ECS (Fargate)*: Chạy backend container  
- *Amazon RDS (PostgreSQL)*: Lưu trữ dữ liệu  
- *Amazon S3*: Lưu trữ file và hình ảnh  
- *Amazon CloudWatch*: Logging & monitoring

### *Thiết kế mạng (Networking)*  
- VPC riêng cho hệ thống  
- Public Subnet:
  - ALB  
  - NAT Gateway  
- Private Subnet:
  - ECS Fargate  
  - RDS  
- Internet Gateway cho truy cập internet  

---

## 4. Triển khai kỹ thuật  

### *Các giai đoạn triển khai*  

a. *Nghiên cứu & định hướng*  
   - Xác định yêu cầu hệ thống  
   - Lựa chọn công nghệ (React, Node.js, AWS)  

b. *Thiết kế kiến trúc*  
   - Vẽ sơ đồ hệ thống  
   - Thiết kế VPC, subnet, routing  

c. *Phát triển hệ thống*  
   - Xây dựng frontend bằng React  
   - Xây dựng backend bằng Node.js  
   - Kết nối PostgreSQL  

d. *Triển khai lên AWS*  
   - Deploy frontend bằng Amplify  
   - Deploy backend bằng ECS Fargate  
   - Setup RDS, S3, CloudFront  

e. *Bảo mật & giám sát*  
   - Cấu hình WAF  
   - Thiết lập CloudWatch  
   - Triển khai GuardDuty  

---

## 5. Lộ trình & Mốc triển khai  

- *Tháng 1*:  
  - Học AWS cơ bản  
  - Xây dựng backend & frontend  

- *Tháng 2*:  
  - Thiết kế và triển khai hệ thống AWS  
  - Kết nối các service  

- *Tháng 3*:  
  - Tối ưu hệ thống  
  - Thêm bảo mật (WAF, GuardDuty)  
  - Test và hoàn thiện  

---

## 6. Ước tính ngân sách  

Chi phí dự kiến (Free Tier + mức thấp):

- ECS: ~35 USD/tháng  (1vCPU:0.04$/1hours+2GB:0.004445$/GB+Ram 24/7)
- RDS PostgreSQL: ~0–10 USD/tháng(instance:db.t4g.micro=>0.017$/1h,Storage:20 GB gp2=>0.115$/GB)
- S3: ~0.1 USD/tháng(6MB,100 requests)  
- CloudFront: ~0.5 USD/tháng(10GB traffic/tháng → ~0.5 USD)  
- CloudWatch: ~0.2 USD/tháng(1GB data + ít request → ~0.1 USD/tháng)  
- WAF: ~1 USD/tháng(1 Web ACL + 1 rule)  
- GuardDuty: ~1–2 USD/tháng (CloudTrail:0.8$/1M event)  
- Bedrock: ~1-3$ (0.25$/1M input tokens,1.25$/1M output tokens)

Tổng: khoảng 38.8–51.8 USD/tháng 

---

## 7. Đánh giá rủi ro  

### *Rủi ro*  
- Tấn công web (SQLi, XSS)  
- Lộ thông tin database  
- Quá tải hệ thống  
- Chi phí AWS tăng cao  

### *Giảm thiểu*  
- Sử dụng WAF để filter request  
- Dùng IAM Role thay vì hardcode key  
- Auto scaling ECS  
- Cảnh báo billing  

### *Dự phòng*  
- Backup RDS  
- Snapshot định kỳ  
- Rollback hệ thống  

---

## 8. Kết quả kỳ vọng  

### *Kỹ thuật*  
- Xây dựng hệ thống cloud hoàn chỉnh  
- Triển khai fullstack app trên AWS  
- Áp dụng bảo mật thực tế  

### *Giá trị*  
- Nâng cao kỹ năng AWS & DevOps  
- Hiểu rõ kiến trúc hệ thống thực tế  
- Có thể mở rộng thành sản phẩm thương mại  

---