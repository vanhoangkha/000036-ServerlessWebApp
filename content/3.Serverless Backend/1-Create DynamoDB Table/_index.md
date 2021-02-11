---
title: "1 - Create DynamoDB Table"
date: 2020-04-18T00:39:21+07:00
---
####  Create an Amazon DynamoDB Table

Use the Amazon DynamoDB console to create a new DynamoDB table. Call your table `Rides` and give it a partition key called `RideId` with type String. The table name and partition key are case sensitive. Make sure you use the exact IDs provided. Use the defaults for all other settings.

After you've created the table, note the ARN for use in the next step.

1. Go to the [Amazon DynamoDB Console][dynamodb-console]
1. Choose **Create table**.
1. Enter `Rides` for the **Table name**. This field is case sensitive.
1. Enter `RideId` for the **Partition key** and select **String** for the key type. This field is case sensitive.
1. Check the **Use default settings** box and choose **Create**
2. Scroll to the bottom of the Overview section of your new table and note the **ARN**. You will use this in the next section.


**Note**: Double check your DynamoDB table name (**Rides**) and partition key (**RideId**) before moving to next step.
![DynamoDB](/images/3.backend/dynamodb-verify.png?width=90pc)    

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[lambda]: https://aws.amazon.com/lambda/
[api-gw]: https://aws.amazon.com/api-gateway/
[dynamodb]: https://aws.amazon.com/dynamodb/
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[iam-console]: https://console.aws.amazon.com/iam/home
[lambda-console]: https://console.aws.amazon.com/lambda/home