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

## 💻 Software Projects

### 5. CRUD API
**Repo:** [link](https://github.com/Bla-vk/Simple-CRUD-API)

A REST API built in Python implementing full Create, Read, Update, and Delete operations.

**Skills demonstrated:** Python, REST API design, backend development

---

### 6. Chatbot
**Repo:** [link](https://github.com/Bla-vk/Chatbot)

A conversational chatbot built in Python.

**Skills demonstrated:** Python, conversational logic

---

### 7. Data Structures & Algorithms
**Repo:** [link](https://github.com/Bla-vk/Data_Structures_And_Algorithm-Python)

Implementations and practice solutions covering core data structures and algorithms in Python.

**Skills demonstrated:** Python, data structures, algorithmic problem solving

---

### 8. Frontend Project
**Repo:** [link](https://github.com/Bla-vk/random_frontend_projects)

A frontend project built with HTML, CSS, and JavaScript.

**Skills demonstrated:** HTML, CSS, JavaScript

---

## 🛠️ Tech Stack

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
