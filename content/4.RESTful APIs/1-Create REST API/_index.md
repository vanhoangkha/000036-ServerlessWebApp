---
title: "1 - Create a New REST API"
date: 2020-04-18T00:39:21+07:00
---
#### Create a New REST API
Use the Amazon API Gateway console to create a new API named `WildRydes`.

1. Go to the [Amazon API Gateway Console][api-gw-console]
2. Choose **Create API**.
3. In **REST API** panel, click **Build**.
![API](/images/4.restfulapi/4.2-restapi.png?width=90pc)
4. Enter `WildRydes` for the **API Name**.
5. Select `Edge optimized` from the **Endpoint Type** dropdown.
    ***Note***: Edge optimized are best for public services being accessed from the Internet. Regional endpoints are typically used for APIs that are accessed primarily from within the same AWS Region. Private APIs are for internal services inside of an Amazon VPC.
6. Choose **Create API**
![API](/images/4.restfulapi/4.3-newapiconfig.png?width=90pc)

[amplify-console]: https://aws.amazon.com/amplify/console/
[amplify-console-console]: https://console.aws.amazon.com/amplify/home
[api-gw]: https://aws.amazon.com/api-gateway/
[api-gw-console]: https://console.aws.amazon.com/apigateway/home
[cognito-console]: https://console.aws.amazon.com/cognito/home
[cognito]: https://aws.amazon.com/cognito/
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[dynamodb]: https://aws.amazon.com/dynamodb/
[iam-console]: https://console.aws.amazon.com/iam/home
[jwt-decoder]: https://jwt.io/
[lambda-console]: https://console.aws.amazon.com/lambda/home
[lambda]: https://aws.amazon.com/lambda/