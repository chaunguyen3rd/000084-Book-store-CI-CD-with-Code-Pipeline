---
title : "Xây dựng SAM pipeline"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2. </b> "
---
Trong bước này, chúng ta sẽ tìm hiểu cách tự động hoá việc xây dựng, đóng gói và triển khai các lệnh bằng cách tạo một đường dẫn phân phối liên tục sử dụng AWS Code Pipeline. Chúng ta sẽ sử dụng SAM Pipelines để tạo và tự động cập nhật, CI/CD pipeline nhiều giai đoạn.

#### AWS SAM Pipelines
SAM Pipelines hoạt động bằng cách tạo một tập hợp các tệp cấu hình và cơ sở hạ tầng mà bạn sử dụng để tạo và quản lý hệ thống CI / CD của mình.
SAM Pipelines có thể khởi tạo các pipeline CI/CD cho các nhà cung cấp sau:
- Jenkins
- GitLab CI/CD
- GitHub Actions
- Bitbucket Pipelines
- AWS CodePipeline

SAM Pipelines tạo các tệp cấu hình thích hợp cho nhà cung cấp CI/CD. Ví dụ: khi sử dụng GitHub Actions, SAM sẽ tổng hợp một tệp .github/workflows/pipeline.yaml. Tệp này xác định pipeline CI/CD sử dụng GitHub Actions. Trong bài này chúng ta sẽ sử dụng AWS CodePipeline. SAM tạo nhiều tệp, một trong số đó là CloudFormation template là codepipeline.yaml. Mẫu này xác định nhiều tài nguyên AWS hoạt động cùng nhau để triển khai ứng dụng không máy chủ một cách tự động.

#### Nội dung
1. [Tạo Git repository](2-1-create-git-repo)
2. [Tạo SAM pipeline](2-2-create-pipeline)

