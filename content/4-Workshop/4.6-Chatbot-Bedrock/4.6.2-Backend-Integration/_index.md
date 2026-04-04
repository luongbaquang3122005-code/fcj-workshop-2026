---
title : "Backend Integration"
date : 2026-04-03
weight : 2
chapter : false
pre : " <b> 4.6.2. </b> "
---

#### Implementing Chatbot Logic on the Backend

After successfully configuring access permissions in the previous step, we will begin writing the Backend source code to connect and control the artificial intelligence model on **Amazon Bedrock**. This section focuses on installing the necessary tools, initializing a secure connection using your configuration details, and building a simple API to process user messages.

---

#### Step 1: Prepare Necessary Libraries

For your Node.js application to communicate with the Bedrock service, the first step is to install the corresponding development library. This library provides standard tools and commands to easily send requests and receive responses from AI models.


#### Step 2: Initialize the Bedrock Client

Next, create or open an appropriate controller file within your Backend project. In this file, import the newly installed Bedrock library and also the `config.js` configuration file you set up in the previous step. Then, proceed to initialize a new client object, which serves as a secure "gateway." When initializing, ensure you pass the **region**, **credentials** (including **accessKeyId** and **secretAccessKey**), and **maxAttempts** values directly from your **config** object.

![Initialize the Bedrock Client using configuration info](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.2-Backend-Integration/step2-initialize-client.png)

#### Step 3: Write the Chatbot API Handler Function

Finally, write a dedicated API handler function to manage the conversation flow. This function will perform the following tasks: receive the message sent from the React Backend interface (with the flow described in the Introduction section); package this message along with other necessary parameters (select an appropriate AI model, for example, the Claude 3 Haiku model, set the maximum number of tokens) into a standard request structure that the AI model requires; use the client initialized above to send this request to Bedrock and await the response; upon receiving a successful response, the function will decode the data (typically from Buffer to JSON format) and extract the AI-generated response text; lastly, return this response text back to the React Frontend interface for display to the user.

![Chatbot API handler function receiving and replying to messages](/images/4-Workshop/4.6-Chatbot-Bedrock/4.6.2-Backend-Integration/step3-create-api.png)