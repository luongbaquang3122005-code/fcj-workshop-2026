---
title : "Connect Repository"
date : 2026-04-03
weight : 1
chapter : false
pre : " <b> 4.5.1. </b> "
---

#### Step 1: Access the AWS Amplify Service

1. Log in to the **AWS Management Console** and search for the **AWS Amplify** service.
2. On the Amplify homepage, scroll down to the **Amplify Hosting** section.
3. Click the **Get started** or **Host your web app** button depending on your displayed interface.

![Access Amplify Hosting](/images/4-Workshop/4.5-Frontend-Amplify/4.5.1-Connect-Repository/step1-navigate.png)

#### Step 2: Choose a source code provider (GitHub)

For Amplify to automatically fetch the code and deploy it, you need to grant it access to your repository.

1. On the repository selection screen, check **GitHub** (or GitLab/Bitbucket depending on where you host your React Vite source code).
2. Click the **Continue** button.
3. A GitHub authorization window will pop up. Log in to your GitHub account and click the **Authorize AWS Amplify** button to grant AWS permission to read your source code.

![Authorize GitHub connection](/images/4-Workshop/4.5-Frontend-Amplify/4.5.1-Connect-Repository/step2-github-auth.png)

#### Step 3: Select Repository and Branch

1. After successful authorization, you will be automatically redirected back to the AWS Amplify console interface.
2. Under **Recently updated repositories**, open the dropdown list and select the correct repository containing your React Frontend source code (Example: `ecommerce-react-frontend`).
3. Under **Branch**, select the branch you want to configure for automatic deployment (typically the `main` or `master` branch).
4. Ensure the "Connecting a monorepo" checkbox is NOT checked (since our project has separated the Frontend and Backend).
5. Click **Next** to proceed to the Build settings configuration step.

![Select Repository and Branch](/images/4-Workshop/4.5-Frontend-Amplify/4.5.1-Connect-Repository/step3-select-repo.png)