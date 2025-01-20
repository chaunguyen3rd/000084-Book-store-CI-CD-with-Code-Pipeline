---
title : "Serverless - CI/CD with AWS CodePipeline"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# Serverless - CI/CD with AWS CodePipeline

#### Overview
Continuous Integration, Continuous Delivery, Continuous Deployment (CI/CD) are software development practices for producing software in short cycles between merging source code changes and updating applications. The ultimate goal of these practices is to reduce the costs, time, and risks by delivering software in small pieces.

In workshop 7 of this series, we will know about CI/CD flow building so that every time you change and push source code on the git repository, it will automatically re-update our services and applications. There are many tools for us to build CI/CD, the most popular are Jenkins, Gitlab CI, Circle CI. In this workshop, we will use AWS's CodePipeline.

The CI/CD Architecture for back-end:
![SeverlessExample](/images/SAMPipeline.png?featherlight=false&width=50pc)

- The developer create a git repository on CodeCommit and pushes code of SAM project on it
- Every time the source code is updated, CodeBuild will automatically rebuild and prepare the CloudFormation template
- CloudFormation creates/updates serverless services

The CI/CD Architecture for website front-end:

![SeverlessExample](/images/FrontEndPipeline.png?featherlight=false&width=50pc)

- The developer creates a git repository on CodeCommit and pushes the front-end code on it
- Every time the source code is updated, CodeBuild will automatically rebuild and then package the build folder
- Finally, the build folder is pushed to the S3 bucket with the static hosting website enabled

#### CI/CD
**CI**

Continuous Integration is a software development practice in which developers regularly commit and push their local changes back to the shared repository (usually several times a day). By fetching and merging changes from other developers they mitigated the risk of complicated conflict resolution. Before each commit, developers can run unit tests locally on their source code as an additional check before integrating. A continuous integration service automatically builds and runs unit tests on the new source code changes to catch any errors immediately.

**CD**

Continuous Delivery is a software development practice that extends Continuous Integration in which source code changes are automatically prepared for deployment to a production instance. After a build, the build artifact with new changes is deployed to a staging instance where advanced (integration, acceptance, load, end-to-end, etc.) tests are run. If needed, the build artifact is automatically deployed to the production instance after manual approval.

Continuous Deployment is a software development practice that extends Continuous Delivery in which source code changes are automatically deployed to a production instance. The difference between Continuous Delivery and Continuous Deployment is the presence of manual approval. With Continuous Delivery, deployment to production occurs automatically after manual approval. With Continuous Deployment, deployment to production occurs automatically without manual approval.

#### Content

 1. [Preparation](1-preparation/)
 2. [Build SAM pipeline](2-build-sam-pipeline/)
 3. [Build pipeline for frontend](3-build-frontend-pipeline/)
 4. [Test web operation](4-test-operation/)
 5. [Cleanup](5-cleanup)