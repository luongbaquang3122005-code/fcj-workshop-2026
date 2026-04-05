---
title : "Distribution via CloudFront"
date : 2026-04-03
weight : 4
chapter : false
pre : " <b> 4.3.4. </b> "
---

#### Securing S3 with Origin Access Control (OAC)

Since we blocked public access to S3 in the previous step, no one can view the product images. Now, we will create a CloudFront network in front of S3 and grant a special "pass" (OAC) so that CloudFront has permission to fetch images from S3 and deliver them to users.

---

#### Step 1: Create a CloudFront Distribution

1. Go to the **AWS Management Console** and search for the **CloudFront** service.
2. Click the **Create a CloudFront distribution** button.
3. In the **Origin domain** section, click the input box and select the S3 Bucket you created in step 4.3.3 from the dropdown list.
4. Once you select S3, the system will display an access warning. Ignore this warning and proceed to the next step.

![Select S3 as Origin for CloudFront](/images/4-Workshop/4.3-Database-Storage/4.3.4-CloudFront-S3/step1-select-origin.png)

#### Step 2: Configure Origin Access Control (OAC)

This is the most important step to ensure strict security.

1. In the **Settings** section, select **Use recommended origin settings**.
2. Scroll to the bottom and click **Create distribution**.

![Configure Origin Access Control](/images/4-Workshop/4.3-Database-Storage/4.3.4-CloudFront-S3/step2-setup-oac.png)

#### Step 3: Update S3 Policy (Bucket Policy)

CloudFront has been created, but S3 still does not recognize CloudFront as an authorized entity.

1. Right after clicking Create in the previous step, AWS will display a blue banner at the top of the screen prompting you to update the S3 policy.
2. Click the **Copy policy** button available in that notification bar.
3. Click the link to your S3 bucket (also shown in the notification bar) to open the S3 management page in a new tab.
4. In the S3 page, go to the **Permissions** tab and scroll down to the **Bucket policy** section.
5. Click **Edit**, paste the policy you just copied into the box, and click **Save changes**.

![Update S3 Bucket Policy](/images/4-Workshop/4.3-Database-Storage/4.3.4-CloudFront-S3/step3-bucket-policy.png)

#### Step 4: Verify Image Delivery

1. Go back to the CloudFront tab and wait about 3–5 minutes until the Distribution status changes from "Deploying" to completed.
2. Copy the domain name provided by CloudFront under **Distribution domain name** (e.g., `d12345abcdef.cloudfront.net`).
3. Open a new browser tab, paste the domain, and append the name of an image you previously uploaded to S3 (e.g., `d12345abcdef.cloudfront.net/son-moi.png`).
4. If the image displays successfully, congratulations! Your storage architecture now meets enterprise standards.

![Verify image via CloudFront](/images/4-Workshop/4.3-Database-Storage/4.3.4-CloudFront-S3/step4-verify-image.png)