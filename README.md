# AWS-NOTES

---------------------------------------------------------------      🧠 AWS STUDY NOTES (Simplified & Organized)     ------------------------------------------------------------------------

✅ CORE CLOUD CONCEPTS

📦 Virtualization Layers
markdown
Copy
Edit
1. PHYSICAL SERVER - real machine
2. COMPUTE RESOURCES - CPU, RAM
3. STORAGE RESOURCES - HDD/SSD
4. HYPERVISOR - creates/manages virtual machines
5. VIRTUAL MACHINES (VMs) - your "servers"

💡 Virtualization is the heart of cloud computing. It allows multiple VMs on one physical server.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
📈 Cloud Benefits

Term	                                           Meaning
Scalability	Add more servers if demand increases (like auto-creating VMs). Used in Auto Scaling.
Elasticity	Remove extra servers when demand drops to save money.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------- ☁️ AWS Cloud Overview ------------------------------------------------------------------------------------------
1. 🔧 Compute

Service	Description
EC2	Virtual servers (VMs)
Lambda	Run code without servers (event-based, serverless)
Elastic Beanstalk	Full app deployment tool (automates EC2, scaling, monitoring)
ECS	Run Docker containers on AWS
EKS	Managed Kubernetes service for running containers
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
2. 🌐 Networking

Service	Description
VPC	Private network inside AWS; control subnets, routes, firewalls
Route 53	DNS service, turns myapp.com → IP
Elastic Load Balancer (ELB)	Distributes incoming traffic. ALB (Layer 7): For HTTP/HTTPS NLB (Layer 4): For TCP/UDP GWLB (Layer 3): For appliances like firewalls”.
Direct Connect	Direct cable link between AWS and your datacenter
CloudFront	CDN that caches your content near users, reduces load time
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
3. 🗄️ Storage

Service	Description
S3	Object storage (files like images, logs, videos)
S3 Glacier	Archive storage, slower but cheaper
EBS	Disk for EC2s (like a hard drive)
Storage Gateway	Bridge between on-premises storage and AWS (hybrid)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
4. 🧮 Databases

Service	Description
RDS	Managed SQL databases (MySQL, PostgreSQL, etc.)
Aurora	“AWS-optimized SQL DB (MySQL/PostgreSQL compatible, faster, with high availability and auto-scaling)”
DynamoDB	Fast NoSQL DB for apps needing millisecond latency
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
5. 📊 Monitoring & Management

Service	Description
CloudWatch	Monitor logs, CPU, alarms, dashboards
CloudTrail	Log all user/API activity in your AWS account
AWS Config	Tracks changes to resource configurations
CloudFormation	Infrastructure as code (build environments via templates)
Systems Manager	Manage EC2s, run commands/scripts remotely
OpsWorks	Use Chef/Puppet for automating infrastructure
AppConfig	Manage feature flags and config changes separately
CodeDeploy	Automate deployment to EC2s or on-prem servers
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
6. 🔐 Security & Identity

Service	Description
IAM	Create users, roles, permissions
Cognito	“User sign-up/sign-in and identity federation. Provides JWT tokens for access, and can integrate with IAM roles.”
KMS	Manage encryption keys
Directory Service	Connect AWS to Microsoft Active Directory for domain logins
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
7. 🔄 App Integration

Service	Description
SQS	Queue messages between services
SNS	Send emails, SMS, push notifications
SWF	Coordinate microservices into workflows (modern alternative to SWF)
API Gateway	Build/manage APIs for apps (routes traffic, adds auth etc.)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
🌍 AWS Global Infrastructure

“30+ regions and 100+ availability zones globally (and growing)”

GovCloud: AWS region dedicated to US government

Endpoints: URLs to access services (e.g., ec2.us-east-1.amazonaws.com)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
⚖️ AWS Shared Responsibility Model

Add: “Responsibility depends on the service type — with managed services like Lambda or S3, AWS handles more.”

You (Customer)	AWS
App data, OS, security config	Physical infrastructure, hardware
EC2 software config, network setup	Global availability, services
IAM, encryption, firewalls	Datacenter security, storage infra
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
💼 AWS Support Plans

Plan	Key Features
Basic	Free, account-level support only
Developer	$29+/mo, email access, dev help
Business	$100+/mo, 24/7, fast response, API support
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
🔄 AWS Migration Services

Service	Use
Migration Hub	Track/manage app migrations to AWS
App Migration Service	Lift & shift whole servers
Database Migration (DMS)	Move databases to AWS with minimal downtime
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

--------------------------------------------------------------------- ❌ YOUR MISTAKES FROM THE PRACTICE TEST -------------------------------------------------------------------------------
Question 2 - You answered A (wrong), correct answer: B
Explanation: Route 53 doesn’t help with scaling directly. Auto Scaling does.

🔑 Tip: Route 53 = DNS, not scaling.

Question 5 - You answered C (wrong), correct answer: A
Explanation: KMS is for managing encryption keys, not handling user auth or API keys.

🔑 Tip: For access control, think IAM, not KMS.

Question 6 - You answered D (wrong), correct answer: A
Explanation: AWS provides whitepapers and compliance reports to help you evaluate services. Not "customer feedback".

🔑 Tip: If you want to verify AWS meets regulations, read their whitepapers or certifications.

Question 10 - You answered B (wrong), correct answer: A
Explanation: Shared Responsibility Model – AWS is responsible for security of the cloud (infra). You’re responsible for what you put in the cloud.

🔑 Tip: Always ask: Is this physical/hardware? Then it’s AWS.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

EC2 has access to storage, memory, and network interface. Its primary storage drive will come with a fresh and clean operating system.

You choose hardware resources, the OS, and software stack.

Hardware specs (CPU, network, memory, primary storage) ← all of those are defined before launching.

The OS is defined by the Amazon Machine Image (AMI) you choose.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------- AMI – Amazon Machine Image --------------------------------------------------------------------------------------

An AMI is a pre-configured template used to launch EC2 instances with a specific OS and software.

Amazon Quick Start AMIs 🚀 – Pre-built AMIs by AWS to quickly deploy popular software and architectures following best practices.
→ Linux, Windows, macOS Server OSs.
→ Also available: deep learning, database operations, etc.

AWS Marketplace AMIs 🛒 – Pre-configured AMIs sold or shared by third-party vendors through AWS Marketplace for easy deployment of software solutions.

Community AMIs 🌍 – Free AMIs shared by other AWS users.
→ Most of them are created and maintained by independent vendors.

Private AMIs 🔒 – AMIs created by you or your organization, visible only to selected AWS accounts.

Particular AMIs will be available in single regions.
You get billed hourly when using certain paid AMI software.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------- EC2 Instance Type Families --------------------------------------------------------------------------------------

General Purpose ⚖️ – Balanced compute, memory, and networking.
→ Web servers, small databases, development environments.

Compute Optimized 💻 – High-performance CPUs for compute-heavy tasks.
→ Gaming servers, batch processing, scientific modeling.

Memory Optimized 💾 – More RAM for memory-intensive applications.
→ In-memory databases, real-time big data analytics, caching.

Accelerated Computing 🚀 – Uses GPUs or FPGAs for specialized workloads.
→ Machine learning, video processing, scientific simulations.

Storage Optimized 💽 – High-speed, high-capacity storage.
→ Big data processing, data warehousing, large NoSQL databases.

------------------------------------------------------------------ CONFIGURING AN ENVIRONMENT FOR YOUR INSTANCE -----------------------------------------------------------------------------

Before launching an EC2 instance, decide:

Region (where your server lives) 🌎
AWS Regions
AWS has data centers in different parts of the world, called regions.

→ Choose a region close to your users or one that meets legal requirements (like data laws).
→ You can only manage EC2 resources within the region you're currently using.

Set the active region:
→ Console (top-right dropdown)
→ CLI: aws configure

Costs and available features can differ between regions.

VPC (your network space) 🌐
VPC – Virtual Private Cloud
A VPC is your own private network inside AWS.

→ Use different VPCs for different project stages:
• Development
• Testing
• Production

 Example: Dev team updates api.myapp.com in the Dev VPC EC2, but Test and Prod teams don’t see the change because they use separate EC2 instances in isolated VPCs.

Basic VPCs (without NAT or VPN) are free.

Tenancy (shared or dedicated hardware) 🖥️
EC2 offers different tenancy models:

Shared Tenancy (default) 🏘️ – Your instance runs on a physical server shared with other poeple too.
→ It's secure. You don’t see or interact with others’ instances.

Dedicated Tenancy 💎 – Costs more.

✅ Dedicated Instances
→ Your EC2 instance runs on a physical server not shared with other AWS customers.
→ You don’t choose the exact server.

✅ Dedicated Hosts 🏠
→ Same isolation as Dedicated Instances, plus:
→ You know and control the exact physical server used.
→ Useful for special licensing or compliance.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------- User Data (Bootstrapping) ⚙️ -------------------------------------------------------------------------------------
Run custom commands/scripts when your EC2 instance boots.

→ Add via console or with --user-data in CLI.

Examples:

Install a web server

Join instance to config management like Puppet
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------- Placement Groups 📍 -----------------------------------------------------------------------------------------

Control how your instances are physically placed on AWS hardware.

• Cluster Placement Group 🏞️
→ All instances in one Availability Zone, close together.
→ Low latency, high throughput
→ Great for HPC

Example: A machine learning app with 10 EC2 instances needs ultra-fast communication between nodes.

• Spread Placement Group 🌐
→ Instances spread across different racks/zones.
→ Reduces risk of multiple failures.
→ Good for high-availability apps.

 Imagine each EC2 instance is put on a different physical rack or Availability Zone.
So if one rack crashes, the others keep working.
✅ Example: You have a critical app with 7 EC2s — AWS places each one on a separate rack, so one failure doesn’t kill your app.

• Partition Placement Group 🗂️
→ Instances grouped into partitions, each isolated.
→ Limits impact of failure.
→ Used for big systems like Hadoop.

 You split your EC2s into partitions, and each partition is isolated from the others (separate hardware).
So if one partition fails, the others are safe.
✅ Example: Running Hadoop with 3 partitions → each partition handles a chunk of data, and they don’t share hardware, so failure in one doesn’t affect the rest.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------- Spot Instances 💸 ----------------------------------------------------------------------------------------------
→ Cheaper than On-Demand
→ Best for interruptible workloads
→ Instance runs while price ≤ your bid
→ Stops if price > your bid
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------ Combining Models 🔀 ------------------------------------------------------------------------------------------
Reserved Instances → for stable demand

On-Demand Instances → for traffic spikes

Reserved Instances → for stable demand
✅ Example: A backend API server that runs 24/7 for your production app.

On-Demand Instances → for traffic spikes
✅ Example: Extra EC2s launched on Black Friday to handle a sudden increase in shopping traffic.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------- Terminating vs. Stopping ⏹️ --------------------------------------------------------------------------------------
Terminate = deletes instance + non-persistent data

Stop = saves instance + keeps EBS data

Public IP changes after stop (unless using Elastic IP).
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------ Changing Settings ⚙️ -----------------------------------------------------------------------------------------
Can edit Security Groups anytime (even running)

Can change Instance Type (stop → change → restart)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------- Resource Tags 🏷️ -------------------------------------------------------------------------------------------
Tags = Key + optional Value
→ Used to identify and organize resources
→ Helps with tracking in large deployments
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------- Service Limits 📉 ---------------------------------------------------------------------------------------
AWS sets default limits per account (some per region, some global)

Examples:

5 VPCs per region

5,000 SSH key pairs per account

You can request limit increases if needed.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------- EBS – Elastic Block Store Volumes 💾 ------------------------------------------------------------------------------
→ Virtual hard drives attached to EC2 instances
→ Can attach multiple volumes (but only 1 instance per volume)
→ Persist even after instance is stopped

Use EBS Data Lifecycle Manager for snapshot & data management

EBS Volume Types:

Provisioned IOPS SSD 🚀
→ Best for high-performance apps (e.g., databases)
→ Types: io1, io2, io2 Block Express
→ Up to 256,000 IOPS & 4,000 MB/s (io2 Block Express)

✅ Example: A PostgreSQL database handling thousands of transactions per second.

General-Purpose SSD 📈
→ Good for regular workloads
→ Max 3,000 IOPS
→ Cost Example: $3.29/month for 8 GB boot volume

✅ Example: A web server hosting your portfolio or e-commerce site.

HDD Volumes (Spinning Disk) 💽
→ Good for cold storage or infrequent data
→ Types:

• sc1 (cold HDD) – Cheapest → $0.015/GB-month

✅ Example: Archiving monthly logs that you rarely access.

• st1 (throughput-optimized) – 250 MB/s per TB

✅ Example: Streaming large video files from S3 to EC2 for processing.

• standard (magnetic) – Legacy option

✅ Example: Old legacy system backup storage (not recommended for new setups).

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
