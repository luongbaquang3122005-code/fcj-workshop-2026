---
title : "Frontend Deployment"
date : 2026-04-03
weight : 5
chapter : true
pre : " <b> 4.5. </b> "
---

#### Deploying the React Interface to AWS Amplify

After completing the Backend system and Database, the next step is to bring the user interface (Frontend) to the internet. Our project uses React combined with the Vite build tool.

To host and deliver this web interface to users at the highest speed, we will use **AWS Amplify Hosting**. This service not only provides secure static storage but also automatically sets up a content delivery network (CloudFront) and automates the source code deployment process (CI/CD).

#### Frontend Deployment Roadmap

To successfully get your website online, follow these 3 steps:

1. **[Connect Repository](./4.5.1-Connect-Repository/)**: Authorize AWS Amplify to access your GitHub repository containing the React code.
2. **[Build & Environment Config](./4.5.2-Build-Settings/)**: Set up Vite build commands and declare environment variables so the Frontend knows how to call the Backend API (ECS).
3. **[Deploy & Verify](./4.5.3-Deploy-Verify/)**: Launch the automated build process and access the public domain provided by AWS.