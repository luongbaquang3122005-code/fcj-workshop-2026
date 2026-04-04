---
title : "Administration & Security"
date : 2026-04-03
weight : 7
chapter : true
pre : " <b> 4.7. </b> "
---

#### System Protection with AWS WAF

Although scalable cloud systems (Serverless/ECS) are powerful, without a protective shield, you could face massive bills due to Distributed Denial of Service (DDoS) attacks or AI API (Bedrock) spamming.

In this chapter, we will set up **AWS WAF (Web Application Firewall)** to analyze every traffic flow and block malicious requests right at the CloudFront Edge Network, long before they can reach your Backend servers.

#### Contents

- [Create Web ACL](4.7.1-Create-Web-ACL/)
- [Configure Ruleset](4.7.2-Configure-Rules/)
- [Verify Firewall](4.7.3-Verify-WAF/)

---

### Why is this content important?
* **Prevent Resource Exhaustion**: Stop bots from spamming product API calls or the AI Chatbot.
* **Protect against SQL vulnerabilities**: Block malicious code injection (SQL Injection) attempts targeting your RDS database.
* **Edge Security**: Attaching WAF directly to CloudFront eliminates global malicious traffic without slowing down the Backend system.