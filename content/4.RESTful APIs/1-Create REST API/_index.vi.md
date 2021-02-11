---
title: "1 - Tạo một REST API mới"
date: 2020-04-18T00:39:21+07:00
---
#### Tạo một REST API mới

Sử dụng Amazon API Gateway console để tạo một API mới với tên `WildRydes`.

1. Di chuyển đến [Amazon API Gateway Console][api-gw-console]
2. Chọn **Create API**.
3. Trong panel **REST API**, chọn **Build**.
![API](/images/4.restfulapi/4.2-restapi.png?width=90pc)
4. Nhập vào **API Name** với tên `WildRydes`.
5. Chọn `Edge optimized` từ danh sách **Endpoint Type**.
    ***Ghi chú***: Lựa chọn Edge optimized là lựa chọn tốt nhất cho các dịch vụ công cộng được truy cập vào từ ngoài Internet. Regional endpoint sẽ được sử dụng cho các API được truy cập bên trong cùng một AWS Region. Các Private API được sử dụng cho các dịch vụ nội bộ bên trong Amazon VPC.
6. Chọn **Create API**
![API](/images/4.restfulapi/4.3-newapiconfig.png?width=90pc)

[amplify-console]: https://aws.amazon.com/amplify/console/
[amplify-console-console]: https://console.aws.amazon.com/amplify/home
[api-gw]: https://aws.amazon.com/api-gateway/
[api-gw-console]: https://console.aws.amazon.com/apigateway/home
[cognito-console]: https://console.aws.amazon.com/cognito/home
[cognito]: https://aws.amazon.com/cognito/
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[dynamodb]: https://aws.amazon.com/dynamodb/
[iam-console]: https://console.aws.amazon.com/iam/home
[jwt-decoder]: https://jwt.io/
[lambda-console]: https://console.aws.amazon.com/lambda/home
[lambda]: https://aws.amazon.com/lambda/