---
title : "Create Git repository"
date :  2025-02-11
weight : 1
chapter : false
pre : " <b> 2.1. </b> "
---

1. Open your **Gitlab** dashboard.
    - Click the **Projects** on the left menu.
    - Choose **Create a project** option.
      ![GitRepoCreation](/images/temp/1/6.png?width=90pc)
    - At **Create new project** page, choose **Create blank project** option.
      ![GitRepoCreation](/images/temp/1/7.png?width=90pc)
    - At **Create blank project** page.
      - Enter ``fcj-book-store-backend`` at **Project name**.
      - Uncheck **Initialize repository with a README**.
      - Click the **Create project** button.
        ![GitRepoCreation](/images/temp/1/8.png?width=90pc)

2. Configure SSH keys to communicate with **Gitlab**.
    - Follow the documents in **Notes** to finish this step.
{{% notice note %}}
[Generate an SSH key pair](https://docs.gitlab.com/ee/user/ssh.html#generate-an-ssh-key-pair).\
[Configure SSH to point to a different directory](https://docs.gitlab.com/ee/user/ssh.html#configure-ssh-to-point-to-a-different-directory).\
Read more about [Use SSH keys to communicate with GitLab](https://.docs.gitlab.com/ee/user/ssh.html).
{{% /notice %}}

3. Upload the source code to **fcj-book-store-backend** Gitlab project.
    - Open your terminal and go to the root directory of **fcj-book-store-sam-ws7** project that you downloaded before.
    - Run the code below.

      ```bash
      git init
      git remote add origin git@gitlab.com:fcj-ws/fcj-book-store-backend.git
      git add .
      git commit -m "Init project"
      git push --set-upstream origin master
      ```

      ![GitRepoCreation](/images/temp/1/9.png?width=90pc)

4. Back to **fcj-book-store-backend** Gitlab project. You could see the code has been uploaded.
    ![GitRepoCreation](/images/temp/1/10.png?width=90pc)
