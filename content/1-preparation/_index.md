---
title : "Preparation"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
Before doing the main content of this workshop, we prepare the SAM project and download the front-end source to your machine.
1. Download theh below source code of SAM project

{{%attachments title="SAM source" pattern=".*\.(zip)$"/%}}

2. Run the following command
```
sam build
```

3. Run the following command to clone **fcj-serverless-frontend** code to your device
```
git clone https://github.com/AWS-First-Cloud-Journey/FCJ-Serverless-Workshop
```

4. Run the following command in the root folder of **fcj-serverless-frontend** to build project
```
yarn build
```

We have prepared the necessary source for the next steps.