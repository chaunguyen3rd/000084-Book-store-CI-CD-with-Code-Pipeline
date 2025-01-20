---
title : "Tạo Git repository"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1. </b> "
---
1. Chạy câu lệnh dưới đây để tạo CodeCommit repository mới
```
aws codecommit create-repository --repository-name fcj-book-store-backend
```
Bạn sẽ thấy đầu ra tương tự như sau
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

- Mở bảng điều khiển của [CodeCommit](https://ap-southeast-1.console.aws.amazon.com/codesuite/codecommit/repositories?region=ap-southeast-1) để kiểm tra repository

![CreateRepository](/images/2-build-sam-pipeline/2-1-create-git-repo-1.png?featherlight=false&width=90pc)

2. Chạy các câu lệnh dưới đây tại thư mục sam project mà bạn đã tải - **fcj-book-store-sam-ws7** để khởi tạo một Git repository cục bộ, thêm code và đẩy lên CodeCommit repository.
```
git init -b main
echo -e "\n\n.aws-sam" >> .gitignore
git add .
git commit -m "Initial commit"
```

![PushCode](/images/2-build-sam-pipeline/2-1-create-git-repo-2.png?featherlight=false&width=90pc)

3. Thêm URL của CodeCommit repository mà bạn đã tạo làm remote trên git project cục bộ
```
git remote add origin codecommit://fcj-book-store-backend
```
{{% notice tip %}}
Nếu origin đã tồn tại hoặc url bị sai, có thể xoá bằng cách chạy: `git remote rm origin`
{{% /notice %}}

4. Đẩy code lên CodeCommit repository bằng câu lệnh dưới đây:
```
git push -u origin main
```

![PushCode](/images/2-build-sam-pipeline/2-1-create-git-repo-3.png?featherlight=false&width=90pc)

5. Quay lại với bảng điều khiển của CodeCommit
- Ấn vào repository **fcj-book-store-backend**, bạn sẽ thấy code đã được đẩy lên

![PushCode](/images/2-build-sam-pipeline/2-1-create-git-repo-4.png?featherlight=false&width=90pc)
