---
title : "Storage on Amazon ECR"
date : 2026-04-03
weight : 2
chapter : false
pre : " <b> 4.4.2. </b> "
---

#### Step 1: Access Amazon ECR and Create a repository

1. Log in to the **AWS Management Console** and search for the **Elastic Container Registry (ECR)** service.
2. On the main ECR screen, click the **Create repository** button to start creating a new repository.

![Access ECR](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.2-Amazon-ECR/step1-navigate.png)

#### Step 2: Configure Repository information

1. In the **Repository name** section, enter a memorable name of your choice (For example: `your-ecommerce-backend`).
2. In the **Image tag settings** section, select **Mutable**.
3. Keep the remaining default settings, scroll down to the bottom of the page, and click the **Create repository** button.

![Configure Repository](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.2-Amazon-ECR/step2-config-repo.png)

#### Step 3: Get the list of execution commands

1. After successful creation, your repository will appear in the list. Click on the name of the repository you just created.
2. In the top right corner, click the **View push commands** button.

![View Push Commands Button](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.2-Amazon-ECR/step3-view-btn.png)

#### Step 4: Execute push commands from the Terminal

1. At this point, AWS will display a Popup containing 4 execution steps corresponding to 4 commands. These commands have been automatically pre-filled by AWS with **your AWS Account ID**, **Region**, and the **Repository Name** you just set.
2. Open the Terminal (or Command Prompt) on your personal computer and navigate to the directory containing your Docker setup file.
3. One by one, copy each command from the console screen and paste it into the Terminal to run. This process includes: Logging in, Building the Image, Tagging, and Pushing to the Cloud.

#### Step 5: Verify the results on ECR

1. After the final command finishes running 100% in the Terminal, close the Popup and refresh the web page of your ECR repository.
2. You will see a new record appear with the Image tag as `latest`.
3. Pay attention and copy the **URI** column in the Repositories tab (It will be in the format `[Your-Account-ID].dkr.ecr.[Your-Region].amazonaws.com/[Your-Repo-Name]:latest`). We will use this URI snippet for the next server configuration step.

![Image Results on ECR](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.2-Amazon-ECR/step4-result-uri.png)