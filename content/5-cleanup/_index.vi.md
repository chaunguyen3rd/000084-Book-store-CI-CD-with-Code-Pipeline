---
title : "Dọn dẹp"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

{{% notice note %}}
Sẽ mất một chút thời gian để hoàn thành việc dọn dẹp
{{% /notice %}}

1. Làm trống S3 bucket.
    - Mở [AWS S3 console](https://s3.console.aws.amazon.com/s3/buckets?region=us-east-1).
    - Chọn **fcj-book-shop-by-myself**.
    - Nhấp vào **Empty**.
    - Nhập ``permanently delete``.
    - Nhấp vào **Empty**.
    - Làm tương tự cho các bucket bắt đầu bằng **aws-sam-cli-managed-default-**, **book-image-resize-shop-by-myself** và **codepipeline-us-east-1-**.

2. Xóa pipeline.
    - Mở [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/pipelines?region=us-east-1).
    - Chọn pipeline **fcjBookStoreFEPipeline**.
    - Nhấp vào **Delete pipeline**.
    - Nhập ``delete``.
    - Nhấp vào **Delete**.
    - Làm tương tự cho **fcjBookStorePipeline**.

3. Xóa dự án CodeBuild.
    - Mở [AWS CodeBuild console](https://us-east-1.console.aws.amazon.com/codesuite/codebuild/start?region=us-east-1).
    - Chọn dự án Build **fcjBookStoreBuildProject**.
    - Nhấp vào **Actions**, sau đó nhấp vào **Delete**.
    - Nhập ``delete``.
    - Nhấp vào **Delete**.

4. Xóa kết nối giữa Gitlab và AWS.
    - Mở [AWS CodeBuild console](https://us-east-1.console.aws.amazon.com/codesuite/codebuild/start?region=us-east-1).
    - Nhấp vào **Settings** trên menu bên trái và nhấp vào **Connections** trong dropdown.
    - Chọn **fcjBookStoreGitlabConnection**.
    - Nhấp vào **Delete**.
    - Nhập ``delete``.
    - Nhấp vào **Delete**.

5. Xóa các stack CloudFormation.
    - Thực hiện lệnh dưới đây để xóa ứng dụng AWS SAM.

      ```bash
      sam delete --stack-name fcj-book-store
      sam delete --stack-name aws-sam-cli-managed-default
      ```

    - Nếu bạn gặp vấn đề khi xóa bằng lệnh. Mở [AWS Cloudformation console](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/getting-started). Sau đó, xóa tất cả các stack liên quan đến workshop này.

6. Xóa bucket **codepipeline-us-east-1-...**.
    - Mở [AWS S3 console](https://s3.console.aws.amazon.com/s3/buckets?region=us-east-1).
    - Chọn **codepipeline-us-east-1-...**.
    - Nhấp vào **Delete**.
    - Nhập ``codepipeline-us-east-1-...``.
    - Nhấp vào **Delete bucket**.

7. Xóa kho Git.
  {{% notice note %}}
  Làm theo tài liệu này: [Xóa dự án Gitlab](https://docs.gitlab.com/ee/user/project/working_with_projects.html#delete-a-project).
  {{% /notice %}}
