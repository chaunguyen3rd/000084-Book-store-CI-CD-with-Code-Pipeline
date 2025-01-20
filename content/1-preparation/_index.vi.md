---
title : "Chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
Trước khi thực hiện nội dung chính của workshop này, chúng ta chuẩn bị sam project và tải source của front-end về máy của bạn.
1. Tải source code của sam project dưới đây

{{%attachments title="SAM source" pattern=".*\.(zip)$"/%}}

2. Chạy câu lệnh dưới đây để build project
```
sam build
```

3. Thực hiện câu lệnh dưới đây để tải code **fcj-serverless-frontend** về máy của bạn
```
git clone https://github.com/AWS-First-Cloud-Journey/FCJ-Serverless-Workshop
```

4. Thực hiện câu lệnh dưới đây tại thư mục gốc của **fcj-serverless-frontend** để build project
```
yarn build
```

Chúng ta đã chuẩn bị xong source cần thiết cho các bước tiếp theo.
