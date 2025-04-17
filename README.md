# 🧠 AWS STUDY NOTES (Simplified & Organized)

---

## ✅ CORE CLOUD CONCEPTS

### 📦 Virtualization Layers
1. **PHYSICAL SERVER** - real machine  
2. **COMPUTE RESOURCES** - CPU, RAM  
3. **STORAGE RESOURCES** - HDD/SSD  
4. **HYPERVISOR** - creates/manages virtual machines  
5. **VIRTUAL MACHINES (VMs)** - your "servers"

💡 Virtualization is the heart of cloud computing. It allows multiple VMs on one physical server.

---

### 📈 Cloud Benefits

| Term        | Meaning                                                                 |
|-------------|-------------------------------------------------------------------------|
| **Scalability** | Add more servers if demand increases (like auto-creating VMs). Used in Auto Scaling. |
| **Elasticity**  | Remove extra servers when demand drops to save money.                 |

---

## ☁️ AWS Cloud Overview

### 1. 🔧 Compute

| Service              | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **EC2**              | Virtual servers (VMs)                                                        |
| **Lambda**           | Run code without servers (event-based, serverless)                          |
| **Elastic Beanstalk**| Full app deployment tool (automates EC2, scaling, monitoring)              |
| **ECS**              | Run Docker containers on AWS                                                 |
| **EKS**              | Managed Kubernetes service for running containers                            |

---

### 2. 🌐 Networking

| Service                    | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **VPC**                    | Private network inside AWS; control subnets, routes, firewalls               |
| **Route 53**               | DNS service, turns myapp.com → IP                                            |
| **Elastic Load Balancer (ELB)** | Distributes incoming traffic. ALB (Layer 7): For HTTP/HTTPS NLB (Layer 4): For TCP/UDP GWLB (Layer 3): For appliances like firewalls |
| **Direct Connect**         | Direct cable link between AWS and your datacenter                           |
| **CloudFront**             | CDN that caches your content near users, reduces load time                  |

---

### 3. 🗄️ Storage

| Service                    | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **S3**                     | Object storage (files like images, logs, videos)                            |
| **S3 Glacier**             | Archive storage, slower but cheaper                                          |
| **EBS**                    | Disk for EC2s (like a hard drive)                                            |
| **Storage Gateway**        | Bridge between on-premises storage and AWS (hybrid)                         |

---

### 4. 🧮 Databases

| Service                    | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **RDS**                    | Managed SQL databases (MySQL, PostgreSQL, etc.)                              |
| **Aurora**                 | AWS-optimized SQL DB (MySQL/PostgreSQL compatible, faster, with high availability and auto-scaling) |
| **DynamoDB**               | Fast NoSQL DB for apps needing millisecond latency                           |

---

### 5. 📊 Monitoring & Management

| Service                    | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **CloudWatch**             | Monitor logs, CPU, alarms, dashboards                                       |
| **CloudTrail**             | Log all user/API activity in your AWS account                               |
| **AWS Config**             | Tracks changes to resource configurations                                   |
| **CloudFormation**         | Infrastructure as code (build environments via templates)                   |
| **Systems Manager**        | Manage EC2s, run commands/scripts remotely                                   |
| **OpsWorks**               | Use Chef/Puppet for automating infrastructure                               |
| **AppConfig**              | Manage feature flags and config changes separately                          |
| **CodeDeploy**             | Automate deployment to EC2s or on-prem servers                              |

---

### 6. 🔐 Security & Identity

| Service                    | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **IAM**                    | Create users, roles, permissions                                             |
| **Cognito**                | User sign-up/sign-in and identity federation. Provides JWT tokens for access, and can integrate with IAM roles. |
| **KMS**                    | Manage encryption keys                                                      |
| **Directory Service**      | Connect AWS to Microsoft Active Directory for domain logins                 |

---

### 7. 🔄 App Integration

| Service                    | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **SQS**                    | Queue messages between services                                              |
| **SNS**                    | Send emails, SMS, push notifications                                         |
| **SWF**                    | Coordinate microservices into workflows (modern alternative to SWF)        |
| **API Gateway**            | Build/manage APIs for apps (routes traffic, adds auth etc.)                 |

---

### 🌍 AWS Global Infrastructure

“30+ regions and 100+ availability zones globally (and growing)”

GovCloud: AWS region dedicated to US government

Endpoints: URLs to access services (e.g., ec2.us-east-1.amazonaws.com)

---

### ⚖️ AWS Shared Responsibility Model

| You (Customer)             | AWS                                                                    |
|----------------------------|------------------------------------------------------------------------|
| App data, OS, security config | Physical infrastructure, hardware                                      |
| EC2 software config, network setup | Global availability, services                                        |
| IAM, encryption, firewalls  | Datacenter security, storage infra                                    |

---

### 💼 AWS Support Plans

| Plan            | Key Features                                                            |
|-----------------|-------------------------------------------------------------------------|
| **Basic**       | Free, account-level support only                                         |
| **Developer**   | $29+/mo, email access, dev help                                          |
| **Business**    | $100+/mo, 24/7, fast response, API support                              |

---

### 🔄 AWS Migration Services

| Service                    | Use                                                                         |
|----------------------------|-----------------------------------------------------------------------------|
| **Migration Hub**           | Track/manage app migrations to AWS                                          |
| **App Migration Service**   | Lift & shift whole servers                                                  |
| **Database Migration (DMS)**| Move databases to AWS with minimal downtime                                 |

---

### EC2 has access to storage, memory, and network interface. Its primary storage drive will come with a fresh and clean operating system.

You choose hardware resources, the OS, and software stack.

Hardware specs (CPU, network, memory, primary storage) ← all of those are defined before launching.

The OS is defined by the Amazon Machine Image (AMI) you choose.

---

## AMI – Amazon Machine Image

An AMI is a pre-configured template used to launch EC2 instances with a specific OS and software.

**Amazon Quick Start AMIs 🚀** – Pre-built AMIs by AWS to quickly deploy popular software and architectures following best practices.  
→ Linux, Windows, macOS Server OSs.  
→ Also available: deep learning, database operations, etc.

**AWS Marketplace AMIs 🛒** – Pre-configured AMIs sold or shared by third-party vendors through AWS Marketplace for easy deployment of software solutions.

**Community AMIs 🌍** – Free AMIs shared by other AWS users.  
→ Most of them are created and maintained by independent vendors.

**Private AMIs 🔒** – AMIs created by you or your organization, visible only to selected AWS accounts.

Particular AMIs will be available in single regions.  
You get billed hourly when using certain paid AMI software.

---

## EC2 Instance Type Families

### General Purpose ⚖️ 
Balanced compute, memory, and networking.  
→ Web servers, small databases, development environments.

### Compute Optimized 💻
High-performance CPUs for compute-heavy tasks.  
→ Gaming servers, batch processing, scientific modeling.

### Memory Optimized 💾 
More RAM for memory-intensive applications.  
→ In-memory databases, real-time big data analytics, caching.

### Accelerated Computing 🚀 
Uses GPUs or FPGAs for specialized workloads.  
→ Machine learning, video processing, scientific simulations.

### Storage Optimized 💽 
High-speed, high-capacity storage.  
→ Big data processing, data warehousing, large NoSQL databases.

---

## CONFIGURING AN ENVIRONMENT FOR YOUR INSTANCE

Before launching an EC2 instance, decide:

### Region (where your server lives) 🌎
AWS has data centers in different parts of the world, called regions.

→ Choose a region close to your users or one that meets legal requirements (like data laws).  
→ You can only manage EC2 resources within the region you're currently using.

**Set the active region**:  
→ Console (top-right dropdown)  
→ CLI: `aws configure`

Costs and available features can differ between regions.

### VPC (your network space) 🌐
A VPC is your own private network inside AWS.

→ Use different VPCs for different project stages:  
• Development  
• Testing  
• Production  

Example: Dev team updates `api.myapp.com` in the Dev VPC EC2, but Test and Prod teams don’t see the change because they use separate EC2 instances in isolated VPCs.

Basic VPCs (without NAT or VPN) are free.

---

### Tenancy (shared or dedicated hardware) 🖥️

**Shared Tenancy (default) 🏘️** – Your instance runs on a physical server shared with other people too.  
→ It's secure. You don’t see or interact with others’ instances.

**Dedicated Tenancy 💎** – Costs more.

- **Dedicated Instances** → Your EC2 instance runs on a physical server not shared with other AWS customers.
- **Dedicated Hosts 🏠** → Same isolation as Dedicated Instances, plus you know and control the exact physical server used.

---

### User Data (Bootstrapping) 🧰

A script you can attach to the instance to execute automatically during launch.

E.g., Automatically install software when EC2 starts.  
You can define it through the **Console, CLI, or CloudFormation templates**.

Example: For installing an Nginx server:

```bash
#!/bin/bash
yum install -y nginx
service nginx start
