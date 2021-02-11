---
title: "2 - Tạo IAM Role"
date: 2020-04-18T00:39:21+07:00
---
#### Tạo một IAM Role cho Lambda function

Với mỗi Lambda function cần có một IAM role liên kết với nó. Role sẽ định nghĩa các AWS service mà function được phép thao tác. Đối với mục tiêu của workshop này, bạn sẽ cần phải tạo một IAM role cho phép Lambda function quyền được ghi nhận log từ Amazon CloudWatch Logs và được truy cập để ghi lại nội dung các mục vào bảng DynamoDB.

Sử dụng IAM console để tạo một role mới. Đặt tên role là `WildRydesLambda` và chọn role type là AWS Lambda. Bạn sẽ cần đính các policy gán quyền cho function được phép ghi vào CloudWatch Logs và đưa các mục đó vào bảng DynamoDB.

Đính managed policy có tên `AWSLambdaBasicExecutionRole` vào role này để cấp quyền dịch vụ CloudWatch Logs. Bạn cũng cần phải tạo một custom inline policy cho role để cho phép function thực thi `ddb:PutItem` lên bảng mà bạn đã tạo ra ở nội dung phía trước.

1. Di chuyển đến [AWS IAM Console][iam-console]
2. Chọn **Roles** ở thanh điều hướng bên trái và chọn **Create role**.
![IAM](/images/3.backend/iam-createrole.png?width=90pc)    
 
3. Chọn role type là **Lambda** từ nhóm **AWS service**, sau đó chọn **Next: Permissions**.
    **Ghi chú:** Khi chọn role type thì sẽ tự động tạo ra một trust policy cho role của bạn nhằm cho phép AWS service có thể assume role này khi bạn cần. Nếu bạn tạo role thông qua CLI, AWS CloudFormation hay bằng cơ chế khác, bạn cần phải chỉ định trực tiếp một trust policy.
![IAM](/images/3.backend/iam-chooselambda.png?width=90pc)    
4. Nhập nội dung `AWSLambdaBasicExecutionRole` vào ô **Filter** và lựa chọn vào role này.
5. Chọn **Next: Tags**. Thêm các tag nếu bạn muốn.
6. Chọn **Next: Review**.
7. Nhập vào **Role name** là `WildRydesLambda`.
8. Chọn **Create role**. 
![IAM](/images/3.backend/iam-rolecreated.png?width=90pc)  

#### Thêm quyền về DynamoDB
Kế đến, chúng ta cần phải thêm các quyền cho role để role có thể truy xuất vào bảng DynamoDB của bạn.

1. Ở trong IAM Console, ở trang Roles, nhập `WildRydesLambda` vào filter box và chọn role mà bạn vừa tạo ra.
2. Ở tab Permissions, chọn **Add inline policy** ở vị trí góc phải dưới để tạo một inline policy mới cho role.
![IAM](/images/3.backend/iam-addpolicy.png?width=90pc)  
3. Chọn **Choose a service**.
4. Nhập nội dung `DynamoDB` vào khung tìm kiếm **Find a service** và chọn **DynamoDB**.
5. Ở mục **Access Level** chọn **Write** từ danh sách.
6. Chọn vào ô **PutItem** khi lựa chọn xuất hiện.
![IAM](/images/3.backend/iam-addpolicy-putitem.png?width=90pc)
7. Chọn mục **Resources**.
8. Với lựa chọn **Specific**, chọn **Add ARN link** trong mục **table**.
![IAM](/images/3.backend/iam-addpolicy-putitem-addarn.png?width=90pc)
9. Dán ARN của bảng DynamoDB mà bạn đã tạo ở phần trước và khung **Specify ARN for table** và chọn **Add**.
![IAM](/images/3.backend/iam-addarncomplete.png?width=90pc)
10. Chọn **Review Policy**.
11. Nhập vào tên policy là `DynamoDBWriteAccess` và chọn **Create policy**.
![IAM](/images/3.backend/iam-namingthepolicy.png?width=90pc)


[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[lambda]: https://aws.amazon.com/lambda/
[api-gw]: https://aws.amazon.com/api-gateway/
[dynamodb]: https://aws.amazon.com/dynamodb/
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[iam-console]: https://console.aws.amazon.com/iam/home
[lambda-console]: https://console.aws.amazon.com/lambda/home