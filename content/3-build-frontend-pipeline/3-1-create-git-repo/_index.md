---
title : "Create Git repository "
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

1. Open your **Gitlab** dashboard.
    - Click the **Projects** on the left menu.
    - Click the **New project** button.
      ![GitRepoCreation](/images/temp/1/40.png?width=90pc)
    - At **Create new project** page, choose **Create blank project** option.
      ![GitRepoCreation](/images/temp/1/7.png?width=90pc)
    - At **Create blank project** page.
      - Enter ``fcj-book-store-frontend`` at **Project name**.
      - Uncheck **Initialize repository with a README**.
      - Click the **Create project** button.
        ![GitRepoCreation](/images/temp/1/41.png?width=90pc)

2. Configure SSH keys to communicate with **Gitlab**.
    - Follow the documents in **Notes** to finish this step.
{{% notice note %}}
[Generate an SSH key pair](https://docs.gitlab.com/ee/user/ssh.html#generate-an-ssh-key-pair).\
[Configure SSH to point to a different directory](https://docs.gitlab.com/ee/user/ssh.html#configure-ssh-to-point-to-a-different-directory).\
Read more about [Use SSH keys to communicate with GitLab](https://.docs.gitlab.com/ee/user/ssh.html).
{{% /notice %}}

3. Upload the source code to **fcj-book-store-frontend** Gitlab project.
    - Go to the root directory of **FCJ-Serverless-Workshop** project that you downloaded before.
    - Open **src/config.js**, change the value of **APP_API_URL** to the value of **ApiUrl** that you recorded in the [Create SAM pipeline](2-2-create-pipeline) step, in this case is ``https://zr0i1ihy24.execute-api.us-east-1.amazonaws.com/staging
    ``.
      ![GitRepoCreation](/images/temp/1/42.png?width=90pc)
    - Next, create a new filed called ``buildspec.yml`` at the root directory of **FCJ-Serverless-Workshop** project as the following code.

      ```yml
      version: 0.2

      phases:
        install:
          runtime-versions:
            nodejs: 20.9.0
          commands:
            - npm install -g yarn
        pre_build:
          commands:
            - echo Removing lock files...
            - rm -f package-lock.json
            - rm -f yarn.lock
        build:
          commands:
            - echo Build started on `date`
            - yarn install
            - yarn build

      artifacts:
        base-directory: build
        files:
          - "**/*"
        discard-paths: no
      ```

      ![GitRepoCreation](/images/temp/1/46.png?width=90pc)

    - Run the code below in your terminal at the root directory of **FCJ-Serverless-Workshop** project.

      ```bash
      rm -rf .git
      git init
      git remote add origin git@gitlab.com:fcj-ws/fcj-book-store-frontend.git
      git add .
      git commit -m "Init project"
      git push --set-upstream origin master
      ```

      ![GitRepoCreation](/images/temp/1/43.png?width=90pc)

4. Back to **fcj-book-store-frontend** Gitlab project. You could see the code has been uploaded.
    ![GitRepoCreation](/images/temp/1/44.png?width=90pc)
