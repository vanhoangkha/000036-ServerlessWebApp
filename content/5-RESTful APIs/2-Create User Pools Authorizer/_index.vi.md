---
title : "User Pool Authorizer"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 5.2 </b> "
---

#### Tạo Nhóm Người Dùng được Ủy quyền(UserPool Authorizer) với Cognito

Amazon API Gateway có thể sử dụng JWT tokens được trả về bởi Nhóm người dùng Cognito để xác thực các lệnh gọi API. 
Trong bước này, ta sẽ cấu hình người dùng được ủy quyền cho phép gọi tới API là nhóm người dùng ta đã tạo trong **User Management**.

Trên trang Amazon API Gateway console, tạo Nhóm Người dùng Cognito mới được ủy quyền sử dụng API. Cấu hình với các thông tin chi tiết của nhóm người dùng mà ta đã tạo ở mô-đun trước. Ta có thể kiểm tra cấu hình trong bảng điều khiển bằng cách sao chép và dán auth token được tạo ra sau khi ta thực hiện đăng nhập trên trang /signin.html.

1. Bên dưới API mà ta đã tạo, bấm chọn **Authorizers**.
2. Bấm chọn **Create New Authorizer**.
![API](/images/4.restfulapi/4.4-createnewauthorizer.png?width=90pc)
3. Nhập `WildRydes` vào phần tên của Authorizer.
4. Chọn **Cognito** làm loại người dùng.
5. Trong menu thả xuống của Region bên dưới **Cognito User Pool**, chọn Region tương ứng với nhóm người dùng Cognito mà ta đã tạo ở mô-đun User Management (mặc định là Region hiện tại).
6. Nhập `WildRydes` (hoặc tên của nhóm người dùng mà bạn đã tạo) trong khung nhập liệu giá trị của **Cognito User Pool**.
7. Nhập `Authorization` cho **Token Source**.
8. Bấm **Create**.
![API](/images/4.restfulapi/4.5-authorizer.png?width=90pc)

#### Kiểm tra cấu hình của Authorizer

1. Mở một thẻ trình duyệt mới rồi truy cập vào `/ride.html`.
2. Sau đó bạn sẽ được điều hướng tới trang đăng nhập, thực hiện đăng nhập với tên người dùng bạn đã tạo ở mô-đun trước. Bạn sẽ được điều hướng trở lại trang `/ride.html`.
3. Sao chép auth token trừ bảng thông báo trên trang `/ride.html`.
![API](/images/4.restfulapi/4.6-successauthen.png?width=90pc)
4. Trở về tab mà ta đã thực hiện tạo Authorizer.
5. Bấm **Test** ở bên dưới thẻ thông tin của Authorizer.
![API](/images/4.restfulapi/4.7-testauthen.png?width=90pc)
6. Dán auth token vào phần nội dung **Authorization Token** hiển thị trong ở hộp thoại.
![API](/images/4.restfulapi/4.8-testauthen2.png?width=90pc)
7. Bấm **Test** và kiểm tra kết quả trả về là 200 hay không và những thông báo đi kèm với người dùng được hiển thị.