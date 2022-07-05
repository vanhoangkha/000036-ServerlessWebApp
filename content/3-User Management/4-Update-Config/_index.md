---
title : "Update the config.js"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 3.4 </b> "
---

#### Update the config.js File in Your Website

The **/js/config.js** file contains settings for the user pool ID, app client ID and Region. Update this file with the settings from the user pool and app you created in the previous steps and commit the file back to your git repository.


1. On your Cloud9 development environment open `js/config.js`
2. Update the `cognito` section with the correct values for the user pool and app you just created.
    You can find the value for `userPoolId` on the Pool details page of the Amazon Cognito console after you select the user pool that you created.

    ![Authentication](/images/2.authentication/pool-id.png?width=90pc)

    You can find the value for `userPoolClientId` by selecting **App clients** from the left navigation bar. Use the value from the **App client id** field for the app you created in the previous section.

    ![Authentication](/images/2.authentication/client-id.png?width=90pc)

    The value for `region` should be the AWS Region code where you created your user pool. E.g. `us-east-1` for the N. Virginia Region, or `us-west-2` for the Oregon Region. If you're not sure which code to use, you can look at the Pool ARN value on the Pool details page. The Region code is the part of the ARN immediately after `arn:aws:cognito-idp:`.

    The updated config.js file should look like this. Note that the actual values for your file will be different:
    ![Authentication](/images/2.authentication/2.8-configjs.png?width=90pc)

3. Save the modified file making sure the filename is still `config.js`.
4. Commit the changes to your git repository:
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

    Amplify Console should pick up the changes and begin building and deploying your web application.

**Note:** Instead of having you write the browser-side code for managing the registration, verification, and sign in flows, we provide a working implementation in the assets you deployed in the first module. The **cognito-auth.js**(/js/cognito-auth.js) file contains the code that handles UI events and invokes the appropriate Amazon Cognito Identity SDK methods. For more information about the SDK, see the [project page on GitHub](https://github.com/aws/amazon-cognito-identity-js).

#### Implementation Validation

1. Visit `/register.html` under your website domain, or choose the **Giddy Up!** button on the homepage of your site.
1. Complete the registration form and choose **Let's Ryde**. You can use your own email or enter a fake email. Make sure to choose a password that contains at least one upper-case letter, a number, and a special character. Don't forget the password you entered for later. You should see an alert that confirms that your user has been created.
![Authentication](/images/2.authentication/2.9-register.png?width=90pc)
1. Confirm your new user using one of the two following methods.
  1. If you used an email address you control, you can complete the account verification process by visiting `/verify.html` under your website domain and entering the verification code that is emailed to you. Please note, the verification email may end up in your spam folder. For real deployments we recommend [configuring your user pool to use Amazon Simple Email Service](http://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pool-settings-message-customizations.html#cognito-user-pool-settings-ses-authorization-to-send-email) to send emails from a domain you own.
![Authentication](/images/2.authentication/2.10-verify.png?width=90pc)
1. If you used a dummy email address, you must confirm the user manually through the Cognito console.

    1. From the AWS console, click Services then select **Cognito** under Security, Identity & Compliance.
    1. Choose **Manage your User Pools**
    1. Select the `WildRydes` user pool and click **Users and groups** in the left navigation bar.
    1. You should see a user corresponding to the email address that you submitted through the registration page. Choose that username to view the user detail page.
    1. Choose **Confirm user** to finalize the account creation process.

1. After confirming the new user using either the `/verify.html` page or the Cognito console, visit `/signin.html` and log in using the email address and password you entered during the registration step.

1. If successful you should be redirected to `/ride.html`. You should see a notification that the API is not configured.

![Authentication](/images/2.authentication/2.11-loginsuccess.png?width=90pc)

#### Recap

**Amazon Cognito** provides two different capabilities for managing users, federated identities and user pools. [Amazon Cognito][cognito] user pools can handle almost every aspect about managing users, their login credentials, handling password resets, multifactor authentication and much more!

In this module you've used user pools to create a completely hosted and managed user management system that will allow us to authenticate your users and manage their user information. From there you've updated the website to use the user pool and utlized the AWS SDKs to provide a signin form on the site.

#### Extra

* Try copying the **auth_token** you've received and paste that into an [online JWT Decoder][jwt-decoder] to understand what this token means for your application
![Authentication](/images/2.authentication/2.12-jwt.png?width=90pc)

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[cognito-console]: https://console.aws.amazon.com/cognito/home
[jwt-decoder]: https://jwt.io/