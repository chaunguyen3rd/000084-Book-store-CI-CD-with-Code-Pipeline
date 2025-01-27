---
title : "Tạo pipeline"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

#### Tạo pipeline

1. Mở [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Nhấp vào **Pipelines** trên menu bên trái.
    - Nhấp vào nút **Create pipeline**.
      ![CreatePipeline](/images/temp/1/45.png?width=90pc)

2. Tại trang **Step 1: Choose creation option**.
    - Chọn **Build custom pipeline** tại **Creation options**.
    - Sau đó nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/20.png?width=90pc)

3. Tại trang **Step 2: Choose pipeline settings**.
    - Nhập ``fcjBookStoreFEPipeline`` tại **Pipeline name**.
    - Chọn **New service role** tại **Service role**.
    - Nhập ``AWSCodePipelineServiceRole-us-east-1-fcjBookStoreFEPipeline`` tại **Role name**.
      ![CreatePipeline](/images/temp/1/47.png?width=90pc)
    - Cuộn xuống và nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/48.png?width=90pc)

4. Tại trang **Step 3: Add source stage**.
    - Chọn **Gitlab** tại **Source provider**.
    - Chọn **fcjBookStoreGitlabConnection** tại **Connection**.
      ![CreatePipeline](/images/temp/1/49.png?width=90pc)
    - Cuộn xuống, nhập ``fcj-ws/fcj-book-store-frontend`` tại **Repository name**.
    - Nhập ``master`` tại **Default branch**.
    - Nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/50.png?width=90pc)

5. Tại trang **Step 4: Add build stage**.
    - Chọn **Other build providers** tại **Build provider**.
    - Chọn **AWS CodeBuild**.
    - Nhập ``fcjBookStoreBuildProject`` tại **Project name**.
    - Nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/51.png?width=90pc)

6. Tại trang **Step 5: Add test stage**.
    - Nhấp vào nút **Skip test stage**.
      ![CreatePipeline](/images/temp/1/33.png?width=90pc)

7. Tại trang **Step 6: Add deploy stage**.
    - Chọn **Amazon S3** tại **Deploy provider**.
    - Chọn **BuildArtifact** tại **Artifact name**.
    - Nhập ``fcj-book-shop-by-myself`` tại **Bucket**.
    - Chọn **Extract file before deploy**.
    - Để mặc định và nhấp vào nút **Next**.
      ![CreatePipeline](/images/temp/1/52.png?width=90pc)

8. Tại trang **Step 7: Review**.
    - Cuộn xuống và nhấp vào nút **Create pipeline**.
      ![CreatePipeline](/images/temp/1/53.png?width=90pc)

#### Kiểm tra pipeline

1. Mở [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Nhấp vào **Pipelines** trên menu bên trái.
    - Kiểm tra xem trạng thái của **fcjBookStoreFEPipeline** có phải là **Succeeded** không.
      ![CreatePipeline](/images/temp/1/54.png?width=90pc)

2. Mở [Amazon S3 console](https://s3.console.aws.amazon.com/s3/buckets?region=us-east-1).
    - Nhấp vào **General purpose buckets** trên menu bên trái.
    - Chọn bucket **fcj-book-shop-by-myself**.
      ![Preparation](/images/temp/1/3.png?width=90pc)
    - Tại trang **fcj-book-shop-by-myself**, cuộn xuống và sao chép url **Bucket website endpoint**.
      ![Preparation](/images/temp/1/4.png?width=90pc)

3. Nhập liên kết đã sao chép vào một tab mới trong trình duyệt web của bạn.
    ![Preparation](/images/temp/1/5.png?width=90pc)
