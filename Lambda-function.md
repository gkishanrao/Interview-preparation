#   1. What is AWS Lambda?
AWS Lambda is a serverless compute service that runs your code in response to events and automatically manages the underlying resources.

 ✅  2. What triggers a Lambda function?
Lambda can be triggered by:

• S3 (e.g., file upload)

• API Gateway (for web APIs)

• CloudWatch Events or EventBridge

• DynamoDB Streams

• SNS/SQS

• Step Functions


# ✅ 3. What is the difference between synchronous and asynchronous invocation?
Synchronous: Caller waits for result (e.g., API Gateway).

Asynchronous: Lambda queues and processes later (e.g., S3, SNS).

# ✅ 4. Can you invoke a Lambda function manually?
There are many ways we can invoke a lambda function manually:

• AWS Console

• AWS CLI

• SDKs

• Test events
