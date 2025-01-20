---
title : "Tạo pipeline "
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---
1. Tại bảng điều khiển của CodeCommit, ấn **Pipeline-CodePipeline** ở menu phía bên trái
- Ấn **Getting started**
- Ấn **Create pipeline**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-5.png?featherlight=false&width=90pc)

2. Nhập tên cho pipeline: `fcj-book-store-frontend-pipeline`
- Chọn **New service role** để tạo role mới
- Ấn **Next**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-6.png?featherlight=false&width=90pc)

3. Chọn **AWS CodeCommit** là nhà cũng cấp source
- Chọn repository là **fcj-book-store-frontend**
- Chọn nhánh **main**
- Ấn **Next**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-7.png?featherlight=false&width=90pc)

4. Chọn **AWS CodeBuild** là nhà cung cấp để xây dựng
- Chọn region cùng với region của SAM pipeline
- Ấn **Create new project**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-8.png?featherlight=false&width=90pc)

5. Nhập tên cho project: `fcj-book-store-frontend`
- Chọn **Ubuntu** cho OS

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-9.png?featherlight=false&width=90pc)

6. Chọn **Standard** cho mục **Rumtime(s)**
- Chọn **aws/codebuild/standard:5.0** cho mục **Image**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-10.png?featherlight=false&width=90pc)

7. Bạn có thể nhập `buildspec.yaml` vào mục tên của Buildspec hoặc không
- Ấn **Continue to CodePipeline**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-11.png?featherlight=false&width=90pc)

8. Chọn project bạn vừa tạo
- Ấn **Next**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-12.png?featherlight=false&width=90pc)

9. Chọn **Amazon S3** là nhà cung cấp triển khai
- Chọn bucket **fcj-book-store**
- Tích vào **Extract file before deploy**
- Ấn **Next**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-13.png?featherlight=false&width=90pc)

10. Kéo xuống cuối trang và ấn **Create pipeline**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-14.png?featherlight=false&width=90pc)

11. Chờ một lúc để pipeline được xử lý đến khi thành công

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-15.png?featherlight=false&width=90pc)

12. Mở bảng điều khiển của [Amazon S3](https://s3.console.aws.amazon.com/s3/buckets?region=ap-southeast-1)

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-16.png?featherlight=false&width=90pc)

13. Ấn vào bucket **fcj-book-store**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-17.png?featherlight=false&width=90pc)

14. Các tập và thư mục sau khi build đã được triển khi trên S3 bucket

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-18.png?featherlight=false&width=90pc)

15. Ấn sang tab **Propertíe**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-19.png?featherlight=false&width=90pc)

16. Kéo xuống cuối trang và ấn vào endpoint của trang web

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-20.png?featherlight=false&width=90pc)

Vậy là chúng ta đã triển khai xong một pipeline mới cho phần source code của front-end. Bước tiếp theo chúng ta sẽ kiểm tra web chạy.
