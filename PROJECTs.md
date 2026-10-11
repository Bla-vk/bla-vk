# Projects

A collection of cloud infrastructure and software projects built while transitioning into cloud engineering.

---

## ☁️ Cloud & AWS Projects

### 1. Building a Virtual Private Cloud on AWS
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Building%20a%20Virtual%20Private%20Cloud)

Built a custom Amazon VPC from scratch, including defining an IPv4 CIDR block, creating public subnets with automatic public IP assignment, and attaching an Internet Gateway for outbound connectivity. Extended the project by provisioning the same VPC, subnet, and Internet Gateway setup using the AWS CLI through CloudShell, comparing console-based and command-line infrastructure workflows.

**Skills demonstrated:** Amazon VPC, CIDR block design, subnetting, Internet Gateways, AWS CLI, AWS CloudShell

---

### 2. VPC Traffic Flow and Security
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/VPC%20Traffic%20Flow%20and%20Security)

Configured route tables to direct internet-bound traffic to an Internet Gateway, completing the routing layer needed to make a subnet public. Set up Security Group inbound/outbound rules to control HTTP traffic at the instance level, and implemented Network ACLs as a stateless, subnet-level layer of defense alongside them. Deployed additional VPC resources in a second AWS region (Frankfurt) and used EC2 Global View to monitor resources across regions.

**Skills demonstrated:** Route tables, Security Groups, Network ACLs, multi-region deployment, EC2 Global View

---

### 3. Static Website Hosting on Amazon S3
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Host%20a%20website%20on%20S3)

Deployed a static website on Amazon S3, configuring the bucket, uploading site files, and enabling static website hosting with a live public endpoint. Diagnosed a 403 Forbidden error by identifying that object-level permissions, not just bucket-level public access settings, controlled visibility, and resolved it by updating object ACLs. Extended the project with a bucket policy denying deletion of the site's index.html file, validated by confirming a blocked delete attempt.

**Skills demonstrated:** Amazon S3, static website hosting, bucket policies, ACLs, permissions troubleshooting

---

### 4. Cloud Security & Access Management with AWS IAM
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Cloud%20Security%20with%20AWS%20IAM)

Provisioned and tagged multiple EC2 instances (production and development) and authored a JSON IAM policy restricting a simulated user to development-tagged resources only. Created IAM users, groups, and an account alias, attaching policies at the group level to enforce scoped access control. Validated the setup end to end: confirmed a restricted IAM user was denied access to the production instance while development actions succeeded, then used the IAM Policy Simulator to test and refine permission scope without disrupting live resources.

**Skills demonstrated:** AWS IAM, JSON policy authoring, least-privilege access design, IAM Policy Simulator, resource tagging

---

### 5. Creating a Private Subnet
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Creating%20a%20Private%20Subnet)

Built a dedicated private subnet within an existing VPC and gave it its own route table, separate from the VPC's main route table, to prevent any path to the internet gateway. Replaced the default Network ACL, which allows all traffic by default, with a custom deny-all NACL as a zero-trust baseline, requiring every port and protocol to be explicitly declared rather than open by default.

**Skills demonstrated:** Private subnets, route table design, Network ACLs, zero-trust security baseline

---

### 6. Launching VPC Resources
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Launching%20VPC%20Resources)

Deployed a public EC2 instance into a custom VPC's public subnet with a dedicated public Security Group, and a private EC2 instance into the private subnet with a Security Group scoped to only accept SSH traffic originating from the public instance. Set up SSH key pairs for secure instance access, and used the AWS "VPC and more" quick-create feature to provision an entire VPC topology, including subnets, route tables, and NAT gateways, in minutes while meeting high-availability standards across Availability Zones.

**Skills demonstrated:** EC2 deployment, SSH key pairs, tiered Security Groups, NAT gateways, high-availability subnet design

---

### 7. Testing VPC Connectivity
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Testing%20VPC%20Connectivity)

Tested and troubleshot connectivity between EC2 instances in public and private subnets, using EC2 Instance Connect, ping, and curl to diagnose issues. Resolved a blocked SSH connection by adding a missing Security Group inbound rule, and restored instance-to-instance connectivity by adding the correct Network ACL and Security Group rules for ICMP traffic.

**Skills demonstrated:** Network troubleshooting, EC2 Instance Connect, Security Groups, Network ACLs, ping/curl diagnostics

---

### 8. VPC Peering
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/VPC%20Peering)

Peered two isolated VPCs (NextWork-1 and NextWork-2) so their EC2 instances could communicate privately over the AWS backbone instead of the public internet, configuring unique CIDR blocks, a peering connection, and updated route tables on both sides. Resolved an EC2 Instance Connect failure caused by disabled auto-assign public IPs by attaching an Elastic IP, then validated the peering connection with a successful cross-VPC ping test after updating a security group to allow inbound ICMP traffic from the peer's CIDR block.

**Skills demonstrated:** VPC peering, route table configuration, Elastic IP addresses, EC2 Instance Connect, cross-VPC security group rules

---

### 9. VPC Monitoring with Flow Logs
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/VPC%20Monitoring%20with%20Flow%20Logs)

Set up VPC Flow Logs to capture all inbound and outbound traffic across a two-VPC peered network, creating an IAM role and custom trust policy to grant Flow Logs permission to publish to CloudWatch. Diagnosed a failed ping test by tracing it to a missing peering connection, resolved it by configuring the peering connection and route tables, then used CloudWatch Logs Insights to query flow log data, including a top-10 byte-transfer analysis by source and destination IP.

**Skills demonstrated:** VPC Flow Logs, CloudWatch, Logs Insights, IAM roles and trust policies, network traffic analysis

---

### 10. Access S3 from a VPC
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Access%20S3%20from%20a%20VPC)

Launched an EC2 instance into a custom VPC and configured it to interact with an S3 bucket using the AWS CLI, setting up access keys (access key ID, secret access key, region, and output format) to authenticate the instance. Ran CLI commands to list buckets, list bucket contents, and upload a new file, validating each step's success, while noting that an IAM role with least-privilege permissions is the recommended best practice over long-lived access keys.

**Skills demonstrated:** AWS CLI, IAM access keys, S3 bucket operations, EC2-to-S3 connectivity, least-privilege best practices

---

### 11. VPC Endpoints
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/VPC%20Endpoints)

Set up an S3 Gateway Endpoint to move an EC2 instance's S3 traffic off the public internet and onto the AWS private network, updating the public subnet's route table to direct S3-bound traffic through the endpoint. Layered a bucket policy blocking all access not routed through the specific VPC endpoint with an endpoint policy controlling which resources the endpoint could reach, then validated both allow and deny behavior by toggling the endpoint policy's Effect and confirming S3 CLI access succeeded or failed accordingly.

**Skills demonstrated:** VPC Gateway Endpoints, S3 bucket policies, endpoint policies, private AWS service connectivity, access control validation

---

### 12. Aurora Database with EC2
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Aurora%20Database%20with%20EC2)

Deployed a fully managed Amazon Aurora MySQL cluster designed for high availability, provisioning it alongside an EC2 instance and setting up the key pair and credentials needed to connect the two. Learned the reasoning behind Aurora's cluster architecture, which pairs a write-handling primary instance with read replicas for automatic failover and shared read workload.

**Skills demonstrated:** Amazon Aurora, relational database clusters, EC2 provisioning, high-availability database design

---

### 13. Connect a Web App to Amazon Aurora
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Connect%20a%20Web%20App%20to%20Aurora)

Built a working web application on EC2 (Apache, PHP, and the MySQL client libraries) and connected it to an Amazon Aurora database for real-time data storage and retrieval. Configured the app's database credentials via a PHP include file, wrote a PHP page that read and wrote employee records to Aurora, and validated the integration end to end by submitting data through the UI and confirming it in the database via direct SQL queries.

**Skills demonstrated:** Amazon Aurora, EC2 web hosting (Apache/PHP), SQL, database-backed application integration

---

### 14. Load Data into DynamoDB
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Load%20Data%20into%20DynamoDB)

Created multiple DynamoDB tables and loaded them with data entirely through the AWS CLI in CloudShell, working with partition and sort keys to structure each table's primary key. Explored DynamoDB's flexible, schema-less item model firsthand, noting how individual items in the same table can carry different sets of attributes, and adjusted read/write capacity settings to understand how throughput affects cost and performance.

**Skills demonstrated:** Amazon DynamoDB, NoSQL data modeling, AWS CLI/CloudShell, read/write capacity management

---

### 15. Query Data with DynamoDB
**Repo:** [link](https://github.com/Bla-vk/AWS-Beginner-Roadmap/tree/main/Query%20Data%20with%20DynamoDB)

Queried DynamoDB tables by partition and sort key via the AWS CLI, working through the strict key requirements that distinguish NoSQL querying from relational SQL, and identified which insights were and weren't easily extractable without a well-modeled key structure. Executed a multi-table transactional write that atomically added a new record to one table while updating a related counter in another, guaranteeing all-or-nothing consistency across both.

**Skills demonstrated:** DynamoDB querying, partition/sort key design, AWS CLI, transactional writes, NoSQL data modeling

---

### 16. AWS Dev Environment with Terraform
**Repo:** [link](https://github.com/Bla-vk/terraform-aws-dev-environment)

Independent Infrastructure as Code project rebuilding my manual VPC and EC2 work in Terraform. Provisioned 9 resources with one `terraform apply`: a custom VPC (`10.100.0.0/16`), a public subnet, an Internet Gateway with a default route, a security group, an SSH key pair and an Ubuntu 24.04 EC2 instance. The AMI is found with a data source rather than hardcoded, and credentials come from a named AWS profile. A `user_data` script installs Docker Engine on first boot, and a `local-exec` provisioner writes the new server into my SSH config. Verified the build with `terraform plan`, SSH access and `docker run hello-world`, then removed everything with `terraform destroy`. Documented the troubleshooting, including a failed boot script and a stale SSH entry, and noted the open security group as a known limitation to harden.

**Skills demonstrated:** Terraform, Infrastructure as Code, Amazon VPC, EC2, data sources, `user_data` and cloud-init troubleshooting, Docker installation, SSH key management, `.gitignore` hygiene for state and secrets

---

## 💻 Software Projects

### 17. CRUD API
**Repo:** [link](https://github.com/Bla-vk/Simple-CRUD-API)

A REST API built in Python implementing full Create, Read, Update, and Delete operations.

**Skills demonstrated:** Python, REST API design, backend development

---

### 18. Chatbot
**Repo:** [link](https://github.com/Bla-vk/Chatbot)

A conversational chatbot built in Python.

**Skills demonstrated:** Python, conversational logic

---

### 19. Data Structures & Algorithms
**Repo:** [link](https://github.com/Bla-vk/Data_Structures_And_Algorithm-Python)

Implementations and practice solutions covering core data structures and algorithms in Python.

**Skills demonstrated:** Python, data structures, algorithmic problem solving

---

### 20. Frontend Project
**Repo:** [link](https://github.com/Bla-vk/random_frontend_projects)

A frontend project built with HTML, CSS, and JavaScript.

**Skills demonstrated:** HTML, CSS, JavaScript

---

## 🛠️ Tech Stack

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=flat&logo=terraform&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
