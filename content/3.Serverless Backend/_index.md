+++
title = "Serverless Backend"
date = 2020-04-18T00:38:32+07:00
weight = 7
chapter = true
pre = "<b>3. </b>"
+++

# Module 3: Serverless Service Backend
---
#### Overview  

* In this module you'll use [AWS Lambda][lambda] and [Amazon DynamoDB][dynamodb] to build a backend process for handling requests from your web application. The browser application that you deployed in the first module allows users to request that a unicorn be sent to a location of their choice. In order to fulfill those requests, the JavaScript running in the browser will need to invoke a service running in the cloud.
* You'll implement a Lambda function that will be invoked each time a user requests a unicorn. The function will select a unicorn from the fleet, record the request in a DynamoDB table and then respond to the front-end application with details about the unicorn being dispatched.
![Serverless Backend](/images/3.backend/3.1-architect.png?width=90pc)
* The function is invoked from the browser using [Amazon API Gateway][api-gw]. You'll implement that connection in the next module. For this module you'll just test your function in isolation. Ensure you've completed the **User Management** step before beginning this module.




[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[lambda]: https://aws.amazon.com/lambda/
[api-gw]: https://aws.amazon.com/api-gateway/
[dynamodb]: https://aws.amazon.com/dynamodb/
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[iam-console]: https://console.aws.amazon.com/iam/home
[lambda-console]: https://console.aws.amazon.com/lambda/home