---
title : "Tạo kho Git"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1. </b> "
---

1. Mở bảng điều khiển **Gitlab** của bạn.
    - Nhấp vào **Projects** trên menu bên trái.
    - Chọn tùy chọn **Create a project**.
      ![GitRepoCreation](/images/temp/1/6.png?width=90pc)
    - Tại trang **Create new project**, chọn tùy chọn **Create blank project**.
      ![GitRepoCreation](/images/temp/1/7.png?width=90pc)
    - Tại trang **Create blank project**.
      - Nhập ``fcj-book-store-backend`` tại **Project name**.
      - Bỏ chọn **Initialize repository with a README**.
      - Nhấp vào nút **Create project**.
        ![GitRepoCreation](/images/temp/1/8.png?width=90pc)

2. Cấu hình khóa SSH để giao tiếp với **Gitlab**.
    - Làm theo tài liệu trong **Notes** để hoàn thành bước này.
{{% notice note %}}
[Tạo cặp khóa SSH](https://docs.gitlab.com/ee/user/ssh.html#generate-an-ssh-key-pair).\
[Cấu hình SSH để trỏ đến thư mục khác](https://docs.gitlab.com/ee/user/ssh.html#configure-ssh-to-point-to-a-different-directory).\
Đọc thêm về [Sử dụng khóa SSH để giao tiếp với GitLab](https://.docs.gitlab.com/ee/user/ssh.html).
{{% /notice %}}

3. Tải mã nguồn lên dự án **fcj-book-store-backend** trên Gitlab.
    - Mở terminal của bạn và đi đến thư mục gốc của dự án **fcj-book-store-sam-ws7** mà bạn đã tải xuống trước đó.
    - Chạy mã dưới đây.

      ```bash
      git init
      git remote add origin git@gitlab.com:fcj-ws/fcj-book-store-backend.git
      git add .
      git commit -m "Init project"
      git push --set-upstream origin master
      ```

      ![GitRepoCreation](/images/temp/1/9.png?width=90pc)

4. Quay lại dự án **fcj-book-store-backend** trên Gitlab. Bạn có thể thấy mã đã được tải lên.
    ![GitRepoCreation](/images/temp/1/10.png?width=90pc)
