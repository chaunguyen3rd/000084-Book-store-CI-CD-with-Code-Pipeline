---
title : "Create SAM pipeline"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2. </b> "
---

#### Preparation

In this step, we will create IAM roles for **CodePipeline - Deploy stage** and **CodeBuild**.
> **Warning**
> The role is configured with minimal security, suitable only for a workshop environment.

1. Create **CodePipeline - Deploy stage** role.
    - Open [AWS IAM console](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1), then click **Roles** on the left menu.
    - Click **Create role** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/12.png?width=90pc)
    - At **Step 1: Select trusted entity** page.
      - Choose **AWS service** at **Trusted entity type**.
      - Enter ``CloudFormation`` at **Service or use case** and choose **CloudFormation** at **Use case**.
      - Then click **Next** button.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/13.png?width=90pc)
    - At **Step 2: Add permissions** page.
      - Enter ``AdministratorAccess`` at **Search** box.
      - Choose **AdministratorAccess** policy.
      - Then click **Next** button.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/14.png?width=90pc)
    - At **Step 3: Name, review, and create** page.
      - Enter ``fcjCodePipelineDeployStageRole`` at **Role name**.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/15.png?width=90pc)
      - Scroll down and click **Create role** button.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/16.png?width=90pc)

2. Create **CodeBuild** role.
    - Open [AWS IAM console](https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1), then click **Roles** on the left menu.
    - Click **Create role** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/12.png?width=90pc)
    - At **Step 1: Select trusted entity** page.
      - Choose **AWS service** at **Trusted entity type**.
      - Enter ``CodeBuild`` at **Service or use case** and choose **CodeBuild** at **Use case**.
      - Then click **Next** button.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/17.png?width=90pc)
    - At **Step 2: Add permissions** page.
      - Enter ``AdministratorAccess`` at **Search** box.
      - Choose **AdministratorAccess** policy.
      - Then click **Next** button.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/14.png?width=90pc)
    - At **Step 3: Name, review, and create** page.
      - Enter ``fcjCodePipelineDeployStageRole`` at **Role name**.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/18.png?width=90pc)
      - Scroll down and click **Create role** button.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/19.png?width=90pc)

#### Create the pipeline

1. Open [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Click **Pipelines** on the left menu.
    - Click **Create pipeline** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/11.png?width=90pc)

2. At **Step 1: Choose creation option** page.
    - Choose **Build custom pipeline** at **Creation options**.
    - Then click **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/20.png?width=90pc)

3. At **Step 2: Choose pipeline settings** page.
    - Enter ``fcjBookStorePipeline`` at **Pipeline name**.
    - Choose **New service role** at **Service role**.
    - Enter ``AWSCodePipelineServiceRole-us-east-1-fcjBookStorePipeline`` at **Role name**.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/21.png?width=90pc)
    - Scroll down and click the **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/22.png?width=90pc)

4. At **Step 3: Add source stage** page.
    - Choose **Gitlab** at **Source provider**.
    - Click the **Connect to Gitlab** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/23.png?width=90pc)
    - At **Create a connection** page at new browser tab is just opened.
      - Enter ``fcjBookStoreGitlabConnection`` at **Connection name**.
      - Click the **Connect to Gitlab** button.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/24.png?width=90pc)
      - After successful login to Gitlab, click the **Connect** button.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/25.png?width=90pc)
    - Check if the **Gitlab** connection is successful.
    - Enter ``fcj-ws/fcj-book-store-backend`` at **Repository name**.
    - Enter ``master`` at **Default branch**.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/26.png?width=90pc)
    - Scroll down to the bottom and click the **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/27.png?width=90pc)

5. At **Step 4: Add build stage** page.
    - Choose **Other build providers** at **Build provider**.
    - Choose the **AWS CodeBuild**.
    - Click the **Create project** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/31.png?width=90pc)
    - At **Create build project** page at the new browser tab is just opened.
      - Enter ``fcjBookStoreBuildProject`` at **Project name**.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/28.png?width=90pc)
      - Scroll down, choose **Ubuntu** at **Operating system**.
      - Choose **Existing service role** at **Service role**.
      - Choose **fcjCodeBuildRole** at **Role ARN**.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/29.png?width=90pc)
      - Scroll down to the bottom, choose **Use a buildspec file** at **Build specifications**.
      - Click the **Continue to CodePipeline** button.
        ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/30.png?width=90pc)
    - Choose the **fcjBookStoreBuildProject** at **Project name**.
    - Leave as default and click the **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/32.png?width=90pc)

6. At **Step 5: Add test stage** page.
    - Click the **Skip test stage** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/33.png?width=90pc)

7. At **Step 6: Add deploy stage** page.
    - Choose the **AWS CloudFormation** at **Deploy provider**.
    - Choose the **BuildArtifact** at **Input artifacts**.
    - Choose the **Create or update a stack** at **Action mode**.
    - Enter ``fcj-book-store`` at **Stack name**.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/34.png?width=90pc)
    - Scroll down, choose **BuildArtifact** at **Artifact name**.
    - Enter ``packaged.yaml`` at **File name**.
    - Choose the **CAPABILITY_IAM**, **CAPABILITY_NAMED_IAM** and **CAPABILITY_AUTO_EXPAND** at **Capabilities - optional**.
    - Choose the **fcjCodePipelineDeployStageRole** at **Role name**.
    - Click the **Next** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/35.png?width=90pc)

8. At **Step 7: Review** page.
    - Scroll down and click the **Create pipeline** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/36.png?width=90pc)

#### Test the pipeline

1. Open [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Click **Pipelines** on the left menu.
    - Choose **fcjBookStorePipeline** pipeline.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/37.png?width=90pc)

2. At **fcjBookStorePipeline** page.
    - Scroll down to the bottom, click the **View details** button.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/38.png?width=90pc)

3. At **fcjBookStorePipeline - Deploy stage** page.
    - Choose the **Output** tab and record the **ApiUrl**.
      ![CreatePipeline](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/39.png?width=90pc)
