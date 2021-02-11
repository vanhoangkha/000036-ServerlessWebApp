---
title: "4 - Modify the site"
date: 2020-04-18T00:39:21+07:00
---

#### Modify the website
The AWS Amplify Console will rebuild and redeploy the app when it detects changes to the connected repository. Make a change to the main page to test out this process.

1. From your Cloud9 environment open the ```index.html``` file in the root directory of the repository.
2. Modify the title line:
    ```
      <title>Wild Rydes</title>
    ```
    So that it says:
    ```
      <title>Wild Rydes - Rydes of the Future!</title>
    ```
    Save the file
3. Commit again to your git repository the changes:
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
    Amplify Console will begin to build the site again soon after it notices the update to the repository. It will happen pretty quickly! Head back to the [Amplify Console console page](https://console.aws.amazon.com/amplify/home) to watch the process. 

4. Once completed, re-open the Wild Rydes site and notice the title change.
    
    ![Amplify](/images/1.staticwebsite/1.11-updatedtitle.png?width=30pc)   

#### Recap

AWS Amplify Console makes it really easy to deploy static websites following a continuous integration and delivery model. It has capabilities for "building" more complicated javascript framework based applications and can show you a preview of your application as it would rendor on popular mobile platforms.

In this module, you've created static website which will be the base for our Wild Rydes business.

#### Next

Proceed to the next module, **User Management**, wherein you'll configure Amazon Cognito User Pools to manage the users for our application.

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
