AWS Beginner
1. What is AWS?

A cloud computing platform offering compute, storage, networking, and managed services.

2. What is EC2?

Elastic Compute Cloud — virtual servers in the cloud.

3. What is S3?

Object storage for files, backups, logs, static website hosting.

4. What is IAM?

Identity and Access Management — controls access to AWS resources.

5. What is an IAM Role vs IAM User?

User → for individuals

Role → for AWS resources (EC2, Lambda, ECS)

AWS Intermediate
6. What is VPC?

Virtual Private Cloud — isolated network for AWS resources.

7. What is an Auto Scaling Group (ASG)?

Automatically increases or decreases EC2 instances.

8. What is ELB?

Elastic Load Balancer — distributes traffic across servers.

9. Difference between ALB vs NLB?
ALB	NLB
Layer 7 HTTP	Layer 4 TCP
Path routing	High-performance low latency
Web apps	High-throughput workloads
10. What is CloudWatch?

Monitoring service for logs, metrics, alarms.

11. What is CloudTrail?

Tracks API calls in AWS (audit/security).

12. What is RDS?

Managed relational databases (MySQL, Postgres, etc.)

13. What is DynamoDB?

Fully-managed NoSQL key-value database.

14. What is AWS Lambda?

Serverless compute platform.

15. What is ECR?

Elastic Container Registry — Docker image storage.

AWS Advanced
16. What is ECS vs EKS?

ECS: AWS native container orchestration

EKS: Managed Kubernetes

17. What is S3 versioning?

Maintains multiple versions of objects for protection.

18. What is S3 lifecycle policy?

Automatically move objects to Glacier / delete old files.

19. What is Route53?

DNS service — manages domains, routing, health checks.

20. What are security groups?

Virtual firewalls controlling inbound/outbound traffic to EC2.

21. What is NACL?

Network ACL — stateless layer controlling subnet-level traffic.

22. Explain VPC Peering.

Connects two VPCs for internal communication.

23. What is Transit Gateway?

Connects multiple VPCs and on-prem networks.

24. What is CloudFormation?

Infrastructure as code service for provisioning resources.

25. What is Amazon KMS?

Key Management Service for encryption.

AWS Scenario-Based
26. Your EC2 instance is not reachable. What do you check?

Security groups

NACL

Route table

Internet gateway

Subnet type

EC2 status checks

27. How do you reduce EC2 cost?

Right-sizing

Spot instances

Savings plans

Auto scaling

28. How do you host a static website in AWS?

Upload to S3

Enable static hosting

Use CloudFront

(Optional) Route53 DNS

29. How do you secure S3 buckets?

Disable public access

Bucket policies

Encryption

Logging

IAM permissions

30. How do you deploy containers in AWS?

Options:

ECS (Fargate or EC2)

EKS

Lightsail Containers
