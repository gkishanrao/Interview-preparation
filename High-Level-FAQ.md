# ✅ 1. Explain your experience developing and deploying applications on AWS.

I developed Spring Boot microservices using an event-driven architecture, leveraging Spring Cloud, Service Registry, circuit breaker patterns, and Resilience4J for fault tolerance. For distributed transactions, I implemented the SAGA design pattern to ensure data consistency across services.

The CI/CD pipeline was built with AWS CodeBuild, which compiled and containerized the services into Docker images. These images were pushed to Amazon ECR and deployed on Amazon ECS with Fargate, enabling serverless container orchestration without the need to manage EC2 instances. This approach provided scalability, reduced operational overhead, and improved deployment speed.

 #  ✅ 2. Which AWS services have you used for building APIs? Walk through the architecture.

For API development, we used Amazon API Gateway to manage and route requests. Security was implemented using JWT tokens, AWS Secrets Manager for storing credentials, AWS WAF for protection against web attacks, Security Groups for instance-level control, and Network ACLs for subnet-level control. The APIs integrated with backend microservices running on ECS/Fargate, and authentication/authorization was handled using Amazon Cognito (when applicable) or custom JWT validation. Logs and metrics were sent to CloudWatch for monitoring and troubleshooting.

#  ✅ 3. How would you deploy a serverless application in AWS? Which services would you choose and why?

For serverless applications, I would typically choose AWS Lambda combined with API Gateway for event-driven workloads that require minimal infrastructure management. However, for containerized workloads, I use ECS with Fargate as it eliminates the need to manage EC2 instances, automates scaling, and optimizes cost. It also integrates seamlessly with AWS services like CloudWatch, Secrets Manager, and ALB. Compared to EKS, ECS/Fargate requires less configuration overhead and offers simpler deployments for small to medium workloads.

#  ✅ 4. Can you describe your approach to application monitoring and performance tuning in AWS?

We leverage Spring Boot Actuator for exposing application health and metrics, combined with ELK Stack or Prometheus + Grafana for centralized logging and visualization. On the AWS side, we use CloudWatch for metrics, logs, and custom dashboards, as well as CloudWatch Alarms for proactive alerts. We also implement X-Ray for distributed tracing in microservices and use CloudTrail for auditing AWS API calls. Performance tuning involves optimizing container resource allocation, analyzing CloudWatch metrics, and profiling application performance using AWS X-Ray and custom logs.
 
#  ✅ 5 AWS Cloud Development & Deployment

Designed and developed Spring Boot microservices with event-driven architecture using Spring Cloud, Service Registry, circuit breaker patterns, and Resilience4J for fault tolerance.
Implemented SAGA design pattern for distributed transaction management, ensuring data consistency across microservices.
Built CI/CD pipelines using AWS CodeBuild, integrated with Docker to create container images, and pushed them to Amazon ECR.
Deployed services to Amazon ECS with Fargate, enabling serverless container orchestration without managing EC2 infrastructure.
Achieved improved scalability, reduced operational overhead, and faster deployment cycles through automation and AWS-native services.


#  ✅ 6 Programming & Scripting: Python, Bash, Shell Script

When to use Python boto3

I use Python boto3 when automation requires logic, conditions, loops, or integration with other systems.
Example: A Lambda function that scans for unused EBS volumes older than 30 days, deletes them, and sends a notification to SNS.
Why: boto3 allows programmatic control, error handling, and reusability, making it ideal for scheduled jobs, event-driven automation, and complex workflows.

When to use AWS CLI
I use AWS CLI for quick, ad-hoc commands or simple shell-based automation.
Example: Running aws s3 sync to replicate data between buckets or aws ec2 stop-instances for a specific environment.
Why: It’s lightweight, fast to execute, and perfect for one-off tasks or integrating simple steps into CI/CD pipelines.

