---
title : "Database Setup"
date : 2026-04-02 
weight : 1
chapter : false
pre : " <b> 4.3.1 </b> "
---

### Introduction to Database Setup

In a real-world system, data needs to be stored in a secure, automatically backed-up, and easily scalable location. Instead of manually installing a database on a virtual server, we will use **Amazon RDS (Relational Database Service)**.

To interact with **Amazon RDS** from the Node.js source code (Backend), we will use **Prisma ORM**. Prisma makes defining table structures and querying data much safer and more intuitive compared to writing raw SQL queries.

---

### Step 1: Initialize Amazon RDS (PostgreSQL)

1. Access the **AWS Management Console** and search for the **RDS** service.
2. Click **Create database**.
3. Under **Choose a database creation method**, select **Standard create**.
4. Under **Engine options**, select **PostgreSQL**.
5. Under **Templates**, select **Free tier** to avoid incurring charges.
6. In the **Settings** section:
   - **DB instance identifier**: `ecommerce-ai-db`.
   - **Master username**: `postgres`.
   - **Master password**: *Enter a strong password and save it carefully.*
7. In the **Connectivity** section:
   - **Public access**: Select **Yes**. 
   > **Note:** In a real production environment, you should select No. We are enabling it here so your local machine can connect for the demo.
8. Click **Create database** (Wait about 5-10 minutes for the system to initialize).

---

### Step 2: Configure Security Group for RDS

Once the RDS status shows as **Available**, you need to allow your personal computer to connect to it:

1. Click on the newly created database name `ecommerce-ai-db`.
2. In the **Connectivity & security** tab, find the **Security** section and click the link for **VPC security groups**.
3. Select that Security Group, switch to the **Inbound rules** tab -> click **Edit inbound rules**.
4. Add a new rule:
   - **Type**: PostgreSQL
   - **Port range**: 5432
   - **Source**: Select **Anywhere-IPv4** (0.0.0.0/0) or **My IP**.
5. Click **Save rules**.
6. Go back to the RDS details page, and copy the **Endpoint** address (e.g., `ecommerce-ai-db.xxxxxx.rds.amazonaws.com`).

---

### Step 3: Install, Configure, and Deploy Prisma

In your Backend source code folder, perform all the following steps to connect and set up the database:

**Code:**
```bash
# 1. Install Prisma and Client libraries
npm install prisma --save-dev
npm install @prisma/client

# 2. Initialize Prisma structure (creates .env file and prisma folder)
npx prisma init

# 3. Configure the environment variable in the .env file (replace with your Password and Endpoint)
# DATABASE_URL="postgresql://postgres:<Your_Password>@<Your_Endpoint>:5432/postgres?schema=public"

# 4. Define the content for the prisma/schema.prisma file: ( Example )
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
#   passwordHash String?        @map("password_hash") // Changed to Optional (?)
#   googleId     String?        @unique @map("google_id") // Stores Google identifier ID
#   authProvider String         @default("LOCAL") @map("auth_provider") // Marker: LOCAL, GOOGLE
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

# 5. Push the table structure to Amazon RDS
npx prisma db push