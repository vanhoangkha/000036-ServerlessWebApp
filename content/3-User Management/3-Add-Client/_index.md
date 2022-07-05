---
title : "Add Client to User Pool"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3.3 </b> "
---

#### Add an App Client to Your User Pool

From the Amazon Cognito console select your user pool and then select the **App clients** section. Add a new app and make sure the Generate client secret option is deselected. Client secrets aren't supported with the JavaScript SDK. If you do create an app with a generated secret, delete it and create a new one with the correct configuration.


1. From the Pool Details page for your user pool, select **App clients** from the **General settings** section in the left navigation bar.
2. Choose **Add an app client**.
3. Give the app client a name such as `WildRydesWebApp`.
4. **Uncheck** the Generate client secret option. Client secrets aren't supported for use with browser-based applications.
5. Choose **Create app client**.
![Authentication](/images/2.authentication/2.6-appclient.png?width=90pc)
6. Note the **App client id** for the newly created application.
![Authentication](/images/2.authentication/2.7-appclientid.png?width=90pc)

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[cognito-console]: https://console.aws.amazon.com/cognito/home
[jwt-decoder]: https://jwt.io/