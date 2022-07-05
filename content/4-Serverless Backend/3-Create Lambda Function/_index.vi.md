---
title : "Tạo Lambda Function"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 4.3 </b> "
---

#### Tạo một Lambda Function để Xử lý các Yêu cầu

AWS Lambda sẽ chạy code của bạn để phản hồi lại các event (ví dụ như một HTTP request). Ở bước này, bạn sẽ build core function để xử lý các yêu cầu đến API từ ứng dụng web nhằm gửi đi các con kỳ lân. Trong mô-đun kế tiếp, bạn sẽ sử dụng Amazon API Gateway để tạo một RESTful API nhằm expose HTTP endpoint, nhờ đó mà chúng có thể được invoke từ trình duyệt từ phía người dùng. Sau đó bạn sẽ phải kết nối Lambda function đã tạo ở bước này với API để tạo ra một backend hoạt động với đầy đủ chức năng cho ứng dụng web của bạn.

Sử dụng AWS Lambda console để tạo một Lambda function mới với tên `RequestUnicorn` để xử lý các yêu cầu đến API. Sử dụng code function ví dụ cho sẵn ở [requestUnicorn.js](requestUnicorn.js). Bạn chỉ cần copy và paste từ tập tin vào khung soạn thảo của AWS Lambda console.

Đảm bảo rằng function của bạn được cấu hình sử dụng IAM role `WildRydesLambda` đã được tạo ở nội dung phía trước.

1. Di chuyển đến [AWS Lambda][lambda-console]
2. Chọn **Create function**.
3. Giữ lựa chọn **Author from scratch** mặc định.
4. Nhập vào khung **Name** với tên `RequestUnicorn`.
5. Chọn **Runtime** là **Node.js 10.x**.
6. Mở rộng mục *Choose or create an execution role* trong **Permissions**.
7. Chắc chăn lựa chọn `Choose an existing role` đã được chọn từ danh sách **Role**.
8. Chọn `WildRydesLambda` từ danh sách **Existing Role**.
9. Chọn vào **Create function**.
![Lambda](/images/3.backend/lambda-createfunction.png?width=90pc)
10. Kéo xuống mục **Function code** và thay nội dung code của tập tin **index.js** bằng nội dung ví dụ trong tập tin **[requestUnicorn.js](/source/requestUnicorn.js)**
```javascript
const randomBytes = require('crypto').randomBytes;

const AWS = require('aws-sdk');

const ddb = new AWS.DynamoDB.DocumentClient();

const fleet = [
    {
        Name: 'Bucephalus',
        Color: 'Golden',
        Gender: 'Male',
    },
    {
        Name: 'Shadowfax',
        Color: 'White',
        Gender: 'Male',
    },
    {
        Name: 'Rocinante',
        Color: 'Yellow',
        Gender: 'Female',
    },
];

exports.handler = (event, context, callback) => {
    if (!event.requestContext.authorizer) {
      errorResponse('Authorization not configured', context.awsRequestId, callback);
      return;
    }

    const rideId = toUrlString(randomBytes(16));
    console.log('Received event (', rideId, '): ', event);

    // Because we're using a Cognito User Pools authorizer, all of the claims
    // included in the authentication token are provided in the request context.
    // This includes the username as well as other attributes.
    const username = event.requestContext.authorizer.claims['cognito:username'];

    // The body field of the event in a proxy integration is a raw string.
    // In order to extract meaningful values, we need to first parse this string
    // into an object. A more robust implementation might inspect the Content-Type
    // header first and use a different parsing strategy based on that value.
    const requestBody = JSON.parse(event.body);

    const pickupLocation = requestBody.PickupLocation;

    const unicorn = findUnicorn(pickupLocation);

    recordRide(rideId, username, unicorn).then(() => {
        // You can use the callback function to provide a return value from your Node.js
        // Lambda functions. The first parameter is used for failed invocations. The
        // second parameter specifies the result data of the invocation.

        // Because this Lambda function is called by an API Gateway proxy integration
        // the result object must use the following structure.
        callback(null, {
            statusCode: 201,
            body: JSON.stringify({
                RideId: rideId,
                Unicorn: unicorn,
                UnicornName: unicorn.Name,
                Eta: '30 seconds',
                Rider: username,
            }),
            headers: {
                'Access-Control-Allow-Origin': '*',
            },
        });
    }).catch((err) => {
        console.error(err);

        // If there is an error during processing, catch it and return
        // from the Lambda function successfully. Specify a 500 HTTP status
        // code and provide an error message in the body. This will provide a
        // more meaningful error response to the end client.
        errorResponse(err.message, context.awsRequestId, callback)
    });
};

// This is where you would implement logic to find the optimal unicorn for
// this ride (possibly invoking another Lambda function as a microservice.)
// For simplicity, we'll just pick a unicorn at random.
function findUnicorn(pickupLocation) {
    console.log('Finding unicorn for ', pickupLocation.Latitude, ', ', pickupLocation.Longitude);
    return fleet[Math.floor(Math.random() * fleet.length)];
}

function recordRide(rideId, username, unicorn) {
    return ddb.put({
        TableName: 'Rides',
        Item: {
            RideId: rideId,
            User: username,
            Unicorn: unicorn,
            UnicornName: unicorn.Name,
            RequestTime: new Date().toISOString(),
        },
    }).promise();
}

function toUrlString(buffer) {
    return buffer.toString('base64')
        .replace(/\+/g, '-')
        .replace(/\//g, '_')
        .replace(/=/g, '');
}

function errorResponse(errorMessage, awsRequestId, callback) {
  callback(null, {
    statusCode: 500,
    body: JSON.stringify({
      Error: errorMessage,
      Reference: awsRequestId,
    }),
    headers: {
      'Access-Control-Allow-Origin': '*',
    },
  });
}

```  
![Lambda](/images/3.backend/lambda-copycode-save.png?width=90pc)
11.  Chọn **"Save"** ở phía góc phải bên trên của trang.

#### Kiểm tra kết quả thực hiện

Đối với mô-đun này, bạn sẽ kiểm tra hoạt động function mà bạn đã viết sử dụng AWS Lambda console. Trong mô-đun kế tiếp, bạn sẽ thêm một REST API với API Gateway vào để invoke function của bạn từ phía ứng dụng trên trình duyệt mà bạn đã deploy ở mô-đun đầu tiên.

1. Từ khung soạn thảo function của bạn, chọn **Configure test events** từ danh sách **Select a test event...**.
2. Giữ lựa chọn **Create new test event**.
3. Nhập vào khung **Event name** với tên `TestRequestEvent`.
4. Copy và paste test event sau vào khung soạn thảo:
    ```JSON
    {
        "path": "/ride",
        "httpMethod": "POST",
        "headers": {
            "Accept": "*/*",
            "Authorization": "Your cognito authorization , copied when you logged in to the Wild Rydes site",
            "content-type": "application/json; charset=UTF-8"
        },
        "queryStringParameters": null,
        "pathParameters": null,
        "requestContext": {
            "authorizer": {
                "claims": {
                    "cognito:username": "Your cognito user name"
                }
            }
        },
        "body": "{\"PickupLocation\":{\"Latitude\":47.6174755835663,\"Longitude\":-122.28837066650185}}"
    }
    ```
![Lambda](/images/3.backend/lambda-testevent.png?width=90pc)
5. Chọn **Create**.
6. Ở trang soạn thảo function, chọn **Test** với lựa chọn `TestRequestEvent`.  
![Lambda](/images/3.backend/lambda-clicktotest.png?width=90pc)
7. Cuộn đến đầu trang và mở rộng mục **Details** của kết quả thực thi **Execution result**.
8. Kiểm tra rằng việc thực thi đã thành công và kết quả thực thi function tương tự như bên dưới:
    ```JSON
    {
      "statusCode": 201,
      "body": "{\"RideId\":\"1h0zDZ-6KLZaEQCPyqTxeQ\",\"Unicorn\":{\"Name\":\"Shadowfax\",\"Color\":\"White\",\"Gender\":\"Male\"},\"UnicornName\":\"Shadowfax\",\"Eta\":\"30 seconds\",\"Rider\":\"the_username\"}",
      "headers": {
        "Access-Control-Allow-Origin": "*"
      }
    }
    ```
![Lambda](/images/3.backend/lambda-testsuccess.png?width=90pc)

**Chi chú:** Trường hợp bạn gặp lỗi, hãy kiểm tra lại tên bảng DynamoDB (**Rides**) và partition key (**RideId**)

#### Tóm tắt

[AWS Lambda][lambda] là một sản phẩm dịch vụ serverless function giúp bạn loại bỏ đi trở ngại về việc quản lý các máy chủ để chạy ứng dụng của bạn. Bạn sẽ cấu hình một trigger và thiết lập role để function có thể giao tiếp đến hầu hết mọi thứ mà bạn cần từ database, datastore, hay các dịch vụ khác ngay cả các dịch vụ trên internet hay trong môi trường Amazon Virtual Private Cloud (VPC) của bạn.  
[Amazon DynamoDB][dynamodb] là một non-relational serverless database có thể mở rộng tự động nhằm xử lý một số lượng cực lớn các luồng và dữ liệu mà không cần bạn phải quản lý bất kì một máy chủ nào.

Trong mô-đun này, bạn đã tạo ra một bảng DynamoDB và sau đó là một Lambda function để ghi dữ liệu vào bảng đó. Function này sẽ được đặt phía sau Amazon API Gateway ở mô-đun tiếp theo nhằm sử dụng cho việc kết nối đến ứng dụng web của bạn ghi nhận các thông tin chi tiết từ phía người dùng.

#### Kế tiếp

Sau khi bạn đã thử nghiệm thành công function mới với Lambda console, bạn có thể thực hiện tiếp mô-đun tiếp theo.

[amplify-console]: https://aws.amazon.com/amplify/console/
[cognito]: https://aws.amazon.com/cognito/
[lambda]: https://aws.amazon.com/lambda/
[api-gw]: https://aws.amazon.com/api-gateway/
[dynamodb]: https://aws.amazon.com/dynamodb/
[dynamodb-console]: https://console.aws.amazon.com/dynamodb/home
[iam-console]: https://console.aws.amazon.com/iam/home
[lambda-console]: https://console.aws.amazon.com/lambda/home