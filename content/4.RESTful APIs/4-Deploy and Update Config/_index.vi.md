---
title: "4 - Triển khai & Cập nhật cấu hình"
date: 2020-04-18T00:39:21+07:00
---

#### Triển khai API
Từ trang Amazon API Gateway console, chọn Actions, rồi bấm Deploy API. Một cửa sổ tạo stage mới sẽ hiện ra. Ta có thể sử dụng `prod` làm tên của stage.

1. Trong menu thả xuống của **Actions** bấm chọn **Deploy API**.
1. Chọn **[New Stage]** trong menu thả xuống của **Deployment stage**.
1. Nhập `prod` vào khung **Stage Name**.
1. Chọn **Deploy**.
1. Lưu lại **Invoke URL**. Giá trị này sẽ được sử dụng ở bước tiếp theo.

#### Cập nhật cấu hình trang Web
Cập nhật `invoke URL` của stage vào file /js/config.js. Ta nên sao chép `invoke URL` trực tiếp từ trang chỉnh sửa stage trên Amazon API Gateway console rồi gán giá trị cho từ khóa \_config.api.invokeUrl nằm trong file /js/config.js. Đảm bảo rằng file cấu hình mà ta đang cập nhật vẫn phải chứa những nội dung cập nhật cho nhóm người dùng Cognito mà ta đã thực hiện ở mô-đun trước đó.


1. Trên môi trường phát triển Cloud9, mở file `js/config.js`
2. Cập nhật thiết lập cho **invokeUrl** nằm bên dưới từ khóa **api** trong file config.js. Thiết lập giá trị **Invoke URL** stage mà ta đã tạo từ các bước trước đây.
    Ví dụ về một tệp `config.js` hoàn chỉnh như bên dưới. Lưu ý, thực tế các giá trị trong tệp của mỗi người có thể khác nhau.
    ```JavaScript
    window._config = {
        cognito: {
            userPoolId: 'us-west-2_uXboG5pAb', // e.g. us-east-2_uXboG5pAb
            userPoolClientId: '25ddkmj4v6hfsfvruhpfi7n4hv', // e.g. 25ddkmj4v6hfsfvruhpfi7n4hv
            region: 'us-west-2' // e.g. us-east-2
        },
        api: {
            invokeUrl: 'https://rc7nyt4tql.execute-api.us-west-2.amazonaws.com/prod' // e.g. https://rc7nyt4tql.execute-api.us-west-2.amazonaws.com/prod,
        }
    };
    ```

3. Lưu tệp đã sửa đổi và đảm bảo tên tệp vẫn là `config.js`.
4. Thực hiện commit những thay đổi lên kho mã nguồn git của bạn:
    ```
    $ git add js/config.js 
    $ git commit -m "configure api invokeURL"
    $ git push
    ...
    Counting objects: 4, done.
    Compressing objects: 100% (4/4), done.
    Writing objects: 100% (4/4), 422 bytes | 422.00 KiB/s, done.
    Total 4 (delta 3), reused 0 (delta 0)
    To https://git-codecommit.us-east-1.amazonaws.com/v1/repos/wildrydes-site
       c15d5d5..09f1c9a  master -> master
    ```

    [Amplify Console][amplify-console-console] should pick up the changes and begin building and deploying your web application. Watch it to verify the completion of the deployment.

#### Thực hiện kiểm thử

1. Truy cập `/ ride.html` trong tên miền trang web của bạn.
1. Sau khi được chuyển hướng đến trang đăng nhập, thực hiện đăng nhập với tên user đã tạo trong mô-đun trước đó.
1. Sau khi hoàn tất việc tải về bản đồ, ta nhấp vào bất kỳ nơi nào trên bản đồ để đặt vị trí đón (hay vị trí bắt đầu).
1. Chọn **Request Unicorn**. Ta sẽ thấy một thông báo ở thanh bên phải rằng một con kỳ lân đang trên đường tới, rồi một biểu tượng kỳ lân bay đến vị trí đón mà ta đã chọn.

#### Tóm tắt

:key: [Amazon API Gateway][api-gw] là một dịch vụ được quản lý hoàn toàn bởi AWS giúp các nhà phát triển dễ dàng tạo, xuất bản, duy trì, giám sát và bảo mật API ở mọi quy mô. Ta có thể dễ dàng tích hợp Authorization thông qua [Amazon Cognito][cognito] và các nền tảng phụ trợ khác như [AWS Lambda][lambda], từ đó giúp tạo ra những API hoạt động hoàn toàn không cần máy chủ.

:wrench: Trong mô-đun này, ta đã sử dụng API Gateway để cung cấp API REST cho hàm chức năng Lambda đã được tạo ở mô-đun trước. 
Sau đó ta đã cập nhật trang web để có thể sử dụng API endpoint giúp ta có thể yêu cầu các chuyến đi và thông tin về chuyến đi được lưu trong bảng DynamoDB đã được tạo từ trước.

Xin chúc mừng, bạn đã hoàn thành Wild Rydes Web Application Workshop!

#### Tiếp theo

Theo dõi workshop **Hướng dẫn Xóa bỏ Tài nguyên** để nằm được cách xóa bỏ những tài nguyên mà ta đã tạo trong quá trình thực hiện workshop.

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