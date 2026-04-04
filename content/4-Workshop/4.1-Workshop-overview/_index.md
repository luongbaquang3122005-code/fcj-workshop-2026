---
title : "Introduction"
date : 2026-04-02
weight : 1
chapter : false
pre : " <b> 4.1. </b> "
---

#### Introduction to System Architecture

+ Modern AI-integrated e-commerce systems require a clear separation between the interactive interface and the computational processing unit to ensure performance.
+ In this project, the system will completely decouple the **Frontend** source code (React interface) and the **AI Backend** (Python Pipeline and Node.js Controller). All components utilize AWS Serverless and Managed Services to automate operations and minimize the risk of overload during AI analysis.

#### Workshop Overview

In this workshop, you will deploy and connect the two main subsystems of the project step by step:

+ **Frontend Subsystem (User Interaction):** The React source code will be hosted and automatically deployed via **AWS Amplify**. Product images and user-uploaded portrait photos will be stored in **Amazon S3** and delivered at high speed through the **Amazon CloudFront** network. This is also where the application sends direct requests to **Amazon Bedrock** to activate the customer consultation Chatbot feature.
+ **Backend & AI Subsystem (Heavy Workload Processing):** The facial skin analysis AI source code (consisting of 4 models) along with internal APIs will be packaged into a single Docker Image. This image will be uploaded to **Amazon ECR** and run on the **Amazon ECS Fargate** platform. This approach helps the system allocate powerful computing resources independently without the need to maintain physical servers. Product data, revenue, and AI analysis results will be securely accessed and stored in **Amazon RDS** via Prisma ORM.
+ To ensure project security, an **AWS WAF** security layer will be set up at the perimeter to block abnormal traffic and protect customer data.

![AI E-commerce System Architecture Overview](/images/4.1-Workshop-overview/architecture-diagram.png)