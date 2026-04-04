---
title : "Storage & Database Setup"
date : 2026-04-03
weight : 3
chapter : true
pre : " <b> 4.3. </b> "
---

#### Storage and Database Overview

In this chapter, we will build the data foundation for the E-commerce website. A production-ready system categorizes data into two main groups:
1. **Structured Data**: Product information, orders, and users are stored in **Amazon RDS (PostgreSQL)**.
2. **Static Data (Media)**: Product images and banners are stored in **Amazon S3** and delivered at high speed via **Amazon CloudFront**.

This separation helps your system achieve maximum performance and saves bandwidth costs.

#### Contents

- [Database Setup on RDS](4.3.1-setup-rds/)
- [Config Prisma](4.3.2-config-prisma/)
- [S3 Storage Setup](4.3.3-setup-s3/)
- [Image Distribution via CloudFront](4.3.4-cloudfront-s3/)

---

### Why is this architecture important?
* **Speed Optimization (CDN)**: Instead of loading images directly from S3, CloudFront will cache copies at the Edge Locations closest to the user, helping the website load extremely fast.
* **S3 Access Security**: By using **Origin Access Control (OAC)**, we can lock down direct access to S3, forcing all requests to go through CloudFront.
* **Prisma Management**: Helps the Node.js source code communicate safely with RDS and easily synchronize the table schema.