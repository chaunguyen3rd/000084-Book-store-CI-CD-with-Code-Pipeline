---
title : "Build SAM pipeline"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2. </b> "
---
In this chapter you are going to learn how to automate the build, package and deploy commands by creating a continous delivery pipeline using AWS Code Pipeline. We will be using SAM Pipelines to generate and a self-updating, multi-stage CI/CD pipeline.

#### AWS SAM Pipelines
SAM Pipelines works by creating a set of configuration and infrastructure files you use to create and manage your CI/CD pipeline.

As of this writing, SAM Pipelines can bootstrap CI/CD pipelines for the following providers:
- Jenkins
- GitLab CI/CD
- GitHub Actions
- Bitbucket Pipelines
- AWS CodePipeline

SAM Pipelines creates appropriate configuration files for your CI/CD provider of choice. For example, when using GitHub Actions SAM will synthesize a .github/workflows/pipeline.yaml file. This file defines your CI/CD pipeline using GitHub Actions. In this workshop we will be using AWS CodePipeline. As you will soon see, SAM creates multiple files, one of which is a CloudFormation template named codepipeline.yaml. This template defines multiple AWS resources that work together to deploy our serverless application automatically.

#### Content
1. [Create Git repository](2-1-create-git-repo)
2. [Create SAM pipeline](2-2-create-pipeline)
