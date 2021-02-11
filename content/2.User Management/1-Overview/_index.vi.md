---
title: "1 - Kiến trúc tổng quan"
date: 2020-04-18T00:39:21+07:00
---


#### Kiến trúc tổng quan

Khi người dùng truy cập đến trang web của bạn, họ sẽ tiến hành đăng kí một tài khoản người dùng. Đối với mục tiêu của workshop này, chúng ta chỉ yêu cầu người dùng cung cấp địa chỉ email và password để có thể đăng kí tài khoản. Tuy nhiên, bạn có thể cấu hình Amazon Cognito yêu cầu thêm những thông tin khác trong ứng dụng của các bạn.

Sau khi người dùng submit đăng kí của họ, Amazon Cognito sẽ gửi một email xác nhận chứa mã xác nhận đến địa chỉ email mà họ cung cáp. Để xác nhận tài khoản, người dùng sẽ quay trở lại trang web và nhập địa chỉ email cùng với mã xác nhận đã nhận được. Bạn có thể thực hiện việc xác nhận ở trên **Amazon Cognito console** nếu bạn muốn sử dụng một địa chỉ email giả để thử nghiệm.

Sau khi người dùng đã có tài khoản (được xác nhận thông qua email hoặc console), họ sẽ có thể đăng nhập. Khi người dùng đăng nhập, họ sẽ sử dụng username (hoặc email) và password. Một function Javascript sẽ giao tiếp với Amazon Cognito, xác thực sử dụng giao thức Secure Remote Password (SRP) và nhận về một set JSON Web Tokens (JWT). JWT chứa các thông tin định danh của người dùng và sẽ được sử dụng ở mô-đun tiếp theo cho việc xác thực với RESTful API mà bạn build với Amazon API Gateway.

![Xác thực](/images/2.authentication/2.1-architect.png?width=50pc)   


#### Hướng dẫn thực hiện

Đảm bảo rằng bạn đã hoàn thành hướng dẫn **Host Web tĩnh** trước khi tiến hành workshop này.

Các bước tiếp theo sẽ cung cấp các bước thực hiện tổng quan cũng như chi tiết theo từng bước. Các bước tổng quan có thể đủ để bạn thực hiện workshop này nêu như bạn đã quen thuộc với AWS Management Console hoặc bạn muốn tự khám phá các dịch vụ mà không cần xem hướng dẫn chi tiết.

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[cognito-console]: https://console.aws.amazon.com/cognito/home
[jwt-decoder]: https://jwt.io/