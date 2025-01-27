---
title : "Test web operation"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Preparation

1. Open [Amazon Cognito console](https://us-east-1.console.aws.amazon.com/cognito/v2/home?region=us-east-1).
    - Click the **User pools** on the left menu.
    - Choose the **fcj-user-pool** User pool name.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/57.png?width=90pc)

2. At **Overview: fcj-user-pool** page.
    - Click the **App clients** on the left menu.
    - Choose the **fcj-user-pool-client** App client name.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/58.png?width=90pc)

3. At **App client: fcj-user-pool-client** page.
    - Record the value of the **Client ID** and **Client secret**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/59.png?width=90pc)

4. Go to the root directory of the **fcj-book-store-sam-ws7** project that you downloaded before.
    - Open the **template.yml** file at the root folder and change the value of **cognitoClientID** and **cognitoClientSecret** with your recorded value in the previous step.

      ```yml
      cognitoClientID:
        Type: String
        Default: 5fvkqik6cd87mqrfa7m3qg46j0 # Your Client ID

      cognitoClientSecret:
        Type: String
        Default: smz277rcfj11eal321ffbnh59kw # Your Client secret
      ```

      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/60.png?width=90pc)

    - Open your terminal at the root directory of the **fcj-book-store-sam-ws7** project and run the following code.

      ```bash
      git add .
      git commit -m "Change the value of Client ID and Client secret"
      git push
      ```

5. Open [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Click **Pipelines** on the left menu.
    - Check if the status of **fcjBookStorePipeline** is **Succeeded**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/61.png?width=90pc)

#### Test web operation

You can download the image files here to add data to check the operation of the services

{{%attachments title="Images" pattern=".*\.(jpeg)$"/%}}

1. At the tab in your web browser from the last previous step, click **Register** button on the upper right corner of the screen.
    ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/55.png?width=90pc)

2. At **FCJ Book Store - Register** page.
    - Enter information to register an account: email, password and re-validate password.
    - Click the **Register** button.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/56.png?width=90pc)

3. Open the email you register, then find the message from `
no-reply@verificationemail.com` to get verify code.
    ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/62.png?width=90pc)

4. Back to **Verify Email** page.
    - Enter the verify code at the **Verify code**.
    - Click the **Submit** button.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/63.png?width=90pc)

5. At the **FCJ Book Store - Login** page.
    - Enter your account information: Email and Password to login.
    - Click the **Submit** button.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/64.png?width=90pc)

6. So we just registered and logged in successfully. Next, we will test the adding a new book function.
    - Click the **Create new book** tab.
    - Enter ID: `1`.
    - Enter book name: `Python Coding`.
    - Enter author: `Doan Minh Phung`.
    - Enter category: `IT`.
    - Enter price: `5.6`.
    - Enter description: `Guide to basic of Python in real projects`.
    - Click the **Choose File** and select **PythonCoding.jpeg** that downloaded.
    - Click the **Create** button.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/65.png?width=90pc)
    - Then click the **OK** button.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/66.png?width=90pc)

7. Back to the Homepage, we can see A new book has been added to the database.
    ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/67.png?width=90pc)

We have completed the workshop, already know how to create the SAM pipeline and pipeline using the console. Next workshop we learn about debugging, monitoring **AWS Lambda** with **AWS CloudWatch** and **AWS X-ray**.
