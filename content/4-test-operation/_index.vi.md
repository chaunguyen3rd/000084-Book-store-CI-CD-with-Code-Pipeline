---
title : "Kiểm tra hoạt động web"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Chuẩn bị

1. Mở [Amazon Cognito console](https://us-east-1.console.aws.amazon.com/cognito/v2/home?region=us-east-1).
    - Nhấp vào **User pools** trên menu bên trái.
    - Chọn tên User pool **fcj-user-pool**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/57.png?width=90pc)

2. Tại trang **Overview: fcj-user-pool**.
    - Nhấp vào **App clients** trên menu bên trái.
    - Chọn tên App client **fcj-user-pool-client**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/58.png?width=90pc)

3. Tại trang **App client: fcj-user-pool-client**.
    - Ghi lại giá trị của **Client ID** và **Client secret**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/59.png?width=90pc)

4. Đi đến thư mục gốc của dự án **fcj-book-store-sam-ws7** mà bạn đã tải xuống trước đó.
    - Mở tệp **template.yml** tại thư mục gốc và thay đổi giá trị của **cognitoClientID** và **cognitoClientSecret** bằng giá trị bạn đã ghi lại ở bước trước.

      ```yml
      cognitoClientID:
        Type: String
        Default: 5fvkqik6cd87mqrfa7m3qg46j0 # Your Client ID

      cognitoClientSecret:
        Type: String
        Default: smz277rcfj11eal321ffbnh59kw # Your Client secret
      ```

      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/60.png?width=90pc)

    - Mở terminal của bạn tại thư mục gốc của dự án **fcj-book-store-sam-ws7** và chạy mã sau.

      ```bash
      git add .
      git commit -m "Change the value of Client ID and Client secret"
      git push
      ```

5. Mở [AWS CodePipeline console](https://us-east-1.console.aws.amazon.com/codesuite/codepipeline/start?region=us-east-1).
    - Nhấp vào **Pipelines** trên menu bên trái.
    - Kiểm tra xem trạng thái của **fcjBookStorePipeline** có phải là **Succeeded** không.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/61.png?width=90pc)

#### Kiểm tra hoạt động web

Bạn có thể tải xuống các tệp hình ảnh tại đây để thêm dữ liệu kiểm tra hoạt động của các dịch vụ

{{%attachments title="Images" pattern=".*\.(jpeg)$"/%}}

1. Tại tab trong trình duyệt web của bạn từ bước trước, nhấp vào nút **Register** ở góc trên bên phải của màn hình.
    ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/55.png?width=90pc)

2. Tại trang **FCJ Book Store - Register**.
    - Nhập thông tin để đăng ký tài khoản: email, mật khẩu và xác nhận lại mật khẩu.
    - Nhấp vào nút **Register**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/56.png?width=90pc)

3. Mở email bạn đã đăng ký, sau đó tìm tin nhắn từ `no-reply@verificationemail.com` để lấy mã xác minh.
    ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/62.png?width=90pc)

4. Quay lại trang **Verify Email**.
    - Nhập mã xác minh tại **Verify code**.
    - Nhấp vào nút **Submit**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/63.png?width=90pc)

5. Tại trang **FCJ Book Store - Login**.
    - Nhập thông tin tài khoản của bạn: Email và Mật khẩu để đăng nhập.
    - Nhấp vào nút **Submit**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/64.png?width=90pc)

6. Vậy là chúng ta đã đăng ký và đăng nhập thành công. Tiếp theo, chúng ta sẽ kiểm tra chức năng thêm sách mới.
    - Nhấp vào tab **Create new book**.
    - Nhập ID: `1`.
    - Nhập tên sách: `Python Coding`.
    - Nhập tác giả: `Doan Minh Phung`.
    - Nhập thể loại: `IT`.
    - Nhập giá: `5.6`.
    - Nhập mô tả: `Hướng dẫn cơ bản về Python trong các dự án thực tế`.
    - Nhấp vào **Choose File** và chọn **PythonCoding.jpeg** đã tải xuống.
    - Nhấp vào nút **Create**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/65.png?width=90pc)
    - Sau đó nhấp vào nút **OK**.
      ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/66.png?width=90pc)

7. Quay lại trang chủ, chúng ta có thể thấy một cuốn sách mới đã được thêm vào cơ sở dữ liệu.
    ![TestWebOperation](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/temp/1/67.png?width=90pc)

Chúng ta đã hoàn thành workshop, đã biết cách tạo pipeline SAM và pipeline sử dụng console. Workshop tiếp theo chúng ta sẽ học về gỡ lỗi, giám sát **AWS Lambda** với **AWS CloudWatch** và **AWS X-ray**.
