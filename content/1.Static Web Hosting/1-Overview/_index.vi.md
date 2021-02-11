---
title: "1 - Kiến trúc tổng quan"
date: 2020-04-18T00:39:21+07:00
---

#### Kiến trúc tổng quan

Kiến trúc trong mô-đun này khá đơn giản. Toàn bộ nội dung web tĩnh bao gồm HTML, CSS, JavaScript, các hình ảnh và tập tin khác sẽ được quản lý bởi AWS Amplify Console và phục vụ thông qua Amazon CloudFront. Các người dùng cuối của bạn sẽ truy cập tới trang thông qua URL được công khai bởi AWS Amplify Console. Bạn không cần phải chạy web server hoặc sử dụng các dịch vụ khác để host trang web nữa.

![Static website architecture](/images/1.staticwebsite/1.1-architect-web.png?width=90pc)    

#### Hướng dẫn thực hiện

Đảm bảo bạn đã hoàn thành hướng dẫn chuẩn bị môi trường.

Các bước tiếp theo sẽ cung cấp các bước thực hiện tổng quan cũng như chi tiết theo từng bước. Các bước tổng quan có thể đủ để bạn thực hiện workshop này nêu như bạn đã quen thuộc với AWS Management Console hoặc bạn muốn tự khám phá các dịch vụ mà không cần xem hướng dẫn chi tiết.

#### Lựa chọn Region

Workshop này có thể được chạy trên tất cả các AWS Region hỗ trợ những services sau:

- AWS Amplify Console
- AWS CodeCommit

Bạn có thể xem từ **AWS region table** trong AWS documentation để thấy các Regions hỗ trợ 2 dịch vụ trên. Các Regions mà bạn có thể chọn bao gồm:
* North America: N. Virginia, Ohio, Oregon
* Europe: Ireland, London, Frankfurt
* Asia Pacific: Tokyo, Seoul, Singapore, Sydney, Mumbai

Sau khi bạn chọn 1 Region, bạn nên thực hiện toàn bộ các bước trong workshop của mình ở Region đó. Đảm bảo bạn lựa chọn đúng Region từ menu dropdown ở phía trên góc phải trong AWS Console trước khi bắt đầu thực hiện các hướng dẫn trong workshop.