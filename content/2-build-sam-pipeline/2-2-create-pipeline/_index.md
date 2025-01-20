---
title : "Create SAM pipeline"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2. </b> "
---
There are three distinct steps with SAM Pipelines and AWS CodePipeline.
1. Create required IAM roles and infrastructure
2. Create CloudFormation pipeline template
3. Deploy CloudFormation pipeline template

SAM Pipelines automates all of this for us

#### Create required IAM roles and infrastructure
1. Run the following command:
```
sam pipeline init --bootstrap
```

2. Answer the questions with the following list:

- Select a pipeline template to get started: AWS Quick Start Pipeline Templates (1)
- Select CI/CD system: AWS CodePipeline (5)
- Do you want to go through stage setup process now? [y/N]: y
- [1] Stage definition. Stage configuration name: dev
- [2] Account details. Select a credential source to associate with this stage: default (named profile) (2)
- Enter the region in which you want these resources to be created: Your region of choice
- Enter the pipeline IAM user ARN if you have previously … [] return/enter
- Enter the pipeline execution role ARN if you have previously … []: return/enter
- Enter the CloudFormation execution role ARN if you have previously … []: return/enter
- Please enter the artifact bucket ARN for your Lambda function. If you do not … []: return/enter
- Does your application contain any IMAGE type Lambda functions? [y/N]: N
- Press enter to confirm the values above … : return/enter
- Should we proceed with the creation? [y/N]: y

```
sam pipeline init generates a pipeline configuration file that your CI/CD system
can use to deploy serverless applications using AWS SAM.
We will guide you through the process to bootstrap resources for each stage,
then walk through the details necessary for creating the pipeline config file.

Please ensure you are in the root folder of your SAM application before you begin.

Select a pipeline template to get started:
        1 - AWS Quick Start Pipeline Templates
        2 - Custom Pipeline Template Location
Choice: 1

Cloning from https://github.com/aws/aws-sam-cli-pipeline-init-templates.git (process may take a moment)
Select CI/CD system
        1 - Jenkins
        2 - GitLab CI/CD
        3 - GitHub Actions
        4 - Bitbucket Pipelines
        5 - AWS CodePipeline
Choice: 5
You are using the 2-stage pipeline template.
 _________    _________ 
|         |  |         |
| Stage 1 |->| Stage 2 |
|_________|  |_________|

Checking for existing stages...

[!] None detected in this account.

Do you want to go through stage setup process now? If you choose no, you can still reference other bootstrapped resources. [y/N]: y

For each stage, we will ask for [1] stage definition, [2] account details, and [3]
reference application build resources in order to bootstrap these pipeline
resources.

We recommend using an individual AWS account profiles for each stage in your
pipeline. You can set these profiles up using aws configure or ~/.aws/credentials. See
[https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-set-up-credentials.html].


Stage 1 Setup

[1] Stage definition
Enter a configuration name for this stage. This will be referenced later when you use the sam pipeline init command:
Stage configuration name: dev

[2] Account details
The following AWS credential sources are available to use.
To know more about configuration AWS credentials, visit the link below:
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html                
        1 - Environment variables (not available)
        2 - default (named profile)
        3 - produser (named profile)
        q - Quit and configure AWS credentials
Select a credential source to associate with this stage: 2
Associated account 885078239936 with configuration dev.

Enter the region in which you want these resources to be created [ap-southeast-1]: ap-southeast-1
Enter the pipeline IAM user ARN if you have previously created one, or we will create one for you []: 

[3] Reference application build resources
Enter the pipeline execution role ARN if you have previously created one, or we will create one for you []: 
Enter the CloudFormation execution role ARN if you have previously created one, or we will create one for you []: 
Please enter the artifact bucket ARN for your Lambda function. If you do not have a bucket, we will create one for you []: 
Does your application contain any IMAGE type Lambda functions? [y/N]: n

[4] Summary
Below is the summary of the answers:
        1 - Account: 885078239936
        2 - Stage configuration name: dev
        3 - Region: ap-southeast-1
        4 - Pipeline user: [to be created]
        5 - Pipeline execution role: [to be created]
        6 - CloudFormation execution role: [to be created]
        7 - Artifacts bucket: [to be created]
        8 - ECR image repository: [skipped]
Press enter to confirm the values above, or select an item to edit the value: 

This will create the following required resources for the 'dev' configuration: 
        - Pipeline IAM user
        - Pipeline execution role
        - CloudFormation execution role
        - Artifact bucket
Should we proceed with the creation? [y/N]: y
        Creating the required resources...

Checking for existing stages...
```
Once this completes, you will see output which looks like the following:
```
Successfully created!
The following resources were created in your account:
        - Pipeline IAM user
        - Pipeline execution role
        - CloudFormation execution role
        - Artifact bucket
Pipeline IAM user credential:
        AWS_ACCESS_KEY_ID: AAAAAAAAAAAAIFRDVPDX
        AWS_SECRET_ACCESS_KEY: xxxxxxxxxxxxxxxxxxxxxxkMYI9RatNgVcIybUwh
```
3. Open [CloudFormation console](https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/)

![CreatePipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-1.png?featherlight=false&width=90pc)

4. Click **Stacks** on the left menu to check if the stack has been created.
- Click to the displayed stack

![CreatePipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-2.png?featherlight=false&width=90pc)

5. Click **Resources** tab, resources have been initialized

![CreatePipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-3.png?featherlight=false&width=90pc)

6. Back to the SAM pipeline creation screen
- Enter "N" to not create a second stage

![CreatePipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-4.png?featherlight=false&width=90pc)

#### Create CloudFormation pipeline template
We continue to create a CloudFormation template that defines the entire CI/CD pipeline

1. Answer the questions with the following list:

- What is the Git provider? Choice []: CodeCommit (2)
- What is the CodeCommit repository name?: fcj-book-store-backend
- What is the Git branch used for production deployments? [main]: main
- What is the template file path? [template.yaml]: template.yaml
- Select an index or enter the stage 1’s configuration name (as provided during the bootstrapping): 1
- What is the sam application stack name for stage 1? [sam-app]: fcj-book-store-backend-dev
- Select an index or enter the stage 2’s configuration name (as provided during the bootstrapping): 1
- What is the sam application stack name for stage 2? [sam-app]: fcj-book-store-backend-dev

```
What is the Git provider?
        1 - Bitbucket
        2 - CodeCommit
        3 - GitHub
        4 - GitHubEnterpriseServer
Choice []: 2
What is the CodeCommit repository name?: fcj-book-store-backend
What is the Git branch used for production deployments? [main]: main
What is the template file path? [template.yaml]: template.yaml
We use the stage configuration name to automatically retrieve the bootstrapped resources created when you ran `sam pipeline bootstrap`.

Here are the stage configuration names detected in .aws-sam/pipeline/pipelineconfig.toml:
        1 - dev
        2 - prod
Select an index or enter the stage 1's configuration name (as provided during the bootstrapping): 1
What is the sam application stack name for stage 1? [sam-app]: fcj-book-store-backend-dev
Stage 1 configured successfully, configuring stage 2.

Here are the stage configuration names detected in .aws-sam/pipeline/pipelineconfig.toml:
        1 - dev
        2 - prod
Select an index or enter the stage 2's configuration name (as provided during the bootstrapping): 1
What is the sam application stack name for stage 2? [sam-app]: fcj-book-store-backend-dev
Stage 2 configured successfully.
To deploy this template and connect to the main git branch, run this against the leading account:
`sam deploy -t codepipeline.yaml --stack-name <stack-name> --capabilities=CAPABILITY_IAM`.
SUMMARY
We will generate a pipeline config file based on the following information:
        What is the Git provider?: CodeCommit
        What is the CodeCommit repository name?: fcj-book-store-backend
        …………………
        What is the ECR repository URI for stage 2?: 
        What is the AWS region for stage 2?: ap-southeast-1
Successfully created the pipeline configuration file(s):
        - codepipeline.yaml
        - assume-role.sh
        - pipeline/buildspec_unit_test.yml
        - pipeline/buildspec_build_package.yml
        - pipeline/buildspec_integration_test.yml
        - pipeline/buildspec_feature.yml
        - pipeline/buildspec_deploy.yml
```

2. Once this completes, your project should have the structure below
```
└── fcj-book-store-sam-ws7
    ├── codepipeline.yaml       # (new) CodePipeline CloudFormation template
    ├── assume-role.sh          # (new) Helper script for CodePipeline
    ├── pipeline/               # (new) Build Specs for CodeBuild
    ├── events
    ├── fcj-book-store/         # SAM application root
    ├── README.md
    └── template.yaml           # SAM template
```

#### Deploy CloudFormation pipeline template
1. Run the following commands to upload the newly created folders and files to the CodeCommit repository
```
git add .
git commit -m "Adding SAM CI/CD Pipeline definition"
git push
```

2. Then, deplou SAM Pipeline by the following command: 
```
sam deploy -t codepipeline.yaml --stack-name fcj-book-store-backend-pipeline --capabilities=CAPABILITY_IAM
```

3. Wait for a while, back to the CloudFormation console to check
- Reload the stack list
- Select **fcj-book-store-backend** stack

![DeployPipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-5.png?featherlight=false&width=90pc)

4. Open [CodePipeline console](https://ap-southeast-1.console.aws.amazon.com/codesuite/codepipeline/start?region=ap-southeast-1)

![DeployPipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-6.png?featherlight=false&width=90pc)

5. A pipeline is being processed
 
![DeployPipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-7.png?featherlight=false&width=90pc)

6. Wait for a while to to complete pipeline processing

![DeployPipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-8.png?featherlight=false&width=90pc)

7. Back to the CloudFormation console, reload the stack list
- Select **fcj-book-store-backend-dev** stack
- Click **Outputs** tab
- Note down the API URL to use in the next step

![DeployPipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-9.png?featherlight=false&width=90pc)

So we have successfully deployed SAM Pipeline. The next step is to develop the pipeline for the front-end part of the web application.