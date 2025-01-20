---
title : "Create Git repository"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1. </b> "
---
1. Run the following command to create a new CodeCommit repository
```
aws codecommit create-repository --repository-name fcj-book-store-backend
```
You should see output similar to the following:
```
{
    "repositoryMetadata": {
        "accountId": "111111111111",
        "repositoryId": "b782c34e-77dc-4627-8aea-ae8bd5ea46c3",
        "repositoryName": "fcj-book-store-backend",
        "lastModifiedDate": "2022-09-19T11:49:51.325000+07:00",
        "creationDate": "2022-09-19T11:49:51.325000+07:00",
        "cloneUrlHttp": "https://git-codecommit.ap-southeast-1.amazonaws.com/v1/repos/fcj-book-store-backend",
        "cloneUrlSsh": "ssh://git-codecommit.ap-southeast-1.amazonaws.com/v1/repos/fcj-book-store-backend",
        "Arn": "arn:aws:codecommit:ap-southeast-1:111111111111:fcj-book-store-backend"
    }
}
```

- Open [AWS CodeCommit console](https://ap-southeast-1.console.aws.amazon.com/codesuite/codecommit/repositories?region=ap-southeast-1) to check repository

![CreateRepository](/images/2-build-sam-pipeline/2-1-create-git-repo-1.png?featherlight=false&width=90pc)

2. Run the below commands at the sam project folder you downloaded - **fcj-book-store-sam-ws7** to initialize a local Git repository, add code and push to CodeCommit repository.
```
git init -b main
echo -e "\n\n.aws-sam" >> .gitignore
git add .
git commit -m "Initial commit"
```

![PushCode](/images/2-build-sam-pipeline/2-1-create-git-repo-2.png?featherlight=false&width=90pc)

3. Add your CodeCommit repository URL as a remote on your local git project.
```
git remote add origin codecommit://fcj-book-store-backend
```
{{% notice tip %}}
If origin already exists or url is wrong, can remove it by running: `git remote rm origin`
{{% /notice %}}

4. Push code to CodeCommit repository by running the following command: 
```
git push -u origin main
```

![PushCode](/images/2-build-sam-pipeline/2-1-create-git-repo-3.png?featherlight=false&width=90pc)

5. Back to CodeCommit console
- Click **fcj-book-store-backend** repository, you will see the code has been uploaded

![PushCode](/images/2-build-sam-pipeline/2-1-create-git-repo-4.png?featherlight=false&width=90pc)
