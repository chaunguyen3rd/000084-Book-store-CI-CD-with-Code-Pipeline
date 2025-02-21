---
title : "Xây dựng pipeline SAM"
date :  2025-02-11
weight : 2
chapter : false
pre : " <b> 2. </b> "
---
Trong chương này, bạn sẽ học cách tự động hóa các lệnh build, package và deploy bằng cách tạo một pipeline phân phối liên tục sử dụng AWS Code Pipeline. Chúng ta sẽ sử dụng SAM Pipelines để tạo và cập nhật tự động một pipeline CI/CD đa giai đoạn.

#### AWS SAM Pipelines

SAM Pipelines hoạt động bằng cách tạo một tập hợp các tệp cấu hình và hạ tầng mà bạn sử dụng để tạo và quản lý pipeline CI/CD của mình.

Tính đến thời điểm viết bài này, SAM Pipelines có thể bootstrap các pipeline CI/CD cho các nhà cung cấp sau:

- Jenkins
- GitLab CI/CD
- GitHub Actions
- Bitbucket Pipelines
- AWS CodePipeline

SAM Pipelines tạo các tệp cấu hình phù hợp cho nhà cung cấp CI/CD mà bạn chọn. Ví dụ, khi sử dụng Gitlab CI/CD, SAM sẽ tổng hợp một tệp .gitlab-ci.yml. Tệp này định nghĩa pipeline CI/CD của bạn sử dụng Gitlab CI/CD. Trong workshop này, chúng ta sẽ sử dụng AWS CodePipeline. Như bạn sẽ thấy sớm, SAM tạo nhiều tệp, một trong số đó là một mẫu CloudFormation có tên codepipeline.yaml. Mẫu này định nghĩa nhiều tài nguyên AWS làm việc cùng nhau để tự động triển khai ứng dụng serverless của chúng ta.

#### Nội dung

1. [Tạo kho Git](2-1-create-git-repo)
2. [Tạo pipeline SAM](2-2-create-pipeline)
