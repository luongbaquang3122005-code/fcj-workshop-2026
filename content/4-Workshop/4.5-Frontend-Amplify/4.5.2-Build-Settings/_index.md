---
title : "Build and Environment Configuration"
date : 2026-04-03
weight : 2
chapter : false
pre : " <b> 4.5.2. </b> "
---

#### Step 1: Verify the Vite Build Configuration

1. Immediately after selecting the Repository in the previous step, AWS Amplify will auto-detect your source code and generate a Build settings file.
2. Click the **Edit** button in the Build settings panel to verify.
3. Since we are using React Vite, ensure that the build command is `npm run build` and the output directory (baseDirectory) is set to `dist` (not `build`). If correct, proceed to the next step.

![Vite Build Configuration](/images/4-Workshop/4.5-Frontend-Amplify/4.5.2-Build-Settings/step1-build-config.png)

#### Step 2: Set up Environment Variables

Your React source code needs to know the address of the running AI Backend to send photos for analysis. We will pass this information via Environment Variables.

1. Scroll down to the **Advanced settings** section and click to expand it.
2. Locate the **Environment variables** section.
3. Click the **Add variable** button to add a new variable.
4. In the **Key** column, enter the variable name your React code expects (Example: `VITE_API_URL`).
5. In the **Value** column, paste the public IP address or domain of the **Amazon ECS Fargate** cluster you successfully launched in section 4.4.4 (Note: Do not forget to add `http://` and the port `:3500` at the end).

![Environment Variables Setup](/images/4-Workshop/4.5-Frontend-Amplify/4.5.2-Build-Settings/step2-env-vars.png)

#### Step 3: Save Configuration

1. Click the **Next** button at the bottom to confirm.
2. The screen will proceed to the Review page. Double-check all information one last time and click **Save and deploy**.

![Save and Deploy](/images/4-Workshop/4.5-Frontend-Amplify/4.5.2-Build-Settings/step3-save-deploy.png)