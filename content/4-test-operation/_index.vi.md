---
title : "Kiểm tra hoạt động"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---
Bạn có thể tải tệp ảnh ở đây để thêm dữ liệu để kiểm tra hoạt động của các dịch vụ

{{%attachments title="Image" pattern=".*\.(jpeg)$"/%}}

1. Ấn nút **Register** ở góc trên bên phải màn hình

![UpdateSource](/images/4-test-operation/4-test-operation-1.png?featherlight=false&width=90pc)

2. Nhập thông tin để đăng ký tài khoản: email, mật khẩu và xác thực lại mật khẩu
- Ấn **Register**

![UpdateSource](/images/4-test-operation/4-test-operation-2.png?featherlight=false&width=90pc)

3. Mở email mà bạn đăng ký, sau đó tìm đến tin nhắn từ *no-reply@vertificationemail.com* để lấy mã xác thực tài khoản

![UpdateSource](/images/4-test-operation/4-test-operation-3.png?featherlight=false&width=90pc)

4. Nhập mã xác thực vào màn hình xác thực
- Ấn **Submit**

![AccessWeb](/images/4-test-operation/4-test-operation-4.png?featherlight=false&width=90pc)

5. Nhập thông tin tài khoản của bạn: email và mật khẩu để đăng nhập

![AccessWeb](/images/4-test-operation/4-test-operation-5.png?featherlight=false&width=90pc)

6. Như vậy web đã đăng nhập và đăng ký bình thường. Chúng ta sẽ kiểm tra chức năng thêm sách mới
- Ấn tab **Create new book**
- Nhập ID: `1`
- Nhập tên sách: `Python Coding`
- Nhập tác giả: `Doan Minh Phung`
- Nhập thể loại: `IT`
- Nhập giá: `5.6`
- Nhập mô tả: `Guide to basic of Python in real projects`
- Ấn **Choose File** và chọn tệp ảnh **PythonCoding.jpeg** mà bạn vừa tải về
- Ấn **Create**

![CreateBook](/images/4-test-operation/4-test-operation-6.png?featherlight=false&width=90pc)

6. Ấn **OK**

![CreateBook](/images/4-test-operation/4-test-operation-7.png?featherlight=false&width=90pc)

7. Một sách mới đã được thêm vào cơ sở dữ liệu

![CreateBook](/images/4-test-operation/4-test-operation-8.png?featherlight=false&width=90pc)

Chúng ta đã hoàn thành workshop, đã biết tạo SAM pipeline và pipeline bằng bảng điều khiển. Bài tiếp theo chúng ta tìm hiểu về gỡ lỗi, giám sát AWS Lambda với AWS CloudWatch và AWS X-ray