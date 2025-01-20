---
title : "Create pipeline "
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---
1. At the CodeCommit console, click **Pipeline-CodePipeline** on the left menu
- Click **Getting started**
- Click **Create pipeline**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-5.png?featherlight=false&width=90pc)

2. Enter pipeline name: `fcj-book-store-frontend-pipeline`
- Select **New service role** to crate a new role
- Click **Next**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-6.png?featherlight=false&width=90pc)

3. Select **AWS CodeCommit** is source provider
- Select repository is **fcj-book-store-frontend**
- Select **main** branch
- Click **Next**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-7.png?featherlight=false&width=90pc)

4. Select **AWS CodeBuild** is build provider
- Select along with region of SAM pipeline
- Click **Create new project**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-8.png?featherlight=false&width=90pc)

5. Enter project name: `fcj-book-store-frontend`
- Select **Ubuntu** for OS

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-9.png?featherlight=false&width=90pc)

6. Select **Standard** for **Rumtime(s)** section
- Select **aws/codebuild/standard:5.0** for **Image** section

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-10.png?featherlight=false&width=90pc)

7. Can you enter `buildspec.yaml` for the name of Buildspec or not
- Click **Continue to CodePipeline**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-11.png?featherlight=false&width=90pc)

8. Select project you just created
- Click **Next**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-12.png?featherlight=false&width=90pc)

9. Select **Amazon S3** is deploy provider
- Select **fcj-book-store** bucket
- Check to **Extract file before deploy**
- Click **Next**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-13.png?featherlight=false&width=90pc)

10. Scroll down to bottom and click **Create pipeline**

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-14.png?featherlight=false&width=90pc)

11. Wait for a while for the pipeline to be processed until it succeeds

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-15.png?featherlight=false&width=90pc)

12. Open [Amazon S3 console](https://s3.console.aws.amazon.com/s3/buckets?region=ap-southeast-1)

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-16.png?featherlight=false&width=90pc)

13. Click to **fcj-book-store** bucket

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-17.png?featherlight=false&width=90pc)

14. The files and folders after the build have been deployed on the S3 bucket

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-18.png?featherlight=false&width=90pc)

15. Click **Properties** tab

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-19.png?featherlight=false&width=90pc)

16. Scroll down to bottom and click website enpoint

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-20.png?featherlight=false&width=90pc)

So we have deployed a new pipeline for the source code of the front-end. The next step we will test the web running.
