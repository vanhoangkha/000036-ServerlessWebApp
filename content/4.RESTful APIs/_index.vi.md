+++
title = "RESTful APIs"
date = 2020-04-18T00:38:32+07:00
weight = 8
chapter = true
pre = "<b>4. </b>"
+++


# Module 4: RESTful APIs với AWS Lambda và Amazon API Gateway  
---
#### Tổng quan   

* Trong module này, ta sử dụng API Gateway để hiển thị các hàm chức năng Lambda mà ta đã xây dựng ở [module trước] [serverless-backend] dưới dạng API RESTful. API này cho phép nó được gọi qua Internet, và được bảo mật bởi Amazon Cognito mà đã được tạo ở module [Quản lý Người dùng] [user-management]. Sau đó nhờ có cấu hình này, trang web tĩnh của chúng ta sẽ trở thành thành một ứng dụng web động với các mã lệnh JavaScript được thêm vào trên phía máy khách, giúp thực hiện các lệnh gọi AJAX vào các API được hiển thị.
![API](/images/4.restfulapi/4.1-architect.png?width=50pc)
* Sơ đồ trên cho thấy cách xây dựng các thành phần của API Gateway trong module này tích hợp với các thành phần hiện có mà ta đã xây dựng trước đó. Các mục màu xám là các thành phần ta đã thực hiện trong các module trước.
* Trang web tĩnh mà ta xây dựng ở module đầu tiên đã được cấu hình để tương tác với API mà ta sẽ xây dựng trong module này. Giao diện trang /ride.html có một bản đồ đơn giản để phục vụ nhu cầu một chuyến đi kỳ lần. Sau khi xác thực bằng trang /signin.html, người dùng có thể chọn vị trí xuất phát bằng cách nhấp vào một điểm trên bản đồ và sau đó yêu cầu một chuyến đi bằng cách chọn nút "Request Unicorn" ở góc phải trên của trang.
* This module will focus on the steps required to build the cloud components of the API, but if you're interested in how the browser code works that calls this API, you can inspect the [ride.js](/source/ride.js) file of the website. In this case the application uses jQuery's [ajax()](https://api.jquery.com/jQuery.ajax/) method to make the remote request.
* Module này sẽ tập trung vào các bước cần thiết để xây dựng các thành phần của API, nhưng nếu bạn quan tâm đến cách mà trình duyệt gọi API này, bạn có thể kiểm tra nội dung của file [ride.js](/source/ride.js). Trong trường hợp này, ứng dụng sử dụng [ajax()](https://api.jquery.com/jQuery.ajax/) của jQuery để tạo yêu cầu từ xa.

#### Hướng dẫn Cài đặt

* Đảm bảo bạn đã hoàn thành bước **Serverless Backend** trước khi bắt đầu workshop.
* Mỗi phần sau đây cung cấp nội dung triển khai từ tổng quan cho tới hướng dẫn chi tiết, từng bước một. Trong đó tổng quan giúp ta hình dung được ngữ cảnh để có thể hoàn thành việc triển khai nếu ta đã quen thuộc với AWS Management Console hoặc ta muốn tự mình khám phá các dịch vụ mà không cần theo dõi hướng dẫn chi tiết.



