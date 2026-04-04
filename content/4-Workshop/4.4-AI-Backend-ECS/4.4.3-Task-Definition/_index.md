---
title : "Configure Task Definition"
date : 2026-04-03
weight : 3
chapter : false
pre : " <b> 4.4.3. </b> "
---

#### Step 1: Initialize a new Task Definition

1. Log in to the **AWS Management Console** and search for the **Elastic Container Service (ECS)**.
2. On the left navigation menu, select **Task definitions**.
3. Click the **Create new task definition** button.

![Create Task Definition](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.3-Task-Definition/step1-create-task.png)

#### Step 2: Configure Environment and Resources

1. In the **Task definition family** section, name your configuration (Example: `ecommerce-ai-task`).
2. Under **Infrastructure requirements**, select **AWS Fargate** as the compute platform.
3. Scroll down to the Task size section. Since the AI system running TensorFlow is resource-intensive, select **2 vCPU** and **4 GB Memory** to ensure uninterrupted processing.

![Configure Fargate Resources](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.3-Task-Definition/step2-task-size.png)

#### Step 3: Configure Container and Port Mappings

1. Scroll down to the **Container - 1** section.
2. **Name**: Enter a name for the container (Example: `ai-backend-container`).
3. **Image URI**: Paste the URI you copied from ECR in the previous step (Example: `[Your-ID].dkr.ecr.[Region].amazonaws.com/your-ecommerce-backend:latest`).
4. Under **Port mappings**, enter **3500** in the Container port field (This is the port we exposed in the Dockerfile). Leave the Protocol as **TCP**.

![Configure Container URI and Port](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.3-Task-Definition/step3-container-port.png)

#### Step 4: Finalize Task Creation

1. Keep all other default environmental parameters.
2. Scroll to the very bottom and click **Create**. Your system blueprint is now ready to be deployed.

![Complete Task Creation](/images/4-Workshop/4.4-AI-Backend-ECS/4.4.3-Task-Definition/step4-create-success.png)