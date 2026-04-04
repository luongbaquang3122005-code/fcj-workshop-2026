---
title : "Đóng gói với Docker"
date : 2026-04-03
weight : 1
chapter : false
pre : " <b> 4.4.1. </b> "
---

#### Mục đích của việc đóng gói (Docker Packaging)

Phân hệ Backend của chúng ta khá đặc biệt vì nó chạy song song hai môi trường: **Node.js** (để quản lý API và kết nối Prisma) và **Python** (để chạy 4 pipeline AI phân tích da mặt bằng TensorFlow và OpenCV). 

Để đảm bảo mã nguồn chạy ổn định trên Cloud mà không gặp lỗi xung đột thư viện, chúng ta sẽ đóng gói toàn bộ vào một **Docker Image** duy nhất.

#### Tạo file Dockerfile

Tại thư mục gốc của mã nguồn Backend, hãy tạo một file có tên là `Dockerfile` (không có phần đuôi mở rộng) và dán nội dung dưới đây vào. 

Đoạn mã này sẽ hướng dẫn Docker cài đặt một hệ điều hành Linux thu nhỏ, cài đặt Node.js 18, Python 3, và toàn bộ các thư viện AI nặng với phiên bản được chốt cứng để tránh lỗi.

```dockerfile
# 1. Base image Node 18 Slim
FROM node:18-slim

# 2. Cài OpenSSL, Python3, Pip, thư viện OpenCV VÀ tạo bí danh python -> python3
RUN apt-get update -y && apt-get install -y \
  openssl \
  python3 \
  python3-pip \
  libgl1-mesa-glx \
  libglib2.0-0 \
  python-is-python3 \
  && rm -rf /var/lib/apt/lists/*

# 3. Chuyển thư mục làm việc
WORKDIR /app

# 4. Dùng pip3 cài thư viện AI (Chốt cứng phiên bản)
RUN pip3 install --no-cache-dir \
  tensorflow==2.15.0 \
  mediapipe==0.10.14 \
  opencv-python==4.9.0.80 \
  opencv-contrib-python==4.9.0.80 \
  jax==0.4.23 \
  jaxlib==0.4.23 \
  numpy==1.26.4 \
  --break-system-packages

# 5. Cài đặt thư viện NodeJS
COPY package*.json ./
RUN npm install

# 6. Build Prisma
COPY prisma ./prisma/
RUN npx prisma generate

# 7. Copy toàn bộ source code
COPY . .

# 8. Mở cổng và chạy server
EXPOSE 3500
CMD ["npm", "run", "start:prod"]