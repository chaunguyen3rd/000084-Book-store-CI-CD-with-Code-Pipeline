---
title : "Tạo Git repository "
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---
1. Cập nhật lại code của front-end
- Mở tệp **config.js** trong thư mục source code của front-end mà bạn đã tải - fcj-serverless-frontend. Sau đó thay giá trị của **APP_API_URL** bằng URL mà bạn đã ghi lại từ bước trước
- Bỏ comment dòng số 4 và thay giá trị bằng email mà bạn sẽ đăng ký tài khoản

![DeployPipeline](/images/2-build-sam-pipeline/2-2-create-pipeline-9.png?featherlight=false&width=90pc)
![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-1.png?featherlight=false&width=90pc)

- Mở tệp **Login.js** trong thư mục **fcj-serverless-frontend/src/component/Authen/**, bỏ comment dòng số 39 và 41

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-2.png?featherlight=false&width=90pc)

2. Tạo một tệp mới tên là **buildspect.yaml** trong thư mục **fcj-serverless-frontend/**. Sao chép script dưới vào tệp đó
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

3. Chạy câu lệnh dưới đây để tạo CodeCommit repository cho code của front-end
```
aws codecommit create-repository --repository-name fcj-book-store-frontend
```
Bạn sẽ thấy đầu ra tương tự như sau
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

- Mở bảng điều khiển của [CodeCommit](https://ap-southeast-1.console.aws.amazon.com/codesuite/codecommit/repositories?region=ap-southeast-1) để kiểm tra repository

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-3.png?featherlight=false&width=90pc)

4. Chạy các câu lệnh dưới đây tại tư mục gốc của front-end project để khởi tạo một Git repository cục bộ, thêm code và đẩy lên CodeCommit repository.
```
git init -b main
git add .
git commit -m "Initial commit"
```

5. Thêm URL của CodeCommit repository mà bạn đã tạo làm remote trên git project cục bộ
```
git remote add origin codecommit://fcj-book-store-frontend
```
{{% notice tip %}}
Nếu origin đã tồn tại hoặc url bị sai, có thể xoá bằng cách chạy: `git remote rm origin`
{{% /notice %}}

6. Đẩy code lên CodeCommit repository bằng câu lệnh dưới đây:
```
git push -u origin main
```

7. Quay lại với bảng điều khiển của CodeComit
- Ấn vào repository **fcj-book-store-frontend**, bạn sẽ thấy code đã được đẩy lên

![FrontEndPipeline](/images/3-build-frontend-pipeline/3-build-frontend-pipeline-4.png?featherlight=false&width=90pc)