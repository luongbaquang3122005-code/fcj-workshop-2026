---
title : "Amazon S3 Setup"
date : 2026-04-03
weight : 3
chapter : false
pre : " <b> 4.3.3. </b> "
---

#### Hosting Images with Amazon S3

In an E-commerce system, storing product images within the RDS database is a highly suboptimal practice that increases costs and slows down query performance. Instead, we will use **Amazon Simple Storage Service (S3)** to store all static files (images, videos) independently and securely.

---

#### Step 1: Initialize an S3 Bucket

1. Log in to the **AWS Management Console** and search for the **S3** service.
2. On the main S3 screen, click the **Create bucket** button.
3. In the **General configuration** section, enter a name for your bucket (Example: `your-ecommerce-product-images`). Note that the bucket name must be globally unique across all AWS accounts.
4. Select the **AWS Region** that matches the region where you deployed your RDS and ECS to optimize internal connection speeds.

![Initialize S3 Bucket](/images/4-Workshop/4.3-Database-Storage/4.3.3-Setup-S3/step1-create-bucket.png)

#### Step 2: Configure Public Access (Security)

Following standard security principles, we will absolutely not open S3 to direct Internet access. Instead, we will completely lock down S3 and only allow CloudFront (in the next step) to read the data.

1. Scroll down to the **Block Public Access settings for this bucket** section.
2. Ensure that the **Block all public access** option is CHECKED. This prevents anyone from intentionally accessing the direct S3 image URLs.
3. Scroll to the bottom of the page, keep the remaining default settings (such as automatic encryption), and click **Create bucket**.

![Block S3 Public Access](/images/4-Workshop/4.3-Database-Storage/4.3.3-Setup-S3/step2-block-public.png)

#### Step 3: Upload Sample Product Images

To have test data for later Frontend setup steps, we need to upload a few sample cosmetics images.

1. Click on the name of the Bucket you just created in the list.
2. In the **Objects** tab, click the **Upload** button.
3. Click the **Add files** button and upload a few product images from your computer (ensure standard formats like JPG or PNG).
4. Click the **Upload** button at the bottom of the page and wait for the upload process to reach 100%.

![Upload sample images to S3](/images/4-Workshop/4.3-Database-Storage/4.3.3-Setup-S3/step3-upload-images.png)