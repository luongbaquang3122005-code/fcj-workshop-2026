---
title : "AI Chatbot Integration"
date : 2026-04-03
weight : 6
chapter : true
pre : " <b> 4.6. </b> "
---

#### Integrating a Smart Chatbot with Amazon Bedrock

A modern cosmetics e-commerce website is incomplete without a virtual assistant for product consultation and customer care. In this section, we will use **Amazon Bedrock** – a fully managed service that offers access to leading Foundation Models.

To adhere to Security Best Practices, we will absolutely not call Bedrock directly from the Frontend (React). Instead, the user interface will send the question to our **Amazon ECS Backend**. The Backend will verify access permissions and then call the Bedrock API to generate a response and return it to the customer.

#### Contents

- [Configure Bedrock Permissions](4.6.1-Bedrock-Permissions/)
- [Integrate Bedrock into the Backend](4.6.2-Backend-Integration/)
- [Test Chatbot Flow on Frontend](4.6.3-Frontend-Testing/)

---

### Why is this content important?
* **API Key Security**: Placing the AI calling logic in the Backend protects your AWS credentials from being exposed in the user's browser.
* **Serverless AI**: Amazon Bedrock is completely serverless. You do not need to host or maintain heavy Large Language Models (LLMs); you only pay for the API requests you make.