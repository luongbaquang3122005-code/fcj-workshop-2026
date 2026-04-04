---
title : "Docker Packaging"
date : 2026-04-03
weight : 1
chapter : false
pre : " <b> 4.4.1. </b> "
---

#### The Purpose of Docker Packaging

Our Backend subsystem is quite unique because it runs two environments in parallel: **Node.js** (to manage APIs and Prisma connections) and **Python** (to run the 4 facial analysis AI pipelines using TensorFlow and OpenCV).

To ensure the source code runs stably on the Cloud without library conflict errors, we will package everything into a single **Docker Image**.

#### Creating the Dockerfile

At the root directory of the Backend source code, create a file named `Dockerfile` (with no file extension) and paste the content below into it.

This code instructs Docker to install a minimal Linux operating system, install Node.js 18, Python 3, and all the heavy AI libraries with strictly pinned versions to prevent errors.

```dockerfile
# 1. Base image Node 18 Slim
FROM node:18-slim

# 2. Install OpenSSL, Python3, Pip, OpenCV libraries AND create alias python -> python3
RUN apt-get update -y && apt-get install -y \
  openssl \
  python3 \
  python3-pip \
  libgl1-mesa-glx \
  libglib2.0-0 \
  python-is-python3 \
  && rm -rf /var/lib/apt/lists/*

# 3. Set working directory
WORKDIR /app

# 4. Use pip3 to install AI libraries (Pinned versions)
RUN pip3 install --no-cache-dir \
  tensorflow==2.15.0 \
  mediapipe==0.10.14 \
  opencv-python==4.9.0.80 \
  opencv-contrib-python==4.9.0.80 \
  jax==0.4.23 \
  jaxlib==0.4.23 \
  numpy==1.26.4 \
  --break-system-packages

# 5. Install NodeJS libraries
COPY package*.json ./
RUN npm install

# 6. Build Prisma
COPY prisma ./prisma/
RUN npx prisma generate

# 7. Copy all source code
COPY . .

# 8. Expose port and run server
EXPOSE 3500
CMD ["npm", "run", "start:prod"]