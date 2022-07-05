---
title : "Tạo User Pool"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

####  Tạo một Amazon Cognito User Pool

**Amazon Cognito** cung cấp hai cơ chế để xác thực người dùng. Bạn có thể sử dụng Cognito User Pools để thêm chức năng đăng kí và đăng nhập cho ứng dụng của bạn hoặc sử dụng Cognito Identity Pools để xác thực người dùng thông qua những nhà cung cấp định danh mạng xã hội như Facebook, Twitter, hoặc Amazon, với giải pháp định danh SAML, hoặc sử dụng hệ thống định danh của bạn. Trong mô-đun này, bạn sẽ sử dụng một user pool như là một backend cung cấp các trang đăng kí và đăng nhập tài khoản.

Sử dụng **Amazon Cognito console** để tạo một user pool với các thiết lập mặc định. Khi pool của bạn được tạo, hãy ghi chú lại Pool ID. Bạn sẽ cần sử dụng giá trị này ở phần tiếp theo.

1. Di chuyển đến trang [Amazon Cognito Console][cognito-console]
![Authentication](/images/2.authentication/2.2-cognito.png?width=90pc)
2. Chọn **Manage your User Pools**.
3. Chọn **Create a User Pool**
4. Nhập vào một tên cho user pool, ví dụ như `WildRydes`, sau đó chọn **Review Defaults**
![Authentication](/images/2.authentication/2.3-poolname.png?width=90pc)
5. Ở trang review, chọn **Create pool**.
![Authentication](/images/2.authentication/2.4-createpool.png?width=90pc)
6. Ghi chú lại **Pool Id** ở trang Pool details của user pool vừa được tạo.
![Authentication](/images/2.authentication/2.5-poolid.png?width=90pc)

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[cognito-console]: https://console.aws.amazon.com/cognito/home
[jwt-decoder]: https://jwt.io/