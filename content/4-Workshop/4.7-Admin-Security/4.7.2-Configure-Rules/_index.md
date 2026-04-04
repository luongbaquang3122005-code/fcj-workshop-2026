---
title : "Configure Ruleset"
date : 2026-04-03
weight : 2
chapter : false
pre : " <b> 4.7.2. </b> "
---

#### Equipping the Firewall with "Weapons"

A firewall is useless without rules. In this section, we will add rule sets (Rules) to instruct WAF on how to identify and block malicious traffic targeting your Application Load Balancer.

---

#### Step 1: Add AWS Managed Rule Groups

Instead of researching the latest security vulnerabilities yourself, we will "borrow" the defense lists continuously updated by AWS security experts.

1. On the **Add rules and rule groups** screen, click the **Add rules** button and select **Add managed rule groups**.
2. Expand the **AWS managed rule groups** section.
3. Scroll down and toggle the switch (Add to web ACL) for the following two rule sets:
   - **Amazon IP reputation list**: Blocks IP addresses historically associated with botnets, spam, or malware.
   - **Core rule set**: Protects against the most common web vulnerabilities (OWASP Top 10) such as SQL Injection and Cross-Site Scripting.
4. Scroll to the bottom of the page and click **Add rules** to return to the main screen.
5. On the Review screen, double-check all information and click **Create web ACL**.

![Add AWS Managed Rules](/images/4-Workshop/4.7-Admin-Security/4.7.2-Configure-Rules/step1-managed-rules.png)