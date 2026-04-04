---
title : "Test Chatbot Flow"
date : 2026-04-03
weight : 3
chapter : false
pre : " <b> 4.6.3. </b> "
---

#### Finalize and Test the Chatbot System

With the Backend ready to receive and process messages using Amazon Bedrock, our final step is to return to the live web interface on AWS Amplify to verify the entire operational flow from the end-user's perspective.

This testing phase is to confirm our security principle: The web interface communicates only with the internal Backend, completely hiding AWS connection credentials from the outside world.

---

#### Step 1: Access the Chatbot UI

1. Open your web browser and navigate to the public URL of your React application (deployed on AWS Amplify in Chapter 4.5).
2. Navigate to the page or widget window containing the project's customer consultation Chatbot feature.
3. Ensure the interface loads successfully and the message input field is ready to use.

![Chatbot feature UI on the website](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.3-Frontend-Testing/step1-chatbot-ui.png)

#### Step 2: Enable Network Monitoring Tools

To observe how the system exchanges data behind the scenes, we will use the browser's developer tools.

1. Press **F12** (or right-click and select Inspect) to open the Developer Tools window.
2. Switch to the **Network** tab.
3. Ensure the filter is set to display all Fetch/XHR traffic so we can monitor the API packet that is about to be sent.

![Open the Network tab in Developer Tools](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.3-Frontend-Testing/step2-open-network.png)

#### Step 3: Send Request and Verify Data Flow

1. In the chat box on the web interface, type a cosmetics consultation question (For example: "What moisturizer should I use for dry skin?") and press the send button.
2. Immediately observe the Network tab. You will see an outgoing request destined for the IP address or Domain of the **Amazon ECS Backend** server block, absolutely not a direct Amazon Bedrock address.
3. Wait a moment for the Backend to forward the request to the AI and receive the result.
4. When the web interface displays a natural and accurate response from the Chatbot, the verification is entirely successful. Your system is now securely integrated with AI and functioning perfectly on the cloud.

![API call flow and successful response from Chatbot](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.3-Frontend-Testing/step3-verify-flow.png)