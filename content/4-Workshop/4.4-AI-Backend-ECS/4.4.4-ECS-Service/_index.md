---
title : "Launch ECS Service"
date : 2026-04-03
weight : 4
chapter : false
pre : " <b> 4.4.4. </b> "
---

#### Step 1: Create a Cluster

1. On the **ECS** dashboard, select **Clusters** from the left menu.
2. Click the **Create cluster** button.
3. Enter a Cluster name (Example: `Ecommerce-AI-Cluster`).
4. In the **Infrastructure** section, ensure the **AWS Fargate (serverless)** option is checked. Click **Create** and wait about 1 minute for the cluster to be created.

![Create ECS Cluster](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.4-ECS-Service/step1-create-cluster.png)

#### Step 2: Create a Service within the Cluster

1. Click on the name of the Cluster you just created.
2. In the **Services** tab, click the **Create** button.
3. Under **Compute options**, ensure **Fargate** is selected.
4. Under **Deployment configuration**:
   * **Task definition**: Open the dropdown and select the `ecommerce-ai-task` you created in step 4.4.3.
   * **Service name**: Enter a name for this service (Example: `ai-backend-service`).

![Configure ECS Service](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.4-ECS-Service/step2-config-service.png)

#### Step 3: Configure Networking and Security Group

1. Scroll down to the **Networking** section. You can leave the VPC and Subnets as default.
2. Under **Security group**, select **Create a new security group**.
3. Name it `ai-backend-sg`.
4. In the **Inbound rules** section, configure it as follows to allow traffic to reach your API:
   * **Type**: Custom TCP
   * **Port range**: 3500
   * **Source**: Anywhere (0.0.0.0/0)

![Configure Security Group Port 3500](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.4-ECS-Service/step3-network-sg.png)

#### Step 4: Deploy and Verify

1. Scroll to the bottom of the page and click **Create**.
2. AWS will begin provisioning resources and pulling your Image from ECR to run. This process takes about 2-3 minutes.
3. When the Status column of the service turns green with the word **Active** (or Running), your AI Backend is officially online!

![Service Running Successfully](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.4-ECS-Service/step4-service-running.png)