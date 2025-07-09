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


 ✅ 3. What is the difference between synchronous and asynchronous invocation?
      Synchronous: Caller waits for result (e.g., API Gateway).
      
      Asynchronous: Lambda queues and processes later (e.g., S3, SNS).

 ✅ 4. Can you invoke a Lambda function manually?
   There are many ways we can invoke a lambda function manually:
   
         • AWS Console
         
         • AWS CLI
         
         • SDKs
         
         • Test events


  ✅ 5. What are the benefits of using AWS Lambda?
  
	•	No server management
 
	•	Scales automatically
 
	•	Pay only for usage (per ms)
 
	•	Event-driven execution
 
	•	Easy integration with other AWS services
 
  ✅6.	 How does Lambda pricing work?
 
	•	Requests: First 1M requests/month are free
 
	•	Duration: Based on execution time in GB-seconds
 
               Example: 128MB function that runs for 1 second = 0.000000208 USD

  ✅7. What languages does Lambda support?
  
	        # Node.js, Python, Java, Go, Ruby, .NET (C#), and custom runtimes using Docker
         
	 ✅8	What is the maximum execution timeout for a Lambda function?
  
	         •	15 minutes (900 seconds)
          
 ✅9.	What is the memory range supported by Lambda?
 
	•	128 MB to 10,240 MB (10 GB)
 
 ✅10.	How do you trigger a Lambda function?
 
	•	Through services like API Gateway, S3, CloudWatch Events, DynamoDB Streams, SNS, SQS, and more.
 
 ✅11.	What is a cold start in Lambda?
 
              It’s the initial startup time when Lambda creates a new container to run your function. This may cause latency.
              
 ✅12.	What is a warm start?
 
                 A warm start happens when AWS reuses an already initialized container, resulting in faster execution.
                 
 ✅13.	How can you reduce cold starts?
 
            	•	Use Provisioned Concurrency
            	•	Keep dependencies minimal
            	•	Optimize initialization code

⸻

🔹 Advanced/Technical (11–25)
	11.	How do environment variables work in Lambda?
You can configure key-value pairs that are accessible through the runtime (e.g., System.getenv("MY_ENV") in Java).
	12.	What is the role of the Lambda handler function?
It’s the entry point that AWS invokes to start executing your logic.
Example in Python:
[8:55 am, 9/7/2025] Kishan: def lambda_handler(event, context):
    return "Hello World"



    13.	How do you monitor Lambda functions?
	•	Use Amazon CloudWatch Logs, Metrics, and Alarms
	•	View invocation counts, errors, duration, etc.
	14.	What is concurrency in Lambda?
	•	Refers to the number of executions running at the same time
	•	Default quota: 1,000 concurrent executions per account
	15.	What is Provisioned Concurrency?
It pre-warms a set number of instances, ensuring consistent performance by avoiding cold starts.
	16.	Can Lambda functions access a VPC?
Yes. You can configure a Lambda function to connect to private resources in a VPC, such as RDS or EC2.
	17.	What’s the difference between synchronous and asynchronous invocation?
	•	Synchronous: Caller waits for response (e.g., API Gateway)
	•	Asynchronous: Caller doesn’t wait (e.g., S3 events, SNS)
	18.	What is the Lambda execution role?
An IAM role that grants your function permissions to access AWS resources (e.g., S3 read/write, CloudWatch logging)
	19.	What happens when a Lambda function fails?
	•	Synchronous: Error returned to caller
	•	Asynchronous: Retries automatically
	•	Use DLQ (Dead Letter Queue) or Lambda Destinations to capture failed events
	20.	Can you version a Lambda function?
Yes. Lambda supports versioning and aliases for deployment strategies like blue/green deployment.
	21.	How do you deploy a Lambda function?
	•	Via AWS Console, CLI, SDK
	•	Use AWS SAM, Serverless Framework, Terraform, etc.
	22.	How can Lambda functions be packaged?
	•	As a .zip file with code and dependencies
	•	As a container image (up to 10GB) for custom runtimes
	23.	What is Lambda@Edge?
Run Lambda functions closer to users using CloudFront, for low-latency processing at the edge.
	24.	What is the maximum Lambda payload size?
	•	Request/response (synchronous): 6 MB
	•	Event payload (async): 256 KB
	•	With API Gateway: 10 MB
	25.	How do you test Lambda functions locally?
Use tools like AWS SAM CLI (sam local invoke) or Docker-based emulators.
