---
title : "Create Web ACL"
date : 2026-04-03
weight : 1
chapter : false
pre : " <b> 4.7.1. </b> "
---

#### Building the First Firewall

The first step in securing your system is to create a Web Access Control List (Web ACL). This acts as a "checkpoint" where you will later attach security rules and associate it directly with your Backend server's Application Load Balancer (ALB).

---

#### Step 1: Access and Select Resource Type (Regional)

1. Log in to the **AWS Management Console** and search for the **WAF & Shield** service.
2. In the left navigation menu, select **Web ACLs** and click the **Create web ACL** button.
3. In the **Resource type** section, select **Regional resources (Application Load Balancer)**.
4. In the Region dropdown right below it, select the exact Region where you previously created your ECS server and ALB.
5. In the **Name** section, enter a name for your firewall (Example: `ecommerce-waf-acl`).

![Initialize Regional Web ACL](/images/4-Workshop/4.7-Admin-Security/4.7.1-Create-Web-ACL/step1-create-acl.png)

#### Step 2: Associate with Application Load Balancer

1. Right below the name section, locate the **Associated AWS resources** section and click the **Add AWS resources** button.
2. A list of resources will appear. For the resource type, select **Application Load Balancer**.
3. Find and check the box next to your ALB name (Example: `ecs-nodejs-alb`). 
4. Click **Add** to save. At this point, the firewall knows exactly which ECS Backend resource it needs to protect.
5. Click **Create** to proceed to the next screen.

![Associate Web ACL with ALB](/images/4-Workshop/4.7-Admin-Security/4.7.1-Create-Web-ACL/step2-associate-alb.png)