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


#  ✅ 7 Explain your experience with Terraform in AWS pipelines.

I structure Terraform as reusable modules (e.g., network, eks/ecs, datastores, observability) and environment layers (envs/dev, envs/qa, envs/prod).
State & locking: Remote backend on S3 with DynamoDB table for locking. One state per stack/env (e.g., customer360/dev/network.tfstate).
Versioning: Pin terraform and provider versions in required_version and required_providers; module versions pinned via Git tags or registries.
Variables & secrets: .tfvars for env inputs (kept in repo or CI variables); secrets pulled from SSM Parameter Store/Secrets Manager at apply time.
Quality gates: terraform fmt, validate, tflint, checkov (policy/security), optional OPA/Sentinel for org guardrails.

Workflow:
init (backend + providers)
plan (outputs uploaded as CI artifact and commented on MR/PR)
Manual approval
apply with role assumption (OIDC from CI to AWS IAM)
I also schedule periodic plan against prod to detect drift and raise issues.


#  ✅ 8 What are common challenges in Terraform deployments, and how do you handle state management?

1) State management & locking
Risk: Conflicts/corruption if two applies run at once.
Mitigation: Remote state in S3 + DynamoDB locking; one state per stack/env; restricted apply permissions; applies only via CI.
2) Drift (console/manual changes)
Risk: Unexpected diffs or outages.
Mitigation: Prohibit console changes; scheduled plan to detect drift; decide to import, reconcile in code, or ignore with lifecycle { ignore_changes = [...] } (sparingly).
3) Breaking/implicit dependencies
Risk: Wrong ordering; destroy/recreate critical resources.
Mitigation: Correct references between resources; use depends_on only when necessary; split stacks (e.g., network vs apps) to reduce blast radius.

4) Provider / API quirks & version upgrades
Risk: Behavior changes on provider upgrade.
Mitigation: Pin provider versions; test upgrades in lower env; keep a changelog; use -replace for targeted fixes.

5) Imports & legacy resources
Risk: Resources created outside Terraform.
Mitigation: terraform import and then refactor into modules; verify with state show and a no-op plan.

6) Long-lived secrets & credentials
Risk: Leaked keys in code/vars.
Mitigation: Use OIDC from CI to assume IAM roles; fetch secrets from SSM/Secrets Manager at runtime; never commit secrets.

7) Large plans / slow applies

Risk: Timeouts, throttling.
Mitigation: Limit -parallelism, respect API limits, break monoliths into smaller stacks, cache provider plugins in CI.

8) Environment separation
Risk: Cross-env contamination.
Mitigation: Separate backends and buckets per env (or unique state keys), dedicated workspaces/folders, and distinct IAM roles.

9) Safety & reviews
Risk: Accidental deletes.
Mitigation: Require manual approvals, protected branches, policy-as-code (OPA/Sentinel) to block risky changes (e.g., public S3, open SGs).



#  ✅ 9 Have you integrated automated testing into CI/CD pipelines? Give an example.

When creating a feature or hotfix branch, I would make the necessary code changes and push the branch to the repository. This action triggers the Jenkins pipeline, which performs the following stages:

Static Analysis & Security Scanning
SonarQube scan for code quality, coverage, and maintainability.
Fortify scan for vulnerability and security compliance checks.

Build & Package
Build the application and Docker image using a Dockerfile.
Tag the image with the branch name or build number.

Artifact Storage
Push the built Docker image to the Amazon ECR or Google Container Registry (GCR).
Optionally push to Nexus Repository for versioned storage.

Deployment
Pull the latest image from ECR or GCR.
Deploy to Amazon EKS or Google Kubernetes Engine (GKE) using Argo CD for GitOps-driven, declarative deployments.

Validation
Run automated smoke tests and integration tests against the deployed environment to confirm functionality.


