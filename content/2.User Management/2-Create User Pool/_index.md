---
title: "2 - Create User Pool"
date: 2020-04-18T00:39:21+07:00
---

####  Create an Amazon Cognito User Pool

Amazon Cognito provides two different mechanisms for authenticating users. You can use Cognito User Pools to add sign-up and sign-in functionality to your application or use Cognito Identity Pools to authenticate users through social identity providers such as Facebook, Twitter, or Amazon, with SAML identity solutions, or by using your own identity system. For this module you'll use a user pool as the backend for the provided registration and sign-in pages.

Use the Amazon Cognito console to create a new user pool using the default settings. Once your pool is created, note the Pool Id. You'll use this value in a later section.

1. Go to the [Amazon Cognito Console][cognito-console]
![Authentication](/images/2.authentication/2.2-cognito.png?width=90pc)
2. Choose **Manage your User Pools**.
3. Choose **Create a User Pool**
4. Provide a name for your user pool such as `WildRydes`, then select **Review Defaults**
![Authentication](/images/2.authentication/2.3-poolname.png?width=90pc)
5. On the review page, click **Create pool**.
![Authentication](/images/2.authentication/2.4-createpool.png?width=90pc)
6. Note the **Pool Id** on the Pool details page of your newly created user pool.
![Authentication](/images/2.authentication/2.5-poolid.png?width=90pc)

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[cognito-console]: https://console.aws.amazon.com/cognito/home
[jwt-decoder]: https://jwt.io/