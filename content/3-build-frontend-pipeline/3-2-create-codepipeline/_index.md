---
title : "Create pipeline "
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

#### Create the pipeline

1. Open [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Click **Pipelines** on the left menu.
    - Click **Create pipeline** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/45.png?width=90pc)

2. At **Step 1: Choose creation option** page.
    - Choose **Build custom pipeline** at **Creation options**.
    - Then click **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/20.png?width=90pc)

3. At **Step 2: Choose pipeline settings** page.
    - Enter ``fcjBookStoreFEPipeline`` at **Pipeline name**.
    - Choose **New service role** at **Service role**.
    - Enter ``AWSCodePipelineServiceRole-us-east-1-fcjBookStoreFEPipeline`` at **Role name**.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/47.png?width=90pc)
    - Scroll down and click the **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/48.png?width=90pc)

4. At **Step 3: Add source stage** page.
    - Choose **Gitlab** at **Source provider**.
    - Choose **fcjBookStoreGitlabConnection** at **Connection**.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/49.png?width=90pc)
    - Scroll down, enter ``fcj-ws/fcj-book-store-frontend`` at **Repository name**.
    - Enter ``master`` at **Default branch**.
    - Click the **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/50.png?width=90pc)

5. At **Step 4: Add build stage** page.
    - Choose **Other build providers** at **Build provider**.
    - Choose the **AWS CodeBuild**.
    - Enter ``fcjBookStoreBuildProject`` at **Project name**.
    - Click the **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/51.png?width=90pc)

6. At **Step 5: Add test stage** page.
    - Click the **Skip test stage** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/33.png?width=90pc)

7. At **Step 6: Add deploy stage** page.
    - Choose the **Amazon S3** at **Deploy provider**.
    - Choose **BuildArtifact** at **Artifact name**.
    - Enter ``fcj-book-shop-by-myself`` at **Bucket**.
    - Check the **Extract file before deploy**.
    - Leave as default and click the **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/52.png?width=90pc)

8. At **Step 7: Review** page.
    - Scroll down and click the **Create pipeline** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/53.png?width=90pc)

#### Test the pipeline

1. Open [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Click **Pipelines** on the left menu.
    - Check if the status of **fcjBookStoreFEPipeline** is **Succeeded**.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/54.png?width=90pc)

2. Open [Amazon S3 console](https://s3.console.aws.amazon.com/s3/buckets?region=us-east-1).
    - Click **General purpose buckets** on the left menu.
    - Choose **fcj-book-shop-by-myself** bucket.
      ![Preparation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/3.png?width=90pc)
    - At **fcj-book-shop-by-myself** page, scroll down and copy the **Bucket website endpoint** url.
      ![Preparation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/4.png?width=90pc)

3. Enter the copied link in a new tab in your web browser.
    ![Preparation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/5.png?width=90pc)
