---
title : "User Pool Authorizer"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 5.2 </b> "
---

#### Create a Cognito User Pools Authorizer

Amazon API Gateway can use the JWT tokens returned by Cognito User Pools to authenticate API calls. In this step you'll configure an authorizer for your API to use the user pool you created in **User Management**.

In the Amazon API Gateway console, create a new Cognito user pool authorizer for your API. Configure it with the details of the user pool that you created in the previous module. You can test the configuration in the console by copying and pasting the auth token presented to you after you log in via the /signin.html page of your current website.

1. Under your newly created API, choose **Authorizers**.
2. Choose **Create New Authorizer**.
![API](/images/4.restfulapi/4.4-createnewauthorizer.png?width=90pc)
3. Enter `WildRydes` for the Authorizer name.
4. Select **Cognito** for the type.
5. In the Region drop-down under **Cognito User Pool**, select the Region where you created your Cognito user pool in the User Management module (by default the current region should be selected).
6. Enter `WildRydes` (or the name you gave your user pool) in the **Cognito User Pool** input.
7. Enter `Authorization` for the **Token Source**.
8. Choose **Create**.
![API](/images/4.restfulapi/4.5-authorizer.png?width=90pc)

#### Verify your authorizer configuration

1. Open a new browser tab and visit `/ride.html` under your website's domain.
2. If you are redirected to the sign-in page, sign in with the user you created in the last module. You will be redirected back to `/ride.html`.
3. Copy the auth token from the notification on the `/ride.html`.
![API](/images/4.restfulapi/4.6-successauthen.png?width=90pc)
4. Go back to previous tab where you have just finished creating the Authorizer.
5. Click **Test** at the bottom of the card for the authorizer.
![API](/images/4.restfulapi/4.7-testauthen.png?width=90pc)
6. Paste the auth token into the **Authorization Token** field in the popup dialog.
![API](/images/4.restfulapi/4.8-testauthen2.png?width=90pc)

7. Click **Test** button and verify that the response code is 200 and that you see the claims for your user displayed.