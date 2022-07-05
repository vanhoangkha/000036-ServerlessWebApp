---
title : "Tạo bảng DynamoDB"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---

####  Tạo một bảng trong Amazon DynamoDB

Sử dụng Amazon DynamoDB console để tạo một bảng DynamoDB mới. Gọi đến bảng `Rides` và gán một partition key là `RideId` với kiểu String. Tên bản và partition key có sự phân biệt chữ hoa và chữ thường. Đảm bảo ràng bạn sử dụng chính xác các ID được cung cấp. Sử dụng thông số mặc định cho các cấu hình khác.

Sau khi bạn tạo được một bảng, ghi chú lại thông tin ARN để sử dụng ở bước tiếp theo.

1. Di chuyển đến [Amazon DynamoDB Console][dynamodb-console]
1. Chọn **Create table**.
1. Nhập `Rides` ở mục **Table name**. Nội dung này có phân biệt chữ hoa và chữ thường.
1. Nhập `RideId` ở mục **Partition key** và chọn **String** cho key type. Nội dung này có phân biệt chữ hoa và chữ thường.
2. Kiểm tra và lựa chọn **Use default settings**, sau đó chọn **Create**.
3. Di chuyển đến cuối mục Overview của bảng vừa được tạo mới và ghi chú lại thông tin **ARN**. Bạn sẽ cần đến nó ở bước sau.

**Ghi chú**: Kiểm tra lại lần nữa tên bảng DynamoDB của bạn (**Rides**) và partition key (**RideId**) trước khi sang bước kế tiếp.
![DynamoDB](/images/3.backend/dynamodb-verify.png?width=90pc)    

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[lambda]: https://aws.amazon.com/lambda/
[api-gw]: https://aws.amazon.com/api-gateway/
[dynamodb]: https://aws.amazon.com/dynamodb/
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[iam-console]: https://console.aws.amazon.com/iam/home
[lambda-console]: https://console.aws.amazon.com/lambda/home