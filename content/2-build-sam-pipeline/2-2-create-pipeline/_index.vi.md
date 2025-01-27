---
title : "Tạo pipeline cho SAM"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2. </b> "
---

#### Chuẩn bị

Trong bước này, chúng ta sẽ tạo các vai trò IAM cho **CodePipeline - Deploy stage** và **CodeBuild**.
> **Cảnh báo**
> Vai trò được cấu hình với bảo mật tối thiểu, chỉ phù hợp cho môi trường workshop.

1. Tạo vai trò **CodePipeline - Deploy stage**.
    - Mở [AWS IAM console](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1), sau đó nhấp vào **Roles** trên menu bên trái.
    - Nhấp vào nút **Create role**.
      ![CreatePipeline](/images/temp/1/12.png?width=90pc)
    - Tại trang **Step 1: Select trusted entity**.
      - Chọn **AWS service** tại **Trusted entity type**.
      - Nhập ``CloudFormation`` tại **Service or use case** và chọn **CloudFormation** tại **Use case**.
      - Sau đó nhấp vào nút **Next**.
        ![CreatePipeline](/images/temp/1/13.png?width=90pc)
    - Tại trang **Step 2: Add permissions**.
      - Nhập ``AdministratorAccess`` tại **Search** box.
      - Chọn chính sách **AdministratorAccess**.
      - Sau đó nhấp vào nút **Next**.
        ![CreatePipeline](/images/temp/1/14.png?width=90pc)
    - Tại trang **Step 3: Name, review, and create**.
      - Nhập ``fcjCodePipelineDeployStageRole`` tại **Role name**.
        ![CreatePipeline](/images/temp/1/15.png?width=90pc)
      - Cuộn xuống và nhấp vào nút **Create role**.
        ![CreatePipeline](/images/temp/1/16.png?width=90pc)

2. Tạo vai trò **CodeBuild**.
    - Mở [AWS IAM console](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1), sau đó nhấp vào **Roles** trên menu bên trái.
    - Nhấp vào nút **Create role**.
      ![CreatePipeline](/images/temp/1/12.png?width=90pc)
    - Tại trang **Step 1: Select trusted entity**.
      - Chọn **AWS service** tại **Trusted entity type**.
      - Nhập ``CodeBuild`` tại **Service or use case** và chọn **CodeBuild** tại **Use case**.
      - Sau đó nhấp vào nút **Next**.
        ![CreatePipeline](/images/temp/1/17.png?width=90pc)
    - Tại trang **Step 2: Add permissions**.
      - Nhập ``AdministratorAccess`` tại **Search** box.
      - Chọn chính sách **AdministratorAccess**.
      - Sau đó nhấp vào nút **Next**.
        ![CreatePipeline](/images/temp/1/14.png?width=90pc)
    - Tại trang **Step 3: Name, review, and create**.
      - Nhập ``fcjCodePipelineDeployStageRole`` tại **Role name**.
        ![CreatePipeline](/images/temp/1/18.png?width=90pc)
      - Cuộn xuống và nhấp vào nút **Create role**.
        ![CreatePipeline](/images/temp/1/19.png?width=90pc)

#### Tạo pipeline

1. Mở [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Nhấp vào **Pipelines** trên menu bên trái.
    - Nhấp vào nút **Create pipeline**.
      ![CreatePipeline](/images/temp/1/11.png?width=90pc)

2. Tại trang **Step 1: Choose creation option**.
    - Chọn **Build custom pipeline** tại **Creation options**.
    - Sau đó nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/20.png?width=90pc)

3. Tại trang **Step 2: Choose pipeline settings**.
    - Nhập ``fcjBookStorePipeline`` tại **Pipeline name**.
    - Chọn **New service role** tại **Service role**.
    - Nhập ``AWSCodePipelineServiceRole-us-east-1-fcjBookStorePipeline`` tại **Role name**.
      ![CreatePipeline](/images/temp/1/21.png?width=90pc)
    - Cuộn xuống và nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/22.png?width=90pc)

4. Tại trang **Step 3: Add source stage**.
    - Chọn **Gitlab** tại **Source provider**.
    - Nhấp vào nút **Connect to Gitlab**.
      ![CreatePipeline](/images/temp/1/23.png?width=90pc)
    - Tại trang **Create a connection** ở tab trình duyệt mới vừa mở.
      - Nhập ``fcjBookStoreGitlabConnection`` tại **Connection name**.
      - Nhấp vào nút **Connect to Gitlab**.
        ![CreatePipeline](/images/temp/1/24.png?width=90pc)
      - Sau khi đăng nhập thành công vào Gitlab, nhấp vào nút **Connect**.
        ![CreatePipeline](/images/temp/1/25.png?width=90pc)
    - Kiểm tra xem kết nối **Gitlab** có thành công không.
    - Nhập ``fcj-ws/fcj-book-store-backend`` tại **Repository name**.
    - Nhập ``master`` tại **Default branch**.
      ![CreatePipeline](/images/temp/1/26.png?width=90pc)
    - Cuộn xuống dưới cùng và nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/27.png?width=90pc)

5. Tại trang **Step 4: Add build stage**.
    - Chọn **Other build providers** tại **Build provider**.
    - Chọn **AWS CodeBuild**.
    - Nhấp vào nút **Create project**.
      ![CreatePipeline](/images/temp/1/31.png?width=90pc)
    - Tại trang **Create build project** ở tab trình duyệt mới vừa mở.
      - Nhập ``fcjBookStoreBuildProject`` tại **Project name**.
        ![CreatePipeline](/images/temp/1/28.png?width=90pc)
      - Cuộn xuống, chọn **Ubuntu** tại **Operating system**.
      - Chọn **Existing service role** tại **Service role**.
      - Chọn **fcjCodeBuildRole** tại **Role ARN**.
        ![CreatePipeline](/images/temp/1/29.png?width=90pc)
      - Cuộn xuống dưới cùng, chọn **Use a buildspec file** tại **Build specifications**.
      - Nhấp vào nút **Continue to CodePipeline**.
        ![CreatePipeline](/images/temp/1/30.png?width=90pc)
    - Chọn **fcjBookStoreBuildProject** tại **Project name**.
    - Để mặc định và nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/32.png?width=90pc)

6. Tại trang **Step 5: Add test stage**.
    - Nhấp vào nút **Skip test stage**.
      ![CreatePipeline](/images/temp/1/33.png?width=90pc)

7. Tại trang **Step 6: Add deploy stage**.
    - Chọn **AWS CloudFormation** tại **Deploy provider**.
    - Chọn **BuildArtifact** tại **Input artifacts**.
    - Chọn **Create or update a stack** tại **Action mode**.
    - Nhập ``fcj-book-store`` tại **Stack name**.
      ![CreatePipeline](/images/temp/1/34.png?width=90pc)
    - Cuộn xuống, chọn **BuildArtifact** tại **Artifact name**.
    - Nhập ``packaged.yaml`` tại **File name**.
    - Chọn **CAPABILITY_IAM**, **CAPABILITY_NAMED_IAM** và **CAPABILITY_AUTO_EXPAND** tại **Capabilities - optional**.
    - Chọn **fcjCodePipelineDeployStageRole** tại **Role name**.
    - Nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/35.png?width=90pc)

8. Tại trang **Step 7: Review**.
    - Cuộn xuống và nhấp vào nút **Create pipeline**.
      ![CreatePipeline](/images/temp/1/36.png?width=90pc)

#### Kiểm tra pipeline

1. Mở [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Nhấp vào **Pipelines** trên menu bên trái.
    - Chọn pipeline **fcjBookStorePipeline**.
      ![CreatePipeline](/images/temp/1/37.png?width=90pc)

2. Tại trang **fcjBookStorePipeline**.
    - Cuộn xuống dưới cùng, nhấp vào nút **View details**.
      ![CreatePipeline](/images/temp/1/38.png?width=90pc)

3. Tại trang **fcjBookStorePipeline - Deploy stage**.
    - Chọn tab **Output** và ghi lại **ApiUrl**.
      ![CreatePipeline](/images/temp/1/39.png?width=90pc)
