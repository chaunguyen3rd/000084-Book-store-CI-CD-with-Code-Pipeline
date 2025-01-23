---
title : "Create SAM pipeline"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2. </b> "
---

#### Preparation

In this step, we will create IAM roles for **CodePipeline** Deploy stage and **CodeBuild** 

1. Open [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Click **Pipeline** on the left menu.
    - Click **Create pipeline** button.
      ![CreatePipeline](/images/temp/1/11.png?width=90pc)
    - At **Step 1: Choose creation option**.
      - Choose **Create pipeline from template**.
      - Then, click **Next** button.
        ![CreatePipeline](/images/temp/1/12.png?width=90pc)
    - At **Step 2: Choose template** page.
      - Choose **Deployment** at **Category**.
      - Choose **Deploy to Cloudformation** at **Template**.
      - Then, click **Next** button.
        ![CreatePipeline](/images/temp/1/13.png?width=90pc)
    - At **Step 3: Choose source** page.
      - Choose **Gitlab** at **Source provider**.
      - Click **Connect to Gitlab** button
    - At **Create a connection** browser tab just opens.
      - Enter **fcj-gitlab-connection** at **Connection name**.
      - Click **Connect to Gitlab** button.
        ![CreatePipeline](/images/temp/1/15.png?width=90pc)
    - At **AWS Connector for Gitlab ...** browser tab just opens.
      - Click **Authorize AWS Connector for Gitlab** button.
        ![CreatePipeline](/images/temp/1/16.png?width=90pc)
    - At **Connect to Gitlab**  browser tab just opens.
      - Click **Connect** button.
        ![CreatePipeline](/images/temp/1/17.png?width=90pc)
    - Back to **Step 3: Choose source** page.
      - Choose **fcj-ws/fcj-book-store-backend** at **Repository name**.
      - Choose **master** at **Default branch**.
      - Click **Next** button.
        ![CreatePipeline](/images/temp/1/18.png?width=90pc)
    - At **Step 4: Configure template** page.
      - Enter **FcjBookStoreBackendPipeline** at **CodePipelineName**.
      - Enter **fcj-book-store** at **StackName**.
      - Enter **template.yml** at **TemplatePath**.
        ![CreatePipeline](/images/temp/1/19.png?width=90pc)
      - Scroll down, enter the following blocks at **CloudFormationResourcePermissions**.

        ```json
        {
          "Version": "2012-10-17",
          "Statement": [
            {
              "Sid": "PermissionsForCloudformation",
              "Effect": "Allow",
              "Action": "*",
              "Resource": "*"
            }
          ]
        }
        ```

      - Leave as default, and click **Create pipeline from template** button.
        ![CreatePipeline](/images/temp/1/20.png?width=90pc)
    

