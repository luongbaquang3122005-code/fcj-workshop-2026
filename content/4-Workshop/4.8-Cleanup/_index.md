---
title : "Clean up resources"
date : 2026-04-03
weight : 8
chapter : false
pre : " <b> 4.8. </b> "
---

#### Prevent Unexpected Costs (Crucially Important)

Congratulations on successfully completing the AI E-commerce system Workshop on AWS! You have manually set up a complex, enterprise-ready architecture comprising Frontend (Amplify), Backend (ECS), Database (RDS, S3), AI (Bedrock), and Security (WAF).

However, cloud computing platforms charge in real-time (Pay-as-you-go). If you do not intend to keep this website running continuously, you **must** delete the resources you created to avoid unexpected charges.

---

#### Guide to Deleting Services in Safe Order

Deleting resources should be done in the reverse order of creation to avoid dependency errors. Please execute the deletion in the following exact sequence:

1. **Delete AWS WAF:** Access WAF & Shield -> Web ACLs -> Select your ACL -> Disassociate (from the ALB) -> Click Delete.
2. **Delete CloudFront Distributions:** (Including CloudFront for S3 and CloudFront for API). Access CloudFront -> Select the Distribution -> Click **Disable** -> Wait for the status to change to Disabled (about 3-5 minutes) -> Click **Delete**.
3. **Delete ECS Backend:** Access ECS -> Clusters -> Select your Cluster -> Services Tab -> Select the Service -> Update (Set the number of Tasks to 0) -> Then click Delete Service -> Finally click **Delete Cluster**.
4. **Delete Load Balancer (ALB):** Access EC2 -> Load Balancers -> Select your ALB -> Click Actions -> **Delete**. Do not forget to delete the associated Target Groups as well.
5. **Delete Frontend Amplify:** Access AWS Amplify -> All apps -> Select your app -> Actions -> **Delete app**.
6. **Delete RDS Database:** Access RDS -> Databases -> Select your DB -> Actions -> **Delete** (Remember to uncheck "Create final snapshot" if not needed to avoid storage fees).
7. **Delete S3 Storage & ECR:**
   - Access S3 -> Select your image Bucket -> Click **Empty** (Delete all images inside first) -> Click **Delete**.
   - Do the same for your Docker image repository on **Amazon ECR**.

Once again, thank you for your effort in following and completing this entire practice course. The architecture you just built is a solid foundation for any large-scale cloud project in the real world!