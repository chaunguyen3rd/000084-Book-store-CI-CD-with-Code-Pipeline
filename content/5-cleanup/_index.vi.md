---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---
1. Làm rỗng S3 bucket
- Mở bảng điều khiển của [AWS S3](https://s3.console.aws.amazon.com/s3/buckets?region=ap-southeast-1)
- Chọn **fcj-book-store**
- Ấn **Empty**
- Nhập **permanently delete**
- Ấn **Empty**
- Làm tương tự với bucket bắt đầu bằng **aws-sam-cli-managed-default-** và bucket **book-image-resize-store**
2. Xoá pipeline
- Mở bảng điều khiển của [AWS CodePipeline](https://ap-southeast-1.console.aws.amazon.com/codesuite/codepipeline/pipelines?region=ap-southeast-1)
- Chọn pipeline **fcj-book-store-frontend-pipeline**
- Ấn **Delete pipeline**
- Nhập **delete**
- Ấn **Delete**
- Làm tương tự với các pipeline còn lại
3. Xoá stack của CloudFormation và CodeCommit repository
- Chạy câu lệnh dưới đây:
```
aws codecommit delete-repository --repository-name fcj-book-store-backend
aws codecommit delete-repository --repository-name fcj-book-store-frontend
sam delete --stack-name fcj-book-store-backend-dev
sam delete --stack-name fcj-book-store-backend-pipeline
sam delete --stack-name aws-sam-cli-managed-dev-pipeline-resources
```