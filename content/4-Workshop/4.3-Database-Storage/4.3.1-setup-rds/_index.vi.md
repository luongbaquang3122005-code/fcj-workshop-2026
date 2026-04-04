---
title : "Thiết lập Database"
date : 2026-04-02 
weight : 1
chapter : false
pre : " <b> 4.3.1 </b> "
---

### Giới thiệu về quá trình thiết lập Cơ sở dữ liệu

Trong hệ thống thực tế, dữ liệu cần được lưu trữ ở một nơi an toàn, có khả năng sao lưu tự động và dễ dàng mở rộng. Thay vì tự cài đặt cơ sở dữ liệu trên một máy chủ ảo, chúng ta sẽ sử dụng **Amazon RDS (Relational Database Service)**.

Để tương tác với **Amazon RDS** từ mã nguồn Node.js (phần Backend), chúng ta sẽ sử dụng **Prisma ORM**. Prisma giúp việc định nghĩa cấu trúc bảng và truy vấn dữ liệu trở nên an toàn và trực quan hơn rất nhiều so với việc viết các câu lệnh SQL thuần túy.

---

### Bước 1: Khởi tạo Amazon RDS (PostgreSQL)

1. Truy cập vào **AWS Management Console** và tìm kiếm dịch vụ **RDS**.
2. Chọn **Create database** (Tạo cơ sở dữ liệu).
3. Tại mục **Choose a database creation method**, chọn **Standard create**.
4. Tại mục **Engine options**, chọn **PostgreSQL**.
5. Tại mục **Templates**, chọn **Free tier** (Bậc miễn phí) để tránh phát sinh chi phí.
6. Trong phần **Settings**:
   - **DB instance identifier**: `ecommerce-ai-db`.
   - **Master username**: `postgres`.
   - **Master password**: *Nhập mật khẩu mạnh và lưu lại cẩn thận.*
7. Tại mục **Connectivity**:
   - **Public access**: Chọn **Yes**. 
   > **Lưu ý:** Trong thực tế sản xuất, bạn nên chọn No. Chúng ta bật để máy local của bạn kết nối được phục vụ quá trình thực hành demo.
8. Nhấn **Create database** (Đợi khoảng 5-10 phút để hệ thống khởi tạo).

---

### Bước 2: Cấu hình Security Group cho RDS

Sau khi RDS hiển thị trạng thái **Available**, bạn cần cho phép máy tính cá nhân kết nối đến nó:

1. Bấm vào tên cơ sở dữ liệu `ecommerce-ai-db`.
2. Tại tab **Connectivity & security**, tìm mục **Security** và bấm vào link của **VPC security groups**.
3. Chọn Security Group đó, chuyển sang tab **Inbound rules** -> bấm **Edit inbound rules**.
4. Thêm một quy tắc mới:
   - **Type**: PostgreSQL
   - **Port range**: 5432
   - **Source**: Chọn **Anywhere-IPv4** (0.0.0.0/0) hoặc **My IP**.
5. Bấm **Save rules**.
6. Quay lại trang chi tiết RDS, sao chép địa chỉ **Endpoint** (Ví dụ: `ecommerce-ai-db.xxxxxx.rds.amazonaws.com`).

---

### Bước 3: Cài đặt, Cấu hình và Triển khai Prisma

Tại thư mục mã nguồn Backend, bạn thực hiện toàn bộ các thao tác dưới đây để kết nối và thiết lập database:

**Code:**
```bash
# 1. Cài đặt thư viện Prisma và Client
npm install prisma --save-dev
npm install @prisma/client

# 2. Khởi tạo cấu trúc Prisma (tạo file .env và thư mục prisma)
npx prisma init

# 3. Cấu hình biến môi trường trong file .env (thay Password và Endpoint của bạn)
# DATABASE_URL="postgresql://postgres:<Password_cua_ban>@<Endpoint_cua_ban>:5432/postgres?schema=public"

# 4. Định nghĩa nội dung cho file prisma/schema.prisma: ( Ví dụ )
# generator client {
#   provider = "prisma-client-js"
# }
# datasource db {
#   provider = "postgresql"
#   url      = env("DATABASE_URL")
# }
# model Customer {
#   id           String         @id @default(uuid())
#   firstName    String?        @map("first_name")
#   lastName     String?        @map("last_name")
#   accountName  String         @map("accountName")
#   mail         String         @unique
#   phoneNumber  String?        @map("phone_number") @db.VarChar(10)
#   
#   passwordHash String?        @map("password_hash") // Đổi thành Optional (?)
#   googleId     String?        @unique @map("google_id") // Lưu ID định danh từ Google
#   authProvider String         @default("LOCAL") @map("auth_provider") // Đánh dấu: LOCAL, GOOGLE
#   
#   refreshToken String?        @map("refresh_token")
#   avatarUrl    String?        @map("avatar_url")
#   isActive     Boolean        @default(true) @map("is_active")
#   gender       String?        @db.VarChar(10)
#   birthday     DateTime?      @db.Date
#   skinProfile  Json?          @map("skin_profile")
#   tier         Int?
#   createdAt    DateTime       @default(now()) @map("created_at")
#   addressId    String?        @map("address_id")
#   
#   resetTokens  PasswordResetToken[]
#   address      Address?       @relation(fields: [addressId], references: [id])
#   carts        Cart[]
#   CouponUsage  CouponUsage[]
# 
#   @@map("customer")
# }

# 5. Đẩy cấu trúc bảng lên Amazon RDS
npx prisma db push