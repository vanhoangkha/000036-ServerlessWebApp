---
title: "3 - Tạo Resource & Method"
date: 2020-04-18T00:39:21+07:00
---

#### Tạo Resource & Method
Tạo một Resource mới có tên /ride thuộc API của bạn. Sau đó, tạo một Method dạng POST cho tài nguyên, rồi cấu hình tích hợp với Lambda proxy mà được hỗ trợ bởi hàm chức năng RequestUnicorn được tạo ở bước đầu tiên của mô-đun này.

1. Ở thanh điều hướng bên trái, bấm **Resources** bên dưới API có tên WildRydes.
2. Từ menu thả xuống của **Actions**, chọn **Create Resource**.
![API](/images/4.restfulapi/4.9-createresource.png?width=90pc)
3. Nhập `ride` làm giá trị của **Resource Name**.
4. Đảm bảo **Resource Path** được thiết lập là `ride`.
5. Chọn **Enable API Gateway CORS** cho tài nguyên ở trên.
6. Bấm **Create Resource**.
![API](/images/4.restfulapi/4.10-clickcreateresource.png?width=90pc)
7. Với tài nguyên `/ride` đã được chọn, từ menu thả xuống của **Action**, chọn **Create Method**.
![API](/images/4.restfulapi/4.11-method.png?width=90pc)
8. Chọn `POST` khi một menu thả xuống xuất hiện, sau đó chọn **click the checkmark**.
![API](/images/4.restfulapi/4.12-post.png?width=90pc)
![API](/images/4.restfulapi/4.13-checkmark.png?width=90pc)
9.  Chọn **Lambda Function** cho kiểu tích hợp.
10. Tích chọn **Use Lambda Proxy integration**.
11. Chọn Region ta muốn sử dụng với **Lambda Region**.
12. Nhập tên của hàm chức năng mà ta đã tạo ở mô-dun trước, là `RequestUnicorn`, cho **Lambda Function**.
13. Chọn **Save**. Lưu ý rằng, nếu xuất hiện lỗi hàm chức năng không tồn tại, thì ta nên kiểm tra lại region mà ta chọn ở bước phía trên, giá trị này phải giống region ta sử dụng ở module trước.
![API](/images/4.restfulapi/4.14-done.png?width=90pc)
14. Xuất hiện một cửa sổ yêu cầu cấp quyền truy cập hàm chức năng cho Amazon API Gateway, chọn **OK**.
![API](/images/4.restfulapi/4.15-promptok.png?width=90pc)
15. Bấm chọn thẻ **Method Request**.
![API](/images/4.restfulapi/4.16-methodrequest.png?width=90pc)
16. Chọn biểu tượng hình chiếc bút ở bên cạnh **Authorization**.
17. Chọn những người dùng thuộc nhóm người dùng WildRydes Cognito từ menu thả xuống, rồi bấm bảo biểu tượng tích chọn.
![API](/images/4.restfulapi/4.17-select.png?width=90pc)