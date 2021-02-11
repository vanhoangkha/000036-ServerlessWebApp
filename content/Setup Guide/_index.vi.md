+++
title = "Hướng dẫn chuẩn bị"
date = 2020-04-18T00:38:32+07:00
weight = 1
chapter = true
pre = "<b> </b>"
+++

# Thiết lập môi trường

#### Tài khoản AWS

* Để hoàn thành workshop này, bạn sẽ cần có tài khoản AWS và quyền truy cập AWS Identity and Access Management (IAM), Amazon Cognito, AWS Lambda, Amazon S3, Amazon API Gateway, AWS Amplify Console, Amazon DynamoDB và AWSCloud9 trong tài khoản đó. Mã và hướng dẫn trong workshop này chỉ phù hợp một người tham gia  sử dụng một tài khoản AWS tại một thời điểm. Nếu bạn cố gắng chia sẻ tài khoản với người tham gia khác, bạn sẽ gặp phải xung đột đặt tên cho các tài nguyên nhất định. Bạn có thể giải quyết vấn đề này bằng cách thêm hậu tố trong tên tài nguyên của mình hoặc sử dụng các Region riêng biệt, nhưng các hướng dẫn không cung cấp chi tiết về các thay đổi cần thiết để thực hiện công việc này.
* Sử dụng tài khoản cá nhân hoặc tạo tài khoản AWS mới cho workshop này thay vì sử dụng tài khoản của tổ chức để đảm bảo bạn có quyền truy cập đầy đủ vào các dịch vụ cần thiết và để đảm bảo bạn không để lại bất kỳ tài nguyên nào từ workshop.

#### AWS Cloud9 IDE

* AWS Cloud9 là một môi trường phát triển tích hợp dựa trên Cloud (IDE) cho phép bạn viết, chạy và gỡ lỗi mã của mình chỉ bằng một trình duyệt. Nó bao gồm một trình soạn thảo mã, trình gỡ lỗi và thiết bị đầu cuối. Cloud9 được đóng gói sẵn các công cụ cần thiết cho các ngôn ngữ lập trình phổ biến và Giao diện dòng lệnh AWS (CLI) được cài đặt sẵn để bạn không cần cài đặt hoặc cấu hình máy tính xách tay cho workshop này. Môi trường Cloud9 của bạn sẽ có quyền truy cập vào cùng các tài nguyên AWS như người dùng mà bạn đã đăng nhập vào AWS Management Console. Hãy dành một chút thời gian và thiết lập môi trường phát triển Cloud9 của bạn.

#### Hướng dẫn từng bước

1. Truy cập vào  AWS Management Console, click **Services** sau đó chọn **Cloud9** dưới Developer Tools.
2. Click **Create environment**.
![Cloud 9](/images/1.staticwebsite/1.2-cloud9env.png?width=90pc)    
3. Enter `Development` vào **Name** và điền tùy ý vào phần **Description**.
4. Click **Next step**.
5. Bạn có thể để **Environment settings** ở cấu hình mặc định để sử dụng **t2.micro** EC2 instance size, ngoài ra Cloud 9 sẽ bị tạm dừng sau **30 minutes** không hoạt động.
6. Click **Next step**.
![Cloud 9](/images/1.staticwebsite/1.3-cloud9env.png?width=90pc)   
7. Xem lại các thông số cài đặt,click **Create environment**. Sẽ mất vài phút để môi trường của bạn được cung cấp và sẵn sàng.
8. Khi đã sẵn sàng, IDE của bạn sẽ mở ra một màn hình chào mừng. Bên dưới đó, bạn sẽ thấy một dấu nhắc. Bạn có thể chạy các lệnh AWS CLI ở đây giống như bạn làm trên máy tính của mình. Xác minh rằng người dùng của bạn đã đăng nhập bằng cách chạy
`aws sts get-caller-identity`.
```
console
aws sts get-caller-identity
```

9. Bạn sẽ thấy kết quả cho biết thông tin tài khoản và người dùng của bạn:

```
console
ec2-user:~/environment $ aws sts get-caller-identity
```
```json
    {
        "Account": "123456789012",
        "UserId": "AKIAI44QH8DHBEXAMPLE",
        "Arn": "arn:aws:iam::123456789012:user/Alice"
    }
```

10. Giữ IDE AWS Cloud9 của bạn được mở trong một tab trong suốt workshop này.

#### Tips

* Giữ một tab file text trong Cloud9 hoặc trình soạn thảo văn bản trên máy tính cục bộ của bạn để ghi chú. Khi các hướng dẫn yêu cầu bạn lưu ý một số thứ như ID hoặc Tên tài nguyên Amazon (ARN), hãy sao chép và dán mã đó vào file ghi chú.

#### Recap
* Sử dụng **AWS account** cá nhân hoặc tài khoản thử nghiệm của công ty bạn.
* Giữ cho **AWS Cloud9 IDE** luôn mở trong 1 tab trình duyệt.

#### Next
* Tiếp tục tới mô-đun đầu tiên, **Host Web tĩnh** ,bạn sẽ thực hiện deploy một trang web tĩnh thông qua AWS Amplify Console.
