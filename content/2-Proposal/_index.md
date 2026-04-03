---
title: "Project Proposal"
date: 2026-03-31
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# E-commerce Cosmetic Platform  
<div style="text-align: center;">

## AI-Integrated Skincare E-commerce Platform on AWS Cloud

</div>  

---

## 1. Executive Summary  

The E-commerce Cosmetic Platform is an online web system developed to provide skincare and beauty products to users. The platform not only facilitates online shopping but also integrates an AI-driven product recommendation feature based on facial skin analysis, highly personalizing the user experience.

The system is deployed on AWS Cloud utilizing a modern architecture, which includes a React frontend, a Node.js backend, a PostgreSQL database, alongside core services such as CloudFront, Amplify, S3, RDS, and ECS Fargate. 

Additionally, the system incorporates robust security mechanisms like AWS WAF to enhance the detection of and response to security threats.

---

## 2. Problem Statement  

### *Current Issues* Existing e-commerce websites often face the following challenges:
- Lack of product personalization tailored to individual user needs.  
- Absence of smart skin analysis or automated consultation features.  
- Difficulty in scaling the system during high-traffic surges.  
- Exposure to various security risks such as SQL Injection and DDoS attacks.  

### *Proposed Solution* This system is designed to:
- Provide a seamless and user-friendly online shopping platform.  
- Integrate facial scanning technology to offer targeted product recommendations.  
- Utilize AWS infrastructure to guarantee system scalability and high performance.  

### *Key Benefits* - Delivers a highly personalized user experience.  
- Increases overall system performance and stability.  
- Ensures seamless auto-scaling to accommodate user growth.  
- Strengthens cloud security postures and data protection.  

---

## 3. Solution Architecture  

The system utilizes a modern cloud-based architecture, establishing a clear separation between the frontend, backend, and database layers.

### *Core Workflow* 1. Users access the system via Amazon CloudFront.  
2. Incoming requests are inspected and filtered by AWS WAF.  
3. The React frontend is hosted and served via AWS Amplify.  
4. API requests route through CloudFront → Application Load Balancer (ALB) → ECS Fargate.  
5. The Node.js backend processes business logic and interacts with the RDS (PostgreSQL) database.  
6. Static files (images, assets) are stored securely in Amazon S3.  
7. Amazon CloudWatch is utilized for centralized logging and system monitoring.   


![Architecture-Diagram](/images/2-Proposal/architecture-diagram.jpg)


### *AWS Services Utilized* - *AWS Amplify*: Hosts the React frontend.  
- *Amazon CloudFront*: Content Delivery Network (CDN) to accelerate access.  
- *AWS WAF*: Web Application Firewall to protect against web exploits.  
- *Application Load Balancer (ALB)*: Distributes incoming application traffic.  
- *Amazon ECS (Fargate)*: Serverless compute engine for backend containers.  
- *Amazon RDS (PostgreSQL)*: Relational database management.  
- *Amazon S3*: Object storage for media and static files.  
- *Amazon CloudWatch*: Real-time monitoring and observability.

### *Network Design (VPC)* - Dedicated Virtual Private Cloud (VPC) for the system.  
- Public Subnets:
  - Application Load Balancer (ALB)  
  - NAT Gateway  
- Private Subnets:
  - ECS Fargate  
  - Amazon RDS  
- Internet Gateway attached for external internet access.  

---

## 4. Technical Implementation  

### *Deployment Phases* a. *Research & Orientation* - Define system requirements and use cases.  
   - Select the technology stack (React, Node.js, AWS).  

b. *Architectural Design* - Draft system architecture diagrams.  
   - Design VPC topology, subnets, and routing tables.  

c. *System Development* - Develop the user interface using React.  
   - Build RESTful APIs using Node.js.  
   - Establish and configure the PostgreSQL database connection.  

d. *AWS Deployment* - Deploy the frontend via AWS Amplify.  
   - Containerize and deploy the backend via ECS Fargate.  
   - Provision RDS, S3, and CloudFront.  

e. *Security & Monitoring Setup* - Configure AWS WAF rules.  
   - Set up CloudWatch dashboards and alarms.  
   - Enable Amazon GuardDuty for threat detection.  

---

## 5. Roadmap & Milestones  

- *Month 1*:  
  - Learn AWS fundamentals.  
  - Build core backend & frontend features.  

- *Month 2*:  
  - Design and provision AWS infrastructure.  
  - Integrate cloud services and connect components.  

- *Month 3*:  
  - Optimize system performance.  
  - Implement security layers (WAF, GuardDuty).  
  - Conduct end-to-end testing and finalize the project.  

---

## 6. Budget Estimation  

Estimated monthly costs (Assuming Free Tier + Low Usage):

- ECS: ~$35/month (1 vCPU: $0.04/hr + 2GB RAM: $0.004445/GB running 24/7)
- RDS PostgreSQL: ~$0–10/month (Instance: db.t4g.micro => $0.017/hr, Storage: 20 GB gp2 => $0.115/GB)
- S3: ~$0.1/month (6MB, 100 requests)  
- CloudFront: ~$0.5/month (10GB traffic/month → ~$0.5)  
- CloudWatch: ~$0.2/month (1GB data + minimal requests → ~$0.1/month)  
- WAF: ~$1/month (1 Web ACL + 1 rule)  
- GuardDuty: ~$1–2/month (CloudTrail: $0.8/1M events)  
- Bedrock: ~$1-3/month ($0.25/1M input tokens, $1.25/1M output tokens)

Total Estimated Cost: Approximately $38.8–$51.8 USD/month. 

---

## 7. Risk Assessment  

### *Potential Risks* - Web vulnerabilities (SQL Injection, XSS).  
- Database data leaks or unauthorized access.  
- System overload due to traffic spikes.  
- Unexpected AWS billing spikes.  

### *Mitigation Strategies* - Deploy AWS WAF to filter malicious incoming requests.  
- Utilize strict IAM Roles and Policies instead of hardcoded credentials.  
- Implement Auto Scaling for ECS tasks.  
- Configure AWS Budgets and Billing Alarms.  

### *Contingency Plans* - Enable automated RDS Backups.  
- Schedule periodic system and database snapshots.  
- Establish a clear system rollback protocol.  

---

## 8. Expected Outcomes  

### *Technical Deliverables* - Construct a comprehensive, cloud-native system architecture.  
- Successfully deploy a full-stack application on AWS.  
- Apply practical, industry-standard security protocols.  

### *Core Values* - Enhance practical skills in AWS architecture and DevOps practices.  
- Gain deep insights into real-world system deployments.  
- Lay the groundwork for a scalable, commercial-grade product.  

---