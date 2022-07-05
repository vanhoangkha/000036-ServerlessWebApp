---
title : "Serverless Backend"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

#### Serverless Service Backend

* Trong mô-đun này, bạn sẽ sử dụng [AWS Lambda][lambda] và [Amazon DynamoDB][dynamodb] để build một tiến trình backend để xử lý các yêu cầu từ phía ứng dụng web của bạn. Ứng dụng web của bạn đã deploy ở mô-đun đầu tiên cho phép người dùng yêu cầu một chú kỳ lân được gửi đến địa điểm mà họ chọn. Để thực hiện các yêu cầu đó, JavaScript thực thi trên trình duyệt sẽ cần phải invoke dịch vụ thực thi trên cloud.
* Bạn sẽ triển khai một Lambda function để được invoke mỗi khi người dùng yêu cầu một con kỳ lân. Function này sẽ chọn một con kỳ lân từ bầy, ghi lại yêu cầu vào bảng DynamoDB và phản hồi đến front-end ứng dụng với thông tin chi tiết về kỳ lân đã được gửi đi.
![Serverless Backend](/images/3.backend/3.1-architect.png?width=90pc)
* Function được gọi từ phía trình duyệt sử dụng [Amazon API Gateway][api-gw]. Bạn sẽ triển khai việc kết nối ở mô-đun tiếp theo. Ở mô-đun này, bạn sẽ chỉ phải kiểm tra hoạt động độc lập của function này. Đảm bảo rằng bạn đã hoàn thành nội dung bước **Quản lý User** trước khi thực hiện mô-đun này.



[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[lambda]: https://aws.amazon.com/lambda/
[api-gw]: https://aws.amazon.com/api-gateway/
[dynamodb]: https://aws.amazon.com/dynamodb/
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[iam-console]: https://console.aws.amazon.com/iam/home
[lambda-console]: https://console.aws.amazon.com/lambda/home