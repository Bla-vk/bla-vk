# Projects

A collection of cloud infrastructure and software projects built while transitioning into cloud engineering. The AWS projects below follow NextWork guided project formats, with each one documented in its own folder. The Terraform project is independent.

---

## ☁️ Guided AWS Projects

### Networking and VPC

#### 1. Building a Virtual Private Cloud
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/04-Building%20a%20Virtual%20Private%20Cloud)

Built a custom Amazon VPC from scratch, including defining an IPv4 CIDR block, creating public subnets with automatic public IP assignment, and attaching an Internet Gateway for outbound connectivity. Extended the project by provisioning the same VPC, subnet, and Internet Gateway setup using the AWS CLI through CloudShell, comparing console-based and command-line infrastructure workflows.

**Skills demonstrated:** Amazon VPC, CIDR block design, subnetting, Internet Gateways, AWS CLI, AWS CloudShell

---

#### 2. VPC Traffic Flow and Security
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/05-VPC%20Traffic%20Flow%20and%20Security)

Configured route tables to direct internet-bound traffic to an Internet Gateway, completing the routing layer needed to make a subnet public. Set up Security Group inbound and outbound rules to control HTTP traffic at the instance level, and implemented Network ACLs as a stateless, subnet-level layer of defense alongside them. Deployed additional VPC resources in a second AWS region (Frankfurt) and used EC2 Global View to monitor resources across regions.

**Skills demonstrated:** Route tables, Security Groups, Network ACLs, multi-region deployment, EC2 Global View

---

#### 3. Creating a Private Subnet
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/06-Creating%20a%20Private%20Subnet)

Built a dedicated private subnet within an existing VPC and gave it its own route table, separate from the VPC's main route table, to prevent any path to the internet gateway. Replaced the default Network ACL, which allows all traffic by default, with a custom deny-all NACL as a zero-trust baseline, requiring every port and protocol to be explicitly declared rather than open by default.

**Skills demonstrated:** Private subnets, route table design, Network ACLs, zero-trust security baseline

---

#### 4. Launching VPC Resources
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/07-Launching%20VPC%20resources)

Deployed a public EC2 instance into a custom VPC's public subnet with a dedicated public Security Group, and a private EC2 instance into the private subnet with a Security Group scoped to only accept SSH traffic originating from the public instance. Set up SSH key pairs for secure instance access, and used the AWS "VPC and more" quick-create feature to provision an entire VPC topology, including subnets, route tables, and NAT gateways, while meeting high-availability standards across Availability Zones.

**Skills demonstrated:** EC2 deployment, SSH key pairs, tiered Security Groups, NAT gateways, high-availability subnet design

---

#### 5. VPC Peering
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/09-VPC%20Peering)

Peered two isolated VPCs so their EC2 instances could communicate privately over the AWS backbone instead of the public internet, configuring unique CIDR blocks, a peering connection, and updated route tables on both sides. Resolved an EC2 Instance Connect failure caused by disabled auto-assign public IPs by attaching an Elastic IP, then validated the peering connection with a successful cross-VPC ping test after updating a security group to allow inbound ICMP traffic from the peer's CIDR block.

**Skills demonstrated:** VPC peering, route table configuration, Elastic IP addresses, EC2 Instance Connect, cross-VPC security group rules

---

#### 6. VPC Monitoring with Flow Logs
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/10-VPC%20Monitoring%20with%20Flow%20Logs)

Set up VPC Flow Logs to capture inbound and outbound traffic across a two-VPC peered network, creating an IAM role and custom trust policy to grant Flow Logs permission to publish to CloudWatch. Diagnosed a failed ping test by tracing it to a missing peering connection, resolved it by configuring the peering connection and route tables, then used CloudWatch Logs Insights to query flow log data, including a top-10 byte-transfer analysis by source and destination IP.

**Skills demonstrated:** VPC Flow Logs, CloudWatch, Logs Insights, IAM roles and trust policies, network traffic analysis

---

#### 7. VPC Endpoints
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/12-VPC%20Endpoints)

Set up an S3 Gateway Endpoint to move an EC2 instance's S3 traffic off the public internet and onto the AWS private network, updating the route table to direct S3-bound traffic through the endpoint. Layered a bucket policy blocking all access not routed through the specific VPC endpoint with an endpoint policy controlling which resources the endpoint could reach, then validated both allow and deny behavior by toggling the endpoint policy's Effect and confirming S3 CLI access succeeded or failed accordingly.

**Skills demonstrated:** VPC Gateway Endpoints, S3 bucket policies, endpoint policies, private AWS service connectivity, access control validation

---

### Identity, Security and Monitoring

#### 8. Cloud Security and Access Management with AWS IAM
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/03-Cloud%20Security%20with%20AWS%20IAM)

Provisioned and tagged multiple EC2 instances (production and development) and authored a JSON IAM policy restricting a simulated user to development-tagged resources only. Created IAM users, groups, and an account alias, attaching policies at the group level to enforce scoped access control. Validated the setup end to end: confirmed a restricted IAM user was denied access to the production instance while development actions succeeded, then used the IAM Policy Simulator to test and refine permission scope without disrupting live resources.

**Skills demonstrated:** AWS IAM, JSON policy authoring, least-privilege access design, IAM Policy Simulator, resource tagging

---

#### 9. Encrypt Data with AWS KMS
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/17-Encrypt%20Data%20with%20AWS%20KMS)

Created a symmetric AWS KMS key and used it to encrypt a DynamoDB table, working through key user management and the key lifecycle. Tested IAM user policies against the key to confirm who could and could not use it for encryption and decryption.

**Skills demonstrated:** AWS KMS, encryption at rest, KMS key management, IAM policies, DynamoDB

---

#### 10. Secure Secrets with Secrets Manager
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/19-%20Secure%20Secrets%20with%20Secret%20Manager)

Took a sample web app that exposed AWS credentials in its code and moved them into AWS Secrets Manager so they could be stored and retrieved securely. Used interactive Git rebase to remove the sensitive data from commit history and resolved a merge conflict along the way, making sure secrets were never left in version control.

**Skills demonstrated:** AWS Secrets Manager, credential management, Git interactive rebase, secure version control practices

---

#### 11. Build a Security Monitoring System
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/20-Build%20a%20Security%20Monitoring%20System)

Built a monitoring and alerting setup around a Secrets Manager secret: a CloudTrail trail storing logs in S3, a CloudWatch filter and alarm, and SNS notifications by email. Compared CloudTrail and CloudWatch to understand when to use each, and troubleshot a missing alert that turned out to be an alarm threshold issue rather than a delivery failure.

**Skills demonstrated:** AWS CloudTrail, CloudWatch filters and alarms, Amazon SNS, Secrets Manager, security monitoring and alerting

---

### Storage and Content Delivery

#### 12. Static Website Hosting on Amazon S3
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/02-Host%20a%20website%20on%20S3)

Deployed a static website on Amazon S3, configuring the bucket, uploading site files, and enabling static website hosting with a live public endpoint. Diagnosed a 403 Forbidden error by identifying that object-level permissions, not just bucket-level public access settings, controlled visibility, and resolved it by updating object ACLs. Extended the project with a bucket policy denying deletion of the site's index.html file, validated by confirming a blocked delete attempt.

**Skills demonstrated:** Amazon S3, static website hosting, bucket policies, ACLs, permissions troubleshooting

---

#### 13. Website Delivery with CloudFront
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/21-Website%20Delivery%20with%20CloudFront)

Served a website through Amazon CloudFront from an S3 bucket kept private using Origin Access Control and a matching bucket policy. Compared load times between CloudFront delivery and direct S3 hosting to see what a content delivery network adds.

**Skills demonstrated:** Amazon CloudFront, Origin Access Control, S3, content delivery networks, bucket policies

---

### Databases

#### 14. Aurora Database with EC2
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/13-Aurora%20Database%20with%20EC2)

Deployed a fully managed Amazon Aurora MySQL cluster designed for high availability, provisioning it alongside an EC2 instance and setting up the key pair and credentials needed to connect the two. Learned the reasoning behind Aurora's cluster architecture, which pairs a write-handling primary instance with read replicas for automatic failover and shared read workload.

**Skills demonstrated:** Amazon Aurora, relational database clusters, EC2 provisioning, high-availability database design

---

#### 15. Connect a Web App to Amazon Aurora
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/14-Connect%20a%20Web%20App%20with%20Aurora)

Built a working web application on EC2 (Apache, PHP, and the MySQL client libraries) and connected it to an Amazon Aurora database for real-time data storage and retrieval. Configured the app's database credentials via a PHP include file, wrote a PHP page that read and wrote employee records to Aurora, and validated the integration end to end by submitting data through the UI and confirming it in the database via direct SQL queries.

**Skills demonstrated:** Amazon Aurora, EC2 web hosting (Apache/PHP), SQL, database-backed application integration

---

#### 16. Load Data into DynamoDB
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/15-Load%20Data%20into%20DynamoDB)

Created multiple DynamoDB tables and loaded them with data entirely through the AWS CLI in CloudShell, working with partition and sort keys to structure each table's primary key. Explored DynamoDB's flexible, schema-less item model firsthand, noting how individual items in the same table can carry different sets of attributes, and adjusted read and write capacity settings to understand how throughput affects cost and performance.

**Skills demonstrated:** Amazon DynamoDB, NoSQL data modeling, AWS CLI/CloudShell, read/write capacity management

---

#### 17. Query Data with DynamoDB
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/16-Query%20Data%20with%20DynamoDB)

Queried DynamoDB tables by partition and sort key via the AWS CLI, working through the strict key requirements that distinguish NoSQL querying from relational SQL. Executed a multi-table transactional write that atomically added a new record to one table while updating a related counter in another, guaranteeing all-or-nothing consistency across both.

**Skills demonstrated:** DynamoDB querying, partition/sort key design, AWS CLI, transactional writes, NoSQL data modeling

---

### Serverless and Three-Tier Architecture

#### 18. APIs with Lambda and API Gateway
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/22-API%27s%20with%20Lambda%20%2B%20API%27s%20Gateway)

Built a serverless REST API with Amazon API Gateway connected to an AWS Lambda function that looks up user data in DynamoDB by user ID and returns an error message on failure. Worked through API resources, endpoints and documentation to understand the logic tier of an application without managing servers.

**Skills demonstrated:** AWS Lambda, Amazon API Gateway, REST APIs, serverless architecture, DynamoDB

---

#### 19. Fetch Data with AWS Lambda
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/23-Fetch%20Data%20with%20AWS%20Lambda)

Created a DynamoDB table (UserData, keyed on userId) and a Lambda function that retrieves items from it. Wrote a custom inline IAM policy from scratch for the function's execution role and tested the function to confirm the correct data was returned.

**Skills demonstrated:** AWS Lambda, DynamoDB, IAM execution roles, inline policies, function testing

---

#### 20. Build a Three-Tier Web App
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/24-Build%20a%20Three-Tier%20Web%20App)

Built a three-tier web application: S3 and CloudFront for the presentation tier, Lambda and API Gateway for the logic tier, and DynamoDB for the data tier. Troubleshot a 403 error and CORS issue whose real cause was a small typo in the API invoke URL, then confirmed data flowed end to end from DynamoDB through Lambda and API Gateway to the browser.

**Skills demonstrated:** Amazon S3, CloudFront, Lambda, API Gateway, DynamoDB, CORS troubleshooting

---

### Containers and Kubernetes (Amazon EKS)

#### 21. Launch a Kubernetes Cluster
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/25-Launch%20a%20Kubernetes%20Cluster)

Launched an Amazon EKS cluster and node group from the command line with eksctl, which provisions the cluster and its VPC resources through CloudFormation. Fixed an eksctl installation error and an EC2 permissions error, and created an IAM access entry to authorize access to the cluster in the EKS console.

**Skills demonstrated:** Amazon EKS, Kubernetes, eksctl, CloudFormation, IAM access entries

---

#### 22. Set Up a Kubernetes Deployment
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/26-Set%20up%20Kubernetes%20Deployment)

Prepared an application backend for Kubernetes by cloning the code from GitHub, building a Docker container image and pushing it to Amazon ECR. Set up an EC2 admin machine with eksctl and an IAM role to create the cluster.

**Skills demonstrated:** Docker, Amazon ECR, Amazon EKS, Git, container image builds

---

#### 23. Create Kubernetes Manifests
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/27-Create%20Kubernetes%20Manifests)

Wrote Kubernetes manifest files, including a Deployment and a Service, that tell the cluster how to run the containerised backend. Built on the earlier work of creating the cluster and pushing the Docker image to ECR.

**Skills demonstrated:** Kubernetes manifests, Deployments, Services, Docker, Amazon ECR

---

#### 24. Deploy a Backend with Kubernetes
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/28-Deploy%20Backend%20with%20Kubernetes)

Deployed the containerised backend to the EKS cluster using kubectl, pulling the image from ECR and applying the manifest files. Worked through how the control plane schedules containers and how worker nodes run them.

**Skills demonstrated:** kubectl, Amazon EKS, Amazon ECR, Docker, container deployment

---

### CI/CD and Infrastructure as Code

#### 25. Secure Packages with CodeArtifact
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/31-Secure%20Packages%20with%20CodeArtifact)

Set up an AWS CodeArtifact domain and repository with Maven Central as its upstream, connected Maven to it, and configured IAM permissions so an EC2 instance could access it. Resolved CLI and permission errors, then confirmed packages were being pulled into the repository.

**Skills demonstrated:** AWS CodeArtifact, Maven, IAM permissions, artifact repositories, dependency management

---

#### 26. Continuous Integration with CodeBuild
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/32-Continuous%20Integration%20with%20CodeBuild)

Automated building and testing of a Java web app with AWS CodeBuild, writing a buildspec.yml and a test script and connecting CodeBuild to GitHub through CodeConnections using a GitHub App. Worked through Git issues from the terminal and troubleshot the build until it succeeded.

**Skills demonstrated:** AWS CodeBuild, buildspec.yml, CodeConnections, continuous integration, GitHub

---

#### 27. Deploy a Web App with CodeDeploy
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/33-Deploy%20a%20Webapp%20with%20CodeDeploy)

Automated deployment of a web app with AWS CodeDeploy using an appspec.yml file and deployment scripts. Created the production EC2 and VPC environment with CloudFormation, and recovered from a failed deployment by clearing a conflicting file over SSH and redeploying.

**Skills demonstrated:** AWS CodeDeploy, appspec.yml, deployment groups, CloudFormation, deployment recovery

---

#### 28. Build a CI/CD Pipeline with AWS
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/34-Build%20a%20CICD%20pipeline%20with%20AWS)

Built an AWS CodePipeline that takes code from GitHub through CodeBuild to CodeDeploy, so pushing a change updates the live web app without manual steps. Worked with pipeline stages, execution modes, webhooks and rollbacks, and resolved permission errors during a rollback.

**Skills demonstrated:** AWS CodePipeline, CI/CD pipeline design, webhooks, rollbacks, IAM

---

#### 29. Create an S3 Bucket with Terraform
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/40-Create%20an%20S3%20Bucket%20with%20Terraform)

Installed and configured Terraform and the AWS CLI, then wrote and applied a configuration that provisioned an S3 bucket. Worked through provider plugins, the state file that tracks managed resources, and the dependency lock file that pins provider versions, and uploaded a local image to the new bucket.

**Skills demonstrated:** Terraform, Infrastructure as Code, provider plugins, state management, Amazon S3

---

## 🏗️ Independent Infrastructure as Code Project

#### 30. AWS Dev Environment with Terraform
**Repo:** [link](https://github.com/Bla-vk/terraform-aws-dev-environment)

Independent project rebuilding my manual VPC and EC2 work in Terraform. Provisioned 9 resources with one `terraform apply`: a custom VPC (`10.100.0.0/16`), a public subnet, an Internet Gateway with a default route, a security group, an SSH key pair and an Ubuntu 24.04 EC2 instance. The AMI is found with a data source rather than hardcoded, and credentials come from a named AWS profile. A `user_data` script installs Docker Engine on first boot, and a `local-exec` provisioner writes the new server into my SSH config. Verified the build with `terraform plan`, SSH access and `docker run hello-world`, then removed everything with `terraform destroy`. Documented the troubleshooting, including a failed boot script and a stale SSH entry, and noted the open security group as a known limitation to harden.

**Skills demonstrated:** Terraform, Infrastructure as Code, Amazon VPC, EC2, data sources, `user_data` and cloud-init troubleshooting, Docker installation, SSH key management, `.gitignore` hygiene for state and secrets

---

## 💻 Software Projects

#### 31. CRUD API
**Repo:** [link](https://github.com/Bla-vk/Simple-CRUD-API)

A REST API built in Python implementing full Create, Read, Update, and Delete operations.

**Skills demonstrated:** Python, REST API design, backend development

---

#### 32. Chatbot
**Repo:** [link](https://github.com/Bla-vk/Chatbot)

A conversational chatbot built in Python.

**Skills demonstrated:** Python, conversational logic

---

#### 33. Data Structures & Algorithms
**Repo:** [link](https://github.com/Bla-vk/Data_Structures_And_Algorithm-Python)

Implementations and practice solutions covering core data structures and algorithms in Python.

**Skills demonstrated:** Python, data structures, algorithmic problem solving

---

#### 34. Frontend Project
**Repo:** [link](https://github.com/Bla-vk/random_frontend_projects)

A frontend project built with HTML, CSS, and JavaScript.

**Skills demonstrated:** HTML, CSS, JavaScript

---

## 🛠️ Tech Stack

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=flat&logo=terraform&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![AWS Lambda](https://img.shields.io/badge/AWS%20Lambda-FF9900?style=flat&logo=awslambda&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
