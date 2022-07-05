---
title : "Ứng dụng Web Serverless trên AWS"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---

# Ứng dụng Web Serverless trên AWS
---  

#### Tổng quan 

* Trong workshop này, bạn sẽ triển khai một ứng dụng web đơn giản cho phép người dùng yêu cầu các chuyến đi kỳ lân từ đội  Wild Rydes. Ứng dụng sẽ cung cấp cho người dùng giao diện người dùng dựa trên HTML để chỉ ra vị trí họ muốn được chọn và sẽ giao tiếp với phía backend với dịch vụ web RESTful để gửi yêu cầu và gửi một con kỳ lân gần đó. Ứng dụng cũng sẽ cung cấp các phương tiện để người dùng đăng ký dịch vụ và đăng nhập trước khi yêu cầu kỳ lân đến đón.
* Kiến trúc ứng dụng sử dụng AWS Lambda, Amazon API Gateway, Amazon S3, Amazon DynamoDB, Amazon Cognito và AWS Amplify Console. Amplify Console lưu trữ các tài nguyên web tĩnh bao gồm các files HTML, CSS, JavaScript và hình ảnh được tải trong trình duyệt của người dùng thông qua S3. JavaScript được thực thi trong trình duyệt gửi và nhận dữ liệu từ backend API được xây dựng bằng Lambda và API Gateway. Amazon Cognito cung cấp các chức năng xác thực và quản lý người dùng để bảo mật backend API. Cuối cùng, DynamoDB cung cấp một lớp bền vững, nơi dữ liệu có thể được lưu trữ bởi Lambda Function của API.
* Xem sơ đồ dưới đây để mô tả kiến ​​trúc hoàn chỉnh.
* workshop này được chia thành bốn mô-đun. Mỗi mô-đun mô tả một kịch bản về những gì chúng tôi sẽ xây dựng và hướng dẫn từng bước để giúp bạn triển khai kiến ​​trúc và kiểm tra các bước thực hiện của bạn.
![Wild Rydes architecture](/images/1.staticwebsite/1.1-architect.png?width=90pc)  

| Mô-đun | Mô tả |
| --------------------------- | ----------- |
| **1. Host Web tĩnh** | Triển khai trang web tĩnh bằng AWS Amplify Console ,tạo kho lưu trữ git (trong CodeCommit hoặc GitHub) và sau đó đẩy code trang web lên. |
| **2. Quản lý User** | Cấu hình quản lý người dùng cho trang web bằng Amazon Cognito. |
| **3. Serverless Backend** | Tạo một hàm AWS Lambda lưu dữ liệu vào bảng Amazon DynamoDB. |
| **4. RESTful APIs**	| Đưa ra chức năng Lambda thông qua Amazon API Gateway dưới dạng RESTful API mà trang web tĩnh có thể gọi. |  
* Các mô-đun này được dự định sẽ được thực hiện tuần tự..
* Sau khi bạn hoàn thành workshop, bạn có thể xóa tất cả các tài nguyên đã được tạo bằng cách làm theo hướng dẫn dọn dẹp.
* ✅Xem lại và làm theo hướng dẫn trong hướng dẫn thiết lập, trong đó bạn sẽ định cấu hình IDE AWS Cloud9 của mình và thiết lập các điều kiện cần thiết như Tài khoản AWS.