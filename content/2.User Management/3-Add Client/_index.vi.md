---
title: "3 - Thêm Client vào User Pool"
date: 2020-04-18T00:39:21+07:00
---

#### Thêm một App Client vào User Pool

Từ **Amazon Cognito console**, chọn user pool của bạn và sau đó chọn mục **App clients**. Thêm một app và đảm bảo rằng KHÔNG chọn vào lựa chọn **Generate client secret**. Client secret không được hỗ trợ với JavaScript SDK. Nếu bạn đã tạo một app với lựa chọn generated secret, hãy xóa nó và tạo lại một cái mới với cấu hình đúng.

1. Từ trang Pool Details của user pool, chọn **App clients** từ mục **General settings** ở thanh điều hướng bên trái.
2. Chọn **Add an app client**.
3. Nhập tên cho app client, ví dụ như `WildRydesWebApp`.
4. **Bỏ chọn** ở lựa chọn Generate client secret. Client secrets không được hỗ trợ để sử dụng với các ứng dụng chạy trên trình duyệt.
5. Chọn **Create app client**.
![Authentication](/images/2.authentication/2.6-appclient.png?width=90pc)
6. Ghi chú lại thông tin **App client id** của app vừa được tạo.
![Authentication](/images/2.authentication/2.7-appclientid.png?width=90pc)

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[cognito-console]: https://console.aws.amazon.com/cognito/home
[jwt-decoder]: https://jwt.io/