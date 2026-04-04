---
title : "Deploy and Verify"
date : 2026-04-03
weight : 3
chapter : false
pre : " <b> 4.5.3. </b> "
---

#### Step 1: Monitor the Automated Deployment Process (CI/CD)

1. Immediately after clicking **Save and deploy** in the previous step, AWS Amplify will automatically redirect you to the progress management screen for your source code branch (e.g., the `main` branch).
2. Here, you will see a progress chart consisting of 4 sequential steps: **Provision** ➔ **Build** ➔ **Deploy** ➔ **Verify**.
3. This process will take about 3 to 5 minutes for Amplify to download your React source code, run the `npm run build` command, and distribute the static files to the global CloudFront network.

#### Step 2: Access the live website

1. When all 4 steps in the progress chart turn into green checkmarks, the deployment is successfully completed.
2. In the upper left corner of the screen, right below the branch name, you will see a public URL link provided by AWS (Usually in the format: `https://[branch-name].[id-code].amplifyapp.com`).
3. Click on this link to open your E-commerce website's Frontend interface in a new browser tab.

![Access Amplify Domain](/images/4-Workshop/4.5-Frontend-Amplify/4.5.3-Deploy-Verify/step2-domain.png)

#### Step 3: Verify the Frontend and Backend Integration

To ensure the entire end-to-end system is working, we need to test the most basic connection flow: Loading product data.

1. On the newly opened website interface, navigate to the product list page (or homepage).
2. Open the browser's **Developer Tools** (Press F12) and switch to the **Network** tab.
3. Reload the website (F5). You will see the Frontend sending a Request to the **Amazon ECS** IP/Domain that you configured in the Environment Variables in the previous section to call the API to fetch products.
4. If the website screen successfully displays product information (data pulled from the RDS database), congratulations! Your React interface is smoothly connected to your Backend system.

![Verify E-commerce Web](/images/4-Workshop/4.5-Frontend-Amplify/4.5.3-Deploy-Verify/step3-verify.png)