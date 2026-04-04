---
title : "Optimize API"
date : 2026-04-03
weight : 5
chapter : false
pre : " <b> 4.4.5. </b> "
---

#### Using CloudFront as an API Shield (Reverse Proxy)

Instead of letting users call the IP address of the ECS cluster (or Load Balancer) directly, we will place a CloudFront distribution in front of it. This helps leverage AWS's global edge network to reduce connection latency while completely hiding the true Backend IP address from network scanning attacks.

---

#### Step 1: Initialize CloudFront Distribution for the API

1. Access the **CloudFront** service on the AWS Console and click the **Create a CloudFront distribution** button.
2. In the **Origin domain** section, paste the direct URL (DNS or IP) of the ECS Fargate cluster (or Application Load Balancer) that you obtained in step 4.4.4.
3. In the **Protocol** section, choose **HTTP only** (since we are transmitting internal data on port 3500) or adjust according to your server's SSL configuration.

![Set Origin pointing to ECS Backend](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.5-API-CloudFront/step1-api-origin.png)

#### Step 2: Disable Caching (Crucially Important)

Our API returns personalized AI analysis data and dynamic Chatbot content. If we cache this, subsequent users might receive the skin analysis results of previous users! Therefore, caching must be completely disabled.

1. Scroll down to the **Default cache behavior** section.
2. Under **Cache key and origin requests**, select **Cache policy and origin request policy**.
3. In the **Cache policy** dropdown list, find and select the policy named **CachingDisabled** (Absolutely no caching).
4. In the **Origin request policy** dropdown list, select **AllViewer** (Forward all Headers, Cookies, and Query strings directly from the user to the ECS Backend for processing).

![Configure CachingDisabled policy](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.5-API-CloudFront/step2-disable-cache.png)

#### Step 3: Deploy and Update the New Endpoint

1. Scroll down to the **Web Application Firewall (WAF)** section. Similar to before, you can select **Do not enable security protections** for now; we will enable WAF comprehensively in Section 4.7.
2. Click the **Create distribution** button at the bottom of the page and wait for the initialization process to complete.
3. Once the status changes to successful, copy this new **Distribution domain name**. This is your ultra-secure API address. Remember it to use in the `VITE_API_URL` variable when deploying the Frontend in section 4.5.2.

![Save the secure API URL from CloudFront](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.5-API-CloudFront/step3-secure-endpoint.png)