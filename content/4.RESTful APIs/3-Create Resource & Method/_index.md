---
title: "3 - Create Resource & Method"
date: 2020-04-18T00:39:21+07:00
---

#### Create a new resource and method
Create a new resource called /ride within your API. Then create a POST method for that resource and configure it to use a Lambda proxy integration backed by the RequestUnicorn function you created in the first step of this module.

1. In the left nav, click on **Resources** under your WildRydes API.
2. From the **Actions** dropdown select **Create Resource**.
![API](/images/4.restfulapi/4.9-createresource.png?width=90pc)
3. Enter `ride` as the **Resource Name**.
4. Ensure the **Resource Path** is set to `ride`.
5. Select **Enable API Gateway CORS** for the resource.
6. Click **Create Resource**.
![API](/images/4.restfulapi/4.10-clickcreateresource.png?width=90pc)
7. With the newly created `/ride` resource selected, from the **Action** dropdown select **Create Method**.
![API](/images/4.restfulapi/4.11-method.png?width=90pc)
8. Select `POST` from the new dropdown that appears, then **click the checkmark**.
![API](/images/4.restfulapi/4.12-post.png?width=90pc)
![API](/images/4.restfulapi/4.13-checkmark.png?width=90pc)
9.  Select **Lambda Function** for the integration type.
10. Check the box for **Use Lambda Proxy integration**.
11. Select the Region you are using for **Lambda Region**.
12. Enter the name of the function you created in the previous module, `RequestUnicorn`, for **Lambda Function**.
13. Choose **Save**. Please note, if you get an error that you function does not exist, check that the region you selected matches the one you used in the previous module.
![API](/images/4.restfulapi/4.14-done.png?width=90pc)
14. When prompted to give Amazon API Gateway permission to invoke your function, choose **OK**.
![API](/images/4.restfulapi/4.15-promptok.png?width=90pc)
15. Choose on the **Method Request** card.
![API](/images/4.restfulapi/4.16-methodrequest.png?width=90pc)
16. Choose the pencil icon next to **Authorization**.
17. Select the WildRydes Cognito user pool authorizer from the drop-down list, and click the checkmark icon.
![API](/images/4.restfulapi/4.17-select.png?width=90pc)