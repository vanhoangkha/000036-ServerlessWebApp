---
title : "Create Git repository"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---
#### Create the git repository
You have two options to manage the source code for this module:

* **AWS CodeCommit**- CodeCommit access is included in the **AWS Free Tier**.
* **GitHub.com** - If you're more comfortable with GitHub.com and already have an account.

#### Option 1: Using AWS CodeCommit

The AWS Cloud9 development environment comes with AWS managed temporary credentials that are associated with your IAM user. You use these credentials with the AWS CLI credential helper. Enable the credential helper by running the following two commands in the terminal of your Cloud9 environment.

```bash
git config --global credential.helper '!aws codecommit credential-helper $@'
git config --global credential.UseHttpPath true
```

Next you need to create the repository and clone it to your Cloud9 environment:
1. Open the **AWS CodeCommit console**
2. Select **Create Repository**
![Code Commit](/images/1.staticwebsite/1.4-codecommit.png?width=90pc) 
3. Set the *Repository name** to "wildrydes-site"
4. Select **Create**
5. From the *Clone URL* drop down, select *Clone HTTPS*
![Code Commit](/images/1.staticwebsite/1.5-codecommit.png?width=90pc) 
Now from your Cloud9 development environment:
1. From a terminal window run `git clone` and the HTTPS URL of the respository:
    ```
    ec2-user:~/environment $ git clone https://git-codecommit.us-east-1.amazonaws.com/v1/repos/wildrydes-site
    Cloning into 'wildrydes-site'...
    warning: You appear to have cloned an empty repository.
    ec2-user:~/environment $ 
    ```
#### Option 2: Using GitHub.com 

1. Follow the instructions on **Git Hub** to create a repository. NOTE: You should not create a first commit, just create the repository.
2. Clone the repository locally using your GitHub credentials
    1. If you do not have credentially locally, or want to use Cloud9 for today's lab, follow these steps to [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
    2. Clone the repository

#### Populate the git repository
Once you've used either AWS CodeCommit or GitHub.com to create your git repository and clone it locally, you'll need to copy the web site content from an existing publicly accessible S3 bucket associated with this workshop and add the content to your repository.

From your Cloud9 development environment(or local environment)
1. Change directory into your repository:
    ```
    cd wildrydes-site/
    ```
2. Copy the files from S3:
    ```
    aws s3 cp s3://wildrydes-us-east-1/WebApplication/1_StaticWebHosting/website ./ --recursive
    ```
3. Commit the files to your git service (you might need to enter an email and user name for the commit):
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
