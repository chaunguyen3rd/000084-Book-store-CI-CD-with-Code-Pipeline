---
title : "Cleanup"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

{{% notice note %}}
It will take a bit time to finish the cleanup
{{% /notice %}}

1. Empty S3 bucket.
    - Open [AWS S3 console](https://s3.console.aws.amazon.com/s3/buckets?region=us-east-1).
    - Select **fcj-book-shop-by-myself**.
    - Click **Empty**.
    - Enter ``permanently delete``.
    - Click **Empty**.
    - Do the same for bucket starting with **aws-sam-cli-managed-default-**, **book-image-resize-shop-by-myself** and **codepipeline-us-east-1-**.

2. Delete pipeline.
    - Open [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/pipelines?region=us-east-1).
    - Select **fcjBookStoreFEPipeline** pipeline.
    - Click **Delete pipeline**.
    - Enter ``delete``.
    - Click **Delete**.
    - Do the same for **fcjBookStorePipeline**.

3. Delete CodeBuild project.
    - Open [AWS CodeBuild console](https://us-east-1.console.aws.amazon.com/codesuite/codebuild/start?region=us-east-1).
    - Select **fcjBookStoreBuildProject** Build project.
    - Click **Actions**, then click **Delete**.
    - Enter ``delete``.
    - Click **Delete**.

4. Delete Connection between Gitlab and AWS.
    - Open [AWS CodeBuild console](https://us-east-1.console.aws.amazon.com/codesuite/codebuild/start?region=us-east-1).
    - Click **Settings** on the left menu and click **Connections** in the dropdown.
    - Select **fcjBookStoreGitlabConnection**.
    - Click **Delete**.
    - Enter ``delete``.
    - Click **Delete**.

5. Delete CloudFormation stacks.
    - Execute the below command to delete the AWS SAM application.

      ```bash
      sam delete --stack-name fcj-book-store
      sam delete --stack-name aws-sam-cli-managed-default
      ```

    - If you have issues when deleting with command. Open [AWS Cloudformation console](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/getting-started). Then, delete all stacks related to this workshop.

6. Delete **codepipeline-us-east-1-...** bucket.
    - Open [AWS S3 console](https://s3.console.aws.amazon.com/s3/buckets?region=us-east-1).
    - Select **codepipeline-us-east-1-...**.
    - Click **Delete**.
    - Enter ``codepipeline-us-east-1-...``.
    - Click **Delete bucket**.

7. Delete Git repository.
  {{% notice note %}}
  Follow this documentation: [Delete a Gitlab project](https://docs.gitlab.com/ee/user/project/working_with_projects.html#delete-a-project).
  {{% /notice %}}
