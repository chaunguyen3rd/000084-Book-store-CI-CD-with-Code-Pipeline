---
title : "Create Git repository "
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---
1. Update source code of front-end
- Open **config.js** file in source code folder of front-end you downloaded - fcj-serverless-frontend. Next, replace value of **APP_API_URL** with URL that you recorded from the previous step
- Uncomment line 4 and replace value with an email that will register account 

![DeployPipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-9.png?featherlight=false&width=90pc)
![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-1.png?featherlight=false&width=90pc)

- Open **Login.js** file in  **fcj-serverless-frontend/src/component/Authen/** folder, uncomment lines 39 and 41

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-2.png?featherlight=false&width=90pc)

2. Create a new **buildspect.yaml** file in **fcj-serverless-frontend/** folder. Copy the following script into that file
```
version: 0.2

phases:
  install:
    runtime-versions:
      nodejs: latest

    commands:
      # install yarn
      - npm install yarn
      # install dependencies
      - yarn
      # so that build commands work
      - yarn add eslint-config-react-app

  build:
    commands:
      # run build script
      - yarn build

artifacts:
  # include all files required to run application
  # we include only the static build files
  files:
    - '**/*'
  base-directory: 'build'  
```

3. Run the following to create CodeCommit repository for front-end code
```
aws codecommit create-repository --repository-name fcj-book-store-frontend
```
You will see output similar to the following
```
{
    "repositoryMetadata": {
        "accountId": "111111111111",
        "repositoryId": "b782c34e-77dc-4627-8aea-ae8bd5ea79a9",
        "repositoryName": "fcj-book-store-frontend",
        "lastModifiedDate": "2022-09-19T14:49:51.325000+07:00",
        "creationDate": "2022-09-19T14:49:51.325000+07:00",
        "cloneUrlHttp": "https://git-codecommit.ap-southeast-1.amazonaws.com/v1/repos/fcj-book-store-frontend",
        "cloneUrlSsh": "ssh://git-codecommit.ap-southeast-1.amazonaws.com/v1/repos/fcj-book-store-frontend",
        "Arn": "arn:aws:codecommit:ap-southeast-1:111111111111:fcj-book-store-frontend"
    }
}
```

- Open [CodeCommit console](https://ap-southeast-1.console.aws.amazon.com/codesuite/codecommit/repositories?region=ap-southeast-1) to check repository

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-3.png?featherlight=false&width=90pc)

4. Run the commands below at the root of the front-end project to initialize a local Git repository, add the code to it.
```
git init -b main
git add .
git commit -m "Initial commit"
```

5. Add your CodeCommit repository URL as a remote on your local git project.
```
git remote add origin codecommit://fcj-book-store-frontend
```
{{% notice tip %}}
If origin already exists or url is wrong, can remove it by running: `git remote rm origin`
{{% /notice %}}

6. Push code to CodeCommit repository by running the following command: 
```
git push -u origin main
```

7. Back to CodeCommit console
- Click **fcj-book-store-frontend** repository, you will see the code has been uploaded

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-4.png?featherlight=false&width=90pc)
