---
title: "4 - Chỉnh sửa trang web"
date: 2020-04-18T00:39:21+07:00
---

#### Chỉnh sửa trang web
**AWS Amplify Console** sẽ rebuild và redeploy lại ứng dụng khi nó nhận thấy có sự thay đổi ở repository được kết nối. Hãy thử thay đổi một chút ở Main page để kiểm tra quá trình này.

1. Từ môi trường Cloud9 mở tập tin ```index.html``` ở thư mục gốc của repository.
2. Chỉnh sửa dòng title:
    ```
      <title>Wild Rydes</title>
    ```
    Bằng nội dung:
    ```
      <title>Wild Rydes - Rydes of the Future!</title>
    ```
    Lưu tập tin.
3. Commit thay đổi lên git repository:
    ```
    $ git add index.html 
    $ git commit -m "updated title"
    [master dfec2e5] updated title
     1 file changed, 1 insertion(+), 1 deletion(-)
    
    $ git push
    Counting objects: 3, done.
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 315 bytes | 315.00 KiB/s, done.
    Total 3 (delta 2), reused 0 (delta 0)
    remote: processing 
    To https://git-codecommit.us-east-1.amazonaws.com/v1/repos/wildrydes-site
       2e9f540..dfec2e5  master -> master
   ```
    **Amplify Console** sẽ bắt đầu build trang web sau khi nhận thấy có cập nhật ở  repository. Thường thì sẽ rất nhanh đấy! Sau đó hãy qua lại trang [Amplify Console console page](https://console.aws.amazon.com/amplify/home) để xem quá trình được diễn ra.

4. Sau khi hoàn tất, hãy thử mở lại trang Wild Rydes và kiểm tra sự thay đổi ở title.
    
    ![Amplify](/images/1.staticwebsite/1.11-updatedtitle.png?width=30pc)   

#### Tóm tắt

**AWS Amplify Console** cho phép chúng ta dễ dàng deploy một trang web tĩnhtĩnh theo mô hình continuous integration và continuous delivery. Amplify Console có khả năng "xây dựng" một ứng dụng phức tạp hơn dựa trên javascript framework và cho bạn xem trước được ứng dụng này khi render trên các mobile platform thông dụng.

Trong module này, bạn đã tạo ra một trang web tĩnh sử dụng làm nền tảng cho doanh nghiệp Wild Rydes.

#### Tiếp theo

Ở module tiếp theo, **User Management**, bạn sẽ tiến hành cấu hình Amazon Cognito User Pools để quản lý người dùng cho ứng dụng của chúng ta.

[setup]: ../0_Setup/
[commit]: https://aws.amazon.com/codecommit
[github]: https://github.com
[iam-console]: https://console.aws.amazon.com/iam/home
[codecommit-free]: https://aws.amazon.com/codecommit/pricing/
[codecommit-console]: https://console.aws.amazon.com/codesuite/codecommit/repositories
[create-repo]: https://help.github.com/en/articles/create-a-repo
[github-new-sshkey]: https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
[github-clone]: https://help.github.com/en/articles/cloning-a-repository
[amplify-console]: https://aws.amazon.com/amplify/console/
[amplify-console-console]: https://console.aws.amazon.com/amplify/home
[region-services]: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/
