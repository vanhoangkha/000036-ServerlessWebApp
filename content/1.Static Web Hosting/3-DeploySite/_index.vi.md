---
title: "3 - Deploy trang web "
date: 2020-04-18T00:39:21+07:00
---

#### Deploy trang web với AWS Amplify Console
Tiếp theo bạn sẽ sử dụng **AWS Amplify Console** để deploy trang web mà bạn đã commited tới git.Amplify Console sẽ đảm nhiệm công việc cài đặt và chứa mã nguồn ứng dụng web tĩnh của bạn và cung cấp các tính năng hữu ích để đơn giản hóa quản lý vòng đời của ứng dụng cũng như thực hiện các best practices.


1. Mở  trang [Amplify Console console page](https://console.aws.amazon.com/amplify/home)
2. Click **Get Started** dưới mục Deploy with Amplify Console
3. Chọn *Repository service provider* đã sử dụng ( AWS CodeCommit hoặc GitHub) và Click **Continue** ( Nếu bạn dùng GitHub, bạn sẽ cần cho phép AWS Amplify truy cập được tới GitHub account của bạn).
   ![Amplify](/images/1.staticwebsite/1.6-amplify.png?width=90pc) 
4. Từ menu dropdown chọn *Repository* và *Branch* mà bạn đã tạo hôm nay.
     ![Amplify](/images/1.staticwebsite/1.7-amplify.png?width=90pc)   
5. Trên trang "Configure build settings" để cấu hình mặc định và chọn **Next**
6. Trên trang "Review" chọn **Save and deploy**
    
Sẽ mất khoảng vài phút để Amplify Console tạo những tài nguyên cần thiết và deploy trang web của bạm.
  
   ![Amplify](/images/1.staticwebsite/1.8-amplify.png?width=90pc)   

Sau khi hoàn thành, click vào hình ảnh trang web của bạn để mở trang Wild Rydes. ( Hoặc click vào URL mà Amplify Console tạo ra)
![Amplify](/images/1.staticwebsite/1.9-amplify.png?width=50pc)   
Nếu bạn click vào link **Master**, bạn sẽ thấy các thông tin về deployment của trang web của bạn, cùng với một số trang render thử trên các platforms khác nhau:
![Amplify](/images/1.staticwebsite/1.81-amplify.png?width=90pc)   
![Amplify](/images/1.staticwebsite/1.10-amplify.png?width=90pc)   