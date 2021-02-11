---
title: "2 - Tạo Git repository"
date: 2020-04-18T00:39:21+07:00
---

### Tạo git repository
Bạn có hai tùy chọn để quản lý mã nguồn cho mô-đun này:

* **AWS CodeCommit**- CodeCommit được cung cấp trong **AWS Free Tier**.
* **GitHub.com** - Nếu bạn quen với GitHub.com và đã có account.

#### Tùy chọn 1: Sử dụng AWS CodeCommit

Môi trường phát triển AWS Cloud9 đi kèm với thông tin xác thực tạm thời được liên kết với IAM user của bạn. Bạn sử dụng các thông tin đăng nhập này với AWS CLI credential helper. Kích hoạt credential helper bằng cách chạy hai lệnh sau trong môi trường Cloud9 của bạn.


```bash
git config --global credential.helper '!aws codecommit credential-helper $@'
git config --global credential.UseHttpPath true
```

Tiếp theo bạn cần tạo repository và clone nó về môi trường Cloud9 của mình:
1. Mở **AWS CodeCommit console**
2. Chọn **Create Repository**
![Code Commit](/images/1.staticwebsite/1.4-codecommit.png?width=90pc) 
3. Đặt *Repository name** là "wildrydes-site"
4. Chọn **Create**
5.  Trên menu dropdown *Clone URL* , chọn *Clone HTTPS*
![Code Commit](/images/1.staticwebsite/1.5-codecommit.png?width=90pc) 
Bây giờ từ môi trường Cloud9 của bạn
Now from your Cloud9 development environment:
1. Chạy câu lệnh `git clone` cùng với HTTPS URL của respository:
    ```
    ec2-user:~/environment $ git clone https://git-codecommit.us-east-1.amazonaws.com/v1/repos/wildrydes-site
    Cloning into 'wildrydes-site'...
    warning: You appear to have cloned an empty repository.
    ec2-user:~/environment $ 
    ```
#### Tùy chọn 2: Sử dụng GitHub.com 

1. Theo hướng dẫn của **Git Hub** để tạo repository. NOTE: Bạn không cần phải thực hiện commit trước , chỉ cần tạo repository thôi.
2. Clone repository về môi trường local sử dụng thông tin chứng thực của account GitHub của bạn.
    1. Nếu bạn không có thông tin chứng thực ở môi trường local, hoặc bạn muốn sử dụng Cloud9 cho môi trường lab này , bạn có thể xem các steps sau để [ Tạo một SSH key mới và thêm vào ssh-agent](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
    2. Thực hiện Clone repository

#### Đưa mã nguồn lên git repository
Sau khi bạn đã sử dụng AWS CodeCommit hoặc GitHub.com để tạo git repository và clone repository về môi trường local, bạn sẽ càn copy nội dụng trang web của mình từ một public S3 bucket dành cho workshop này lên repository bạn đã tạo.
Từ môi trường Cloud9 của mình ( hoặc môi trường local )
1. Thay đổi đường dẫn thư mục tới repository:
    ```
    cd wildrydes-site/
    ```
2. Copy files từ S3:
    ```
    aws s3 cp s3://wildrydes-us-east-1/WebApplication/1_StaticWebHosting/website ./ --recursive
    ```
3. Commit các files tới dịch vụ git ( bạn có thể cần điền thông tin email và username cho lệnh commit):
    ```
    $ git add .
    $ git config --global user.email "<EMAIL ADDRESS>"
    $ git config --global user.name "<USER NAME>"
    $ git commit -m "initial checkin of website code"
    $ git push
    
    Username for 'https://git-codecommit.us-east-1.amazonaws.com': wildrydes-codecommit-at-xxxxxxxxx
    Password for 'https://wildrydes-codecommit-at-xxxxxxxxx@git-codecommit.us-east-1.amazonaws.com': 
    Counting objects: 95, done.
    Compressing objects: 100% (94/94), done.
    Writing objects: 100% (95/95), 9.44 MiB | 14.87 MiB/s, done.
    Total 95 (delta 2), reused 0 (delta 0)
    To https://git-codecommit.us-east-1.amazonaws.com/v1/repos/wildrydes-site
     * [new branch]      master -> master
    ```
