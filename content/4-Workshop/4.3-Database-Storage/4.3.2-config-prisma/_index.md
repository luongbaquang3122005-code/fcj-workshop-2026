---
title : "Configuring and Executing Prisma Client"
date : 2026-04-02 
weight : 2
chapter : false
pre : " <b> 4.3.2 </b> "
---

### Configuring Prisma Client

After successfully pushing the Schema to the Cloud, the next step is to initialize the **Prisma Client**. This acts as a "bridge" that allows your Node.js source code to understand and interact with the database tables intuitively.

#### 1. Initializing the Client Library
Initialization allows Prisma to scan the entire defined Schema and generate a dedicated library that corresponds perfectly to the structure of tables, such as the `Customer` table, on RDS. This enables the system to automatically suggest column names and data types while you are coding.

![prisma-generate](/images/4-Workshop/4.3-Database-Storage/prisma-generate.png)

#### 2. Checking the Directory Structure
After executing the initialization command, a special folder will be created inside `node_modules`. You can check the connection status and the actual data structure through Prisma's visual management tool to ensure everything perfectly matches AWS RDS.

![prisma-studio](/images/4-Workshop/4.3-Database-Storage/prisma-client-view.png)

---