---
title : "Serverless - CI/CD với CodePipeline"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---

# Serverless - CI/CD với CodePipeline

#### Tổng quan

Continuous Integration, Continuous Delivery, Continuous Deployment (CI/CD) là các phương pháp phát triển phần mềm để sản xuất phần mềm trong các chu kỳ ngắn giữa hợp nhất thay đổi mã nguồn và cập nhật ứng dụng. Mục tiêu cuối của các phương pháp này là giảm chi phí, thời gian và rủi ro bằng cách phân phối phần mềm thành các phần nhỏ.

Trong bài số 7 của series này, chúng ta sẽ tìm hiểu về cách xây dựng luồng CI/CD để mỗi khi bạn thay đổi source của ứng dụng và đưa lên git repository, nó sẽ được tự động cập nhật lại các dịch vụ và ứng dụng của chúng ta. Có rất nhiều tool để ta xây dựng CI/CD, phổ biến nhất là Jenkins, Gitlab CI, Circle CI. Trong bài này chúng ta sẽ sử dụng CodePipeline của AWS.

Kiến trúc CI/CD cho back-end:
![SeverlessExample](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/SAMPipeline.png?featherlight=false&width=50pc)

- Nhà phát triển tạo một git repo trên Gitlab và đưa code của SAM project lên đó
- Mỗi khi source code được cập nhật, CodeBuild sẽ tự động build lại và chuẩn bị CloudFormation template
- CloudFormation tạo/cập nhật các dịch vụ không máy chủ


Kiến trúc CI/CD cho front-end của web:

![SeverlessExample](https://chaunguyen3rd.github.io/000084-Book-store-CI-CD-with-Code-Pipeline/images/FrontEndPipeline.png?featherlight=false&width=50pc)

- Nhà phát triển tạo một git repo trên Gitlab và đưa front-end code lên đó
- Mỗi khi source code được cập nhật, CodeBuild sẽ tự động build lại sau đó đóng gói thư mục build
- Cuối cùng thư mục build được đẩy vào S3 bucket với static hosting website đã được kích hoạt

#### CI/CD

**CI**

Continuous Integration là một phương pháp phát triển phần mềm mà trong đó các nhà phát triển thường xuyên commit và push các thay đổi lên các shared repository. Bằng cách nạp và hợp nhất các thay đổi từ nhiều nhà phát triển khác nhau, vì vậy giảm thiểu nguy cơ xung đột. Trước mỗi lần commit, các nhà phát triển có thể chạy các unit test trên mã nguồn như một kiểm tra bổ sung trước khi tích hợp. Một continuous integration tự động build và chạy các bài kiểm tra trên các mã nguồn thay đổi để phát hiện bất kỳ lỗi nào ngay lập tức.

**CD**

Continuous Delivery là một phương pháp phát triển phần mềm mở rộng Continuous Integration trong đó mã nguồn được tự động chuẩn bị để triển khai cho một production instance. Sau khi build, build artifact với các thay đổi mới được triển khai cho một staging instance nơi chạy các bài kiểm tra nâng cao (integration, acceptance, load, end-to-end, etc.). Nếu cần, build artifact tự động được triển khai tới production instance  sau khi được duyệt thủ công

Continuous Delivery là một phương pháp phát triển phần mềm mở rộng Continuous Delivery trong đó các thay đổi mã nguồn được triển khai tự động đến một production instance. Sự khác biệt giữa Continuous Delivery và Continuous Deployment ở bước kiểm duyệt thủ công. Với Continuous Delivery, việc triển khai diễn ra tự động sau khi kiểm duyệt thủ công. Với Continuous Delivery, việc triển khai diễn ra tự động mà không cần phê duyệt thủ công.

#### Nội dung

 1. [Chuẩn bị](1-preparation/)
 2. [Xây dựng SAM pipeline](2-build-sam-pipeline/)
 3. [Xây dụng pipeline cho frontend](3-build-frontend-pipeline/)
 4. [Kiểm tra hoạt động](4-test-operation/)
 5. [Dọn dẹp tài nguyên](5-cleanup)
