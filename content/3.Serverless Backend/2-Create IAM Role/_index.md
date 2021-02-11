---
title: "2 - Create IAM Role"
date: 2020-04-18T00:39:21+07:00
---
#### Create an IAM Role for Your Lambda function

Every Lambda function has an IAM role associated with it. This role defines what other AWS services the function is allowed to interact with. For the purposes of this workshop, you'll need to create an IAM role that grants your Lambda function permission to write logs to Amazon CloudWatch Logs and access to write items to your DynamoDB table.

Use the IAM console to create a new role. Name it `WildRydesLambda` and select AWS Lambda for the role type. You'll need to attach policies that grant your function permissions to write to Amazon CloudWatch Logs and put items to your DynamoDB table.

Attach the managed policy called `AWSLambdaBasicExecutionRole` to this role to grant the necessary CloudWatch Logs permissions. Also, create a custom inline policy for your role that allows the `ddb:PutItem` action for the table you created in the previous section.

1. Go to the [AWS IAM Console][iam-console]
2. Select **Roles** in the left navigation bar and then choose **Create role**.
![IAM](/images/3.backend/iam-createrole.png?width=90pc)    
 
3. Select **Lambda** for the role type from the **AWS service** group, then click **Next: Permissions**
    **Note:** Selecting a role type automatically creates a trust policy for your role that allows AWS services to assume this role on your behalf. If you were creating this role using the CLI, AWS CloudFormation or another mechanism, you would specify a trust policy directly.
![IAM](/images/3.backend/iam-chooselambda.png?width=90pc)    
4. Begin typing `AWSLambdaBasicExecutionRole` in the **Filter** text box and check the box next to that role.
5. Click **Next: Tags**. Add any tags that you wish.
6. Click **Next: Review**.
7. Enter `WildRydesLambda` for the **Role name**.
8. Choose **Create role**. 
![IAM](/images/3.backend/iam-rolecreated.png?width=90pc)  

#### Add DynamoDB permission.
Next you need to add permissions to the role so that it can access your DynamoDB table.

1. While in the IAM Console on the roles page type `WildRydesLambda` into the filter box on the Roles page and choose the role you just created.
1. On the Permissions tab, choose the **Add inline policy** link in the lower right corner to create a new inline policy.
![IAM](/images/3.backend/iam-addpolicy.png?width=90pc)  
1. Select **Choose a service**.
2. Begin typing `DynamoDB` into the search box labeled **Find a service** and select **DynamoDB** when it appears.
3. Ubder **Access Level** click **Write** drop down menu.
4. Check the box next to **PutItem** when it appears.
![IAM](/images/3.backend/iam-addpolicy-putitem.png?width=90pc)
5. Select the **Resources** section.
6. With the **Specific** option selected, choose the Add ARN link in the **table** section.
![IAM](/images/3.backend/iam-addpolicy-putitem-addarn.png?width=90pc)
7. Paste the ARN of the table you created in the previous section in the **Specify ARN for table** field, and choose **Add**.
![IAM](/images/3.backend/iam-addarncomplete.png?width=90pc)
8. Choose **Review Policy**.
9.  Enter `DynamoDBWriteAccess` for the policy name and choose **Create policy**.
![IAM](/images/3.backend/iam-namingthepolicy.png?width=90pc)


[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[lambda]: https://aws.amazon.com/lambda/
[api-gw]: https://aws.amazon.com/api-gateway/
[dynamodb]: https://aws.amazon.com/dynamodb/
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[iam-console]: https://console.aws.amazon.com/iam/home
[lambda-console]: https://console.aws.amazon.com/lambda/home