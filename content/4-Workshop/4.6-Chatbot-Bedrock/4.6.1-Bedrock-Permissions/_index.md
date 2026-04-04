---
title : "Configure Access Permissions"
date : 2026-04-03
weight : 1
chapter : false
pre : " <b> 4.6.1. </b> "
---

#### Step 1: Amazon Bedrock auto-enablement mechanism

1. Log in to the **AWS Management Console** and access the **Amazon Bedrock** service.
2. In the left navigation menu, select **Model catalog**.
3. Find and select the model you want to use (For example: **Claude 3 Haiku**).
4. Click the **Open in playground** button. If your account is new, AWS will display a prompt asking for use case details. Briefly describe your intent (For example: "Customer support chatbot for e-commerce website") and submit it.
5. Once completed (or upon making your first API call), the model will be automatically ready for your application.

![Access Model Catalog](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.1-Bedrock-Permissions/step1-model-catalog.png)

#### Step 2: Create an IAM User for Bedrock

Instead of using the Root Account, we will create a sub-account (IAM User) that has only one permission: invoking the Bedrock API. This protects your system in case the source code is exposed.

1. Search for and access the **IAM (Identity and Access Management)** service.
2. In the left menu, select **Users** and click **Create user**.
3. Enter the user name as `bedrock-api-user` and click **Next**.
4. In the Set permissions section, select **Attach policies directly**.
5. In the search box, type `AmazonBedrockFullAccess`, check the box next to this policy, click **Next**, and then click **Create user**.

![Create IAM User](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.1-Bedrock-Permissions/step2-create-user.png)

#### Step 3: Obtain Access Key and Secret Key

1. Click on the `bedrock-api-user` name you just created.
2. Switch to the **Security credentials** tab.
3. Scroll down to the **Access keys** section and click **Create access key**.
4. Select **Application running outside AWS** -> Click **Next** -> Click **Create access key**.
5. **CRITICALLY IMPORTANT:** AWS will display the `Access key ID` and `Secret access key`. Copy them immediately and store them in a secure place. You will not be able to view the `Secret access key` again after closing this window.

#### Step 4: Set up Environment Variables in the project

Now, open your Node.js Backend source code (where the `config.js` file is located to connect to AWS).

1. Create or open the `.env` file in the root directory of the Backend project.
2. Add the following variables and paste the information you just obtained from Step 3:

```env
AWS_BEDROCK_AWS_REGION="us-east-1" # Or the Region you are using
AWS_BEDROCK_ACCESS_KEY="Enter-Access-Key-Here"
AWS_BEDROCK_SECRET_ACCESS_KEY="Enter-Secret-Key-Here"