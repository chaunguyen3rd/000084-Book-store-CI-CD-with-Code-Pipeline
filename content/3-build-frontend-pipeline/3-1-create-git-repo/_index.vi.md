---
title : "Tạo kho Git"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

1. Mở bảng điều khiển **Gitlab** của bạn.
    - Nhấp vào **Projects** trên menu bên trái.
    - Nhấp vào nút **New project**.
      ![GitRepoCreation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/40.png?width=90pc)
    - Tại trang **Create new project**, chọn tùy chọn **Create blank project**.
      ![GitRepoCreation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/7.png?width=90pc)
    - Tại trang **Create blank project**.
      - Nhập ``fcj-book-store-frontend`` tại **Project name**.
      - Bỏ chọn **Initialize repository with a README**.
      - Nhấp vào nút **Create project**.
        ![GitRepoCreation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/41.png?width=90pc)

2. Cấu hình khóa SSH để giao tiếp với **Gitlab**.
    - Làm theo tài liệu trong **Notes** để hoàn thành bước này.
{{% notice note %}}
[Tạo cặp khóa SSH](https://docs.gitlab.com/ee/user/ssh.html#generate-an-ssh-key-pair).\
[Cấu hình SSH để trỏ đến thư mục khác](https://docs.gitlab.com/ee/user/ssh.html#configure-ssh-to-point-to-a-different-directory).\
Đọc thêm về [Sử dụng khóa SSH để giao tiếp với GitLab](https://.docs.gitlab.com/ee/user/ssh.html).
{{% /notice %}}

3. Tải mã nguồn lên dự án **fcj-book-store-frontend** trên Gitlab.
    - Đi đến thư mục gốc của dự án **FCJ-Serverless-Workshop** mà bạn đã tải xuống trước đó.
    - Mở **src/config.js**, thay đổi giá trị của **APP_API_URL** thành giá trị của **ApiUrl** mà bạn đã ghi lại trong bước [Tạo pipeline SAM](2-2-create-pipeline), trong trường hợp này là ``https://zr0i1ihy24.execute-api.us-east-1.amazonaws.com/staging``.
      ![GitRepoCreation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/42.png?width=90pc)
    - Tiếp theo, tạo một tệp mới có tên ``buildspec.yml`` tại thư mục gốc của dự án **FCJ-Serverless-Workshop** như mã sau.

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

      ![GitRepoCreation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/46.png?width=90pc)

    - Chạy mã dưới đây trong terminal của bạn tại thư mục gốc của dự án **FCJ-Serverless-Workshop**.

      ```bash
      rm -rf .git
      git init
      git remote add origin git@gitlab.com:fcj-ws/fcj-book-store-frontend.git
      git add .
      git commit -m "Init project"
      git push --set-upstream origin master
      ```

      ![GitRepoCreation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/43.png?width=90pc)

4. Quay lại dự án **fcj-book-store-frontend** trên Gitlab. Bạn có thể thấy mã đã được tải lên.
    ![GitRepoCreation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/44.png?width=90pc)
