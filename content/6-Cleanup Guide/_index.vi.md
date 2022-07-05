---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---


#### Dọn dẹp tài nguyên

#### Module 4 - Xóa REST API  
* Phần nội dung này hướng dẫn cách xóa bỏ REST API đã được tạo ở module 4. Tìm tới **Delete API** nằm trong menu thả xuống khi bấm vào **Actions**, sau đó lựa chọn API mà bạn muốn xóa nằm trong Amazon API Gateway Console.
1. Đi tới trang [Amazon API Gateway Console][api-gw-console]
2. Chọn tên của API đã tạo ở module 4.
3. Bấm vào **Actions** rồi chọn **Delete API** nằm trong menu thả xuống.
4. Chờ khi xuất hiện một cửa sổ nhập liệu, thực hiện nhập tên của API mà bạn muốn xóa, rồi bấm **Delete API**.

#### Module 3 - Xóa Serverless Backend  
* Phần nội dung này hướng dẫn cách xóa bỏ AWS Lambda Function, IAM role và các bảng dữ liệu Amazon DynamoDB đã được tạo ở module 3.

##### Lambda Function

1. Đi tới trang [AWS Lambda console][lambda-console]
2. Chọn hàm chức năng `RequestUnicorn` đã tạo ở module 3.
3. Từ menu thả xuống sau khi bấm **Actions**, chọn **Delete function**.
4. Bấm chọn **Delete** khi xuất hiện cửa sổ thông báo yêu cầu xác nhận.

##### IAM Role

1. Đi tới trang [AWS IAM Console][iam-console]
2. Chọn **Roles** từ menu điều hướng.
3. Nhập `WildRydesLambda` vào khung lọc tìm kiếm.
4. Chọn role đã được tạo ở module 3.
5. Từ menu thả xuống của **Role actions**, Chọn **Delete role**.
6. Chọn **Yes, Delete** khi xuất hiện cửa sổ yêu cầu xác nhận.

##### DynamoDB Table

1. Đi tới trang [Amazon DynamoDB Console][dynamodb-console]
2. Chọn **Tables** trong menu điều hướng..
3. Chọn bảng **Rides** là bảng đã được tạo ở module 3.
4. Chọn **Delete table** từ menu thả xuống của **Actions**.
5. Giữ nguyên lựa chọn mặc định **Delete all CloudWatch alarms for this table** rồi bấm **Delete**.

#### Module 2 - Xóa User Management  
* Xóa Amazon Cognito User Pool

1. Đi tới trang [Amazon Cognito Console][cognito-console]
2. Chọn **Manage your User Pools**.
3. Chọn tập người dùng có tên **WildRydes** đã được tạo ở module 2.
4. Chọn **Delete Pool** nằm ở góc phải trên của trang.
5. Hoàn thành quy trình xóa bỏ ứng dụng.

#### Module 1 - Xóa bỏ Ứng dụng Web   
* Xóa bỏ ứng dụng AWS Amplify Console và những tùy chọn như kho mã nguồn AWS CodeCommit hoặc GitHub đã được tạo:


##### Với ứng dụng web Amplify Console:

1. Truy cập trang ứng dụng web [Amplify Console][amplify-console-console].
2. Chọn úng dụng đã được khởi chạy.
3. Từ menu thả xuống của **Actions** nằm ở góc phải trên, Chọn *Delete App*
4. Hoàn thành thao tác xóa bỏ ứng dụng.

##### Với kho mã nguồn CodeCommit:

1. Truy cập trang [AWS CodeCommit console][codecommit-console]
2. Bấm vào nút chọn bên cạnh kho mã nguồn đã được tạo.
3. Chọn **Delete repository** nằm ở góc phải trên của trang.
4. Hoàn thành thao tác xóa bỏ kho mã nguồn.


#### Xóa bỏ nhật lý CloudWatch  
* AWS Lambda tạo ra một nhóm dữ liệu nhật ký tự động dựa trên chức năng mà AWS cung cấp và những dữ liệu này được ghi bởi Amazon CloudWatch Logs mỗi khi có lời gọi tới hàm chức năng. Bên dưới là hướng dẫn xóa nhóm dữ liệu nhật ký của hàm chức năng **RequestUnicorn**.

1. Từ trang AWS Console bấm **Services** rồi Chọn **CloudWatch** phía dưới Management Tools.
2. Chọn **Logs** nằm trong menu điều hướng..
3. Chọn nhóm dữ liệu nhật ký **/aws/lambda/RequestUnicorn**. Trường hợp ta có nhiều nhóm dữ liệu nhật ký trong cùng một account, ta nhập `/aws/lambda/RequestUnicorn` vào khung nhập liệu **Filter** để dễ dàng xác định nhóm dữ liệu nhật ký muốn xóa.
4. Chọn **Delete log group** từ menu thả xuống của **Actions**.
5. Chọn **Yes, Delete** khi xuất hiện cửa sổ yêu cầu xác nhận.
6. Nếu ta đã khởi chạy bất cứ bản mẫu CloudFormation nào để hoàn thành module, thì lặp lại các thao tác thực hiện từ bước 3 tới bước 5 cho mọi nhóm dữ liệu nhật ký bắt đầu bằng `/aws/lambda/wildrydes-webapp`.

#### Xóa bỏ Cloud9  
* Xóa bỏ môi trường phát triển ứng dụng Cloud9 đã được tạo trước đó. 

1. Truy cập trang [Cloud9 console][cloud9-console].
2. Chọn tên môi trường ta đã khởi chạy.
3. Từ thanh điều hướng bên trên, chọn **Delete**
4. Hoàn thành thao tác xóa bỏ ứng dụng.


[amplify-console-console]: https://console.aws.amazon.com/amplify/home
[amplify-console]: https://aws.amazon.com/amplify/console/
[api-gw-console]: https://console.aws.amazon.com/apigateway/home
[cloud9-console]: https://console.aws.amazon.com/cloud9/home
[codecommit-console]: https://console.aws.amazon.com/codesuite/codecommit/repositories
[codecommit-free]: https://aws.amazon.com/codecommit/pricing/
[cognito-console]: https://console.aws.amazon.com/cognito/home
[commit]: https://aws.amazon.com/codecommit
[create-repo]: https://help.github.com/en/articles/create-a-repo
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[github-clone]: https://help.github.com/en/articles/cloning-a-repository
[github]: https://github.com
[github-new-sshkey]: https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
[iam-console]: https://console.aws.amazon.com/iam/home
[lambda-console]: https://console.aws.amazon.com/lambda/home
[region-services]: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/
