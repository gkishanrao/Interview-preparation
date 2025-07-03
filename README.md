# Interview-preparation


# ✅ 1. How do you deploy a Java app in AWS?
Answer:

I typically use Jenkins as part of the CI/CD pipeline. The process starts by committing the latest code to AWS CodeCommit or GitHub. Jenkins picks up the code, builds the JAR file using Maven, and creates a Docker image. This image is then pushed to Amazon ECR (Elastic Container Registry). Finally, the image is pulled from ECR and deployed into Amazon EKS (Elastic Kubernetes Service). This setup enables scalable, containerized deployment in the cloud.

# ✅ 2. What is the difference between EC2 and Lambda?
Answer:

EC2 provides full control over virtual servers in the cloud. It requires manual provisioning and is ideal for long-running applications or those needing custom environments.
Lambda, on the other hand, is a serverless compute service. You only write and deploy your function code—there's no need to manage infrastructure. It's event-driven, scales automatically, and is best for lightweight, short-lived, or scheduled tasks.

# ✅ 3. How do you secure an S3 bucket?
Answer:

To secure S3 buckets:

I use IAM roles and policies to control access.

Apply bucket policies for fine-grained permissions.

Enable block public access to prevent accidental exposure.

Use server-side encryption (SSE) with AWS KMS for data at rest.

Enable logging and versioning for auditing and data protection.

Configure lifecycle policies for managing storage cost (standard, infrequent access, Glacier).

# ✅ 4. What’s the use of API Gateway?
Answer:

AWS API Gateway is used to expose RESTful APIs securely and efficiently. It allows us to:

Define and manage endpoints (GET, POST, PUT, DELETE)

Authenticate using IAM, Cognito, or API keys

Handle rate limiting, throttling, and caching

Integrate with Lambda, EC2, or backend services
It’s a powerful way to manage and scale APIs with low operational overhead.

# ✅ 5. Can you write a simple REST API to fetch a list of users?
Answer:
Yes, using Spring Boot, I would create:

@RestController to expose endpoints

@Service layer to handle business logic

@Repository layer using JPA for DB operations

A User class with @Data (Lombok) as the POJO

@Configuration class for any API setup
I would implement a basic CRUD service using /users endpoints and connect it to a PostgreSQL or in-memory database like H2.

# ✅ 6. How do you automate deployment using CI/CD?
Answer:
![image](https://github.com/user-attachments/assets/e2f5d47c-1c38-4da0-86cb-aebb87a6a791)

I use a Jenkins pipeline that:

Checks out code from Git

Runs SonarQube for code quality and test coverage

Uses Fortify or Checkmarx for static code security scanning

Builds the artifact using Maven and creates a Docker image

Pushes the image to Amazon ECR

Deploys the image to Amazon EKS
This fully automated pipeline helps ensure code quality, security, and smooth deployments.

