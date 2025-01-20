---
title : "Test web operation"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---
You can download the image files here to add data to check the operation of the services

{{%attachments title="Images" pattern=".*\.(jpeg)$"/%}}

1. Click **Register** button on the upper right corner of the screen

![UpdateSource](/images/4-test-operation/4-test-operation-1.png?featherlight=false&width=90pc)

2. Enter information to register an account: email, password and re-validate password
- Click **Register**

![UpdateSource](/images/4-test-operation/4-test-operation-2.png?featherlight=false&width=90pc)

3. Open the email you register, then find the message from *no-reply@vertificationemail.com* to get verify code

![UpdateSource](/images/4-test-operation/4-test-operation-3.png?featherlight=false&width=90pc)

4. Enter verify code to verify screen
- Click **Submit**

![AccessWeb](/images/4-test-operation/4-test-operation-4.png?featherlight=false&width=90pc)

5. Enter your account information: email and password to login

![AccessWeb](/images/4-test-operation/4-test-operation-5.png?featherlight=false&width=90pc)

6. So the web has logged in and registered normally. Next, we will test the function of adding a new book
- Click tab **Create new book**
- Enter ID: `1`
- Enter book name: `Python Coding`
- Enter author: `Doan Minh Phung`
- Enter category: `IT`
- Enter price: `5.6`
- Enter description: `Guide to basic of Python in real projects`
- Click **Choose File** and select **PythonCoding.jpeg** that downloaded
- Click **Create**

![CreateBook](/images/4-test-operation/4-test-operation-6.png?featherlight=false&width=90pc)

6. Click **OK**

![CreateBook](/images/4-test-operation/4-test-operation-7.png?featherlight=false&width=90pc)

7. A new book has been added to the database

![CreateBook](/images/4-test-operation/4-test-operation-8.png?featherlight=false&width=90pc)

We have completed the workshop, already know how to create the SAM pipeline and pipeline using the console. Next workshop we learn about debugging, monitoring AWS Lambda with AWS CloudWatch and AWS X-ray