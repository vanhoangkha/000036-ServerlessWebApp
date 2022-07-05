---
title : "Cập nhật config.js"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 3.4 </b> "
---

#### Cập nhật tập tin config.js trong trang Web của bạn

Tập tin **/js/config.js** chứa các cấu hình user pool ID, app client ID và Region. Cập nhật tập tin với các thông tin cấu hình đã được tạo ra ở các bước phía trước và commit tập tin lên git repository.

1. Trong môi trường Cloud9, mở tập tin `js/config.js`
2. Cập nhật mục `cognito` với giá trị user pool và app mà bạn vừa tạo ra ở các bước phía trước.
    Bạn có thể tìm thấy thông tin `userPoolId` ở trang Pool details trong Amazon Cognito console sau khi chọn vào user pool mà bạn đã tạo.

    ![Authentication](/images/2.authentication/pool-id.png?width=90pc)

    Bạn có thể tìm thấy thông tin `userPoolClientId` bằng cách chọn **App clients** ở thanh điều hướng bên trái. Sử dụng giá trị ở mục **App client id** của app client mà bạn đã tạo ra ở bước trước.

    ![Authentication](/images/2.authentication/client-id.png?width=90pc)

    Giá trị `region` là AWS Region code của region mà bạn tạo user pool. VD: `us-east-1` là mã của Region N. Virginia , hoặc `us-west-2` là mã của Region Oregon. Nếu bạn không chắc chắn về giá trị này, bạn có thể xem giá trị Pool ARN ở trang Pool details. Giá trị Region code là phần thông tin ngay sau `arn:aws:cognito-idp:` trong nội dung của giá trị ARN.

    Tập tin config.js sau khi được cập nhật sẽ tương tự như sau. Các giá trị thực tế sẽ khác so với trong ví dụ được đưa ra:
    ![Authentication](/images/2.authentication/2.8-configjs.png?width=90pc)

3. Lưu tập tin đã thay đổi và đảm bảo rằng tên tập tin vẫn là `config.js`.
4. Commit các thay đổi lên git repository:
    ```
    $ git add js/config.js 
    $ git commit -m "configure cognito"
    $ git push
    ...
    Counting objects: 4, done.
    Compressing objects: 100% (4/4), done.
    Writing objects: 100% (4/4), 415 bytes | 415.00 KiB/s, done.
    Total 4 (delta 3), reused 0 (delta 0)
    To https://git-codecommit.us-east-1.amazonaws.com/v1/repos/wildrydes-site
       7668ed4..683e884  master -> master
    ```

    Amplify Console sẽ nhận thấy các thay đổi và tiến hành build và deploy lại ứng dụng web của bạn.

**Ghi chú:** Thay vì bạn viết code cho việc quản lý đăng kí, xác nhận và đăng nhập phía trình duyệt, chúng tôi cung cấp phương án triển khai trong nội dung mà bạn đã deploy ở mô-đun thứ nhất. Tập tin **cognito-auth.js**(/js/cognito-auth.js) chứa code đảm nhận các UI event và invoke các method tương ứng trong Amazon Cognito Identity SDK. Thông tin chi tiết về SDK bạn có thể xem tại [trang project trên GitHub](https://github.com/aws/amazon-cognito-identity-js).

#### Kiểm tra kết quả thực hiện

1. Truy cập vào trang `/register.html` với domain trang web của bạn, hoặc chọn **Giddy Up!** ở homepage trang web của bạnbạn.
2. Hoàn thành form đăng kí và chọn **Let's Ryde**. Bạn có thể sử dụng email của bạn hoặc nhập vào một email giả. Đảm bảo rằng password chưa tối thiểu một ký tự in hoa, một ký tự số, và một ký tự đặc biệt. Đừng quên password đã nhập để sử dụng ở các bước tiếp theo. Bạn sẽ thấy một thông báo xác nhận rằng user đã được tạo.
![Authentication](/images/2.authentication/2.9-register.png?width=90pc)
3. Xác nhận user mới được tạo bằng một trong hai cách sau:
    1. Nếu bạn sử dụng địa chỉ email của bạn, bạn có thể xác nhận tài khoản bằng cách truy cập vào trang `/verify.html` với domain trang web của bạn và nhập vào verification code được gửi thông qua email. Hãy cẩn thận vì có thể email xác nhận được gửi vào thư mục Spam của hộp mail. Khi triển khai thực tế, chúng tôi khuyến cáo [cấu hình user pool sử dụng Amazon Simple Email Service](http://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pool-settings-message-customizations.html#cognito-user-pool-settings-ses-authorization-to-send-email) để gửi email dưới domain của bạn..
![Authentication](/images/2.authentication/2.10-verify.png?width=90pc)
    2. Nếu bạn sử dụng một email giả, bạn cần phải xác nhận tài khoản thông qua Cognito console.
       1. Từ AWS console, chọn Services sau đó chọn **Cognito** ở mục Security, Identity & Compliance.
       2. Chọn **Manage your User Pools**
       3. Chọn user pool `WildRydes` và chọn **Users and groups** ở thanh điều hướng bên trái.
       4. Bạn sẽ thấy một user tương ứng với email đã được sử dụng ở trang đăng kí. Chọn username để tới trang user detail.
       5. Chọn **Confirm user** để hoàn tất quá trình tạo user.

4. Sau khi xác nhận user mới (bằng một trong hai cách: thông qua trang `/verify.html` hay Cognito console), truy cập vào `/signin.html` và đăng nhập với thông tin địa chỉ email và password đã được sử dụng ở bước đăng kí user.

5. Nếu thành công, bạn sẽ được chuyển đến trang `/ride.html`. Bạn cũng sẽ thấy một thông báo rằng API chưa được cấu hình.

![Authentication](/images/2.authentication/2.11-loginsuccess.png?width=90pc)

#### Tóm tắt

**Amazon Cognito** cung cấp hai phương thức để quản lý user, federated identities và user pool. [Amazon Cognito][cognito] user pools có thể xử lý hầu hết các tác vụ liên quan đến việc quản lý user, user login credential, reset password, multifactor authentication và hơn thế nữa!

Trong mô-đun này, bạn đã sử dụng user pool để tạo một hệ thống hoàn chỉnh cho việc quản lý user cho phép chúng ta có thể xác thực user và quản lý thông tin của user đó. Từ đó, bạn đã cập nhật cho trang web sử dụng user pool và AWS SDK để cung cấp một form đăng nhập cho trang web.

#### Nội dung mở rộng

* Hãy thử copy **auth_token** mà bạn nhận được và dán vào [online JWT Decoder][jwt-decoder] để hiểu rõ hơn sự tương quan giữa token và ứng dụng web của bạn.
![Authentication](/images/2.authentication/2.12-jwt.png?width=90pc)

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[cognito-console]: https://console.aws.amazon.com/cognito/home
[jwt-decoder]: https://jwt.io/