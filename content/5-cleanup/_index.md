---
title : "Cleanup"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---
1. Empty S3 bucket
- Open [AWS S3 console](https://s3.console.aws.amazon.com/s3/buckets?region=ap-southeast-1)
- Select **fcj-book-store**
- Click **Empty**
- Enter **permanently delete**
- Click **Empty**
- Do the same for bucket starting with **aws-sam-cli-managed-default-** and **book-image-resize-store** bucket
2. Delete pipeline
- Open [AWS CodePipeline console](https://ap-southeast-1.console.aws.amazon.com/codesuite/codepipeline/pipelines?region=ap-southeast-1)
- Select **fcj-book-store-frontend-pipeline** pipeline
- Click **Delete pipeline**
- Enter **delete**
- Click **Delete**
3. Delete CloudFormation stacks and CodeCommit repository
- Execute the below commands:
```
aws codecommit delete-repository --repository-name fcj-book-store-backend
aws codecommit delete-repository --repository-name fcj-book-store-frontend
sam delete --stack-name fcj-book-store-backend-dev
sam delete --stack-name fcj-book-store-backend-pipeline
sam delete --stack-name aws-sam-cli-managed-dev-pipeline-resources
```