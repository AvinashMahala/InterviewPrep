### AWS Interview Questions and Answers

#### Basic AWS Interview Questions

**Question 1: Describe the three major categories of cloud service and the AWS products based on them.**
- **Answer**:
  - **Public Cloud**: Built using end-users' infrastructure, e.g., AWS, Google Cloud.
  - **Private Cloud**: Used by one individual or group, often on rented data centers.
  - **Hybrid Cloud**: Combines public and private clouds, appearing as a connected environment.
  - **Services**: 
    - **Infrastructure as a Service (IaaS)**: Managed infrastructure (e.g., EC2).
    - **Platform as a Service (PaaS)**: Managed hardware and application software platforms (e.g., Elastic Beanstalk).
    - **Software as a Service (SaaS)**: Managed software applications (e.g., Amazon WorkMail).

**Question 2: How do the availability zone and the region relate to one another?**
- **Answer**: Each region has multiple isolated locations called availability zones, identified by a region code followed by a letter (e.g., us-east-1a). Regions are isolated for fault tolerance and stability. Resources are tied to the specified region, and AMIs in different regions must be copied.

**Question 3: What is auto scaling?**
- **Answer**: AWS Auto Scaling monitors applications and adjusts capacity to maintain steady performance at the lowest cost. It provides a user interface for building scaling plans for resources, including EC2 instances.

**Question 4: What is Geo targeting in CloudFront?**
- **Answer**: Geo targeting in CloudFront detects the country from where users request content, passing this information to the origin server via an HTTP header. This allows generating and caching different content versions based on geographic location.

**Question 5: What services can be used to create a centralized logging solution?**
- **Answer**: 
  - Amazon CloudWatch Logs
  - Amazon S3
  - Amazon Elasticsearch
  - Amazon Kinesis Firehose

**Question 6: What are the different types of virtualization in AWS and what are the differences between them?**
- **Answer**:
  - **Hardware Virtual Machine (HVM)**: Fully virtualized hardware acting as separate VMs.
  - **Para-Virtualization (PV)**: Uses a bootloader to chain load the kernel.
  - **Para-Virtualization on HVM**: Combines HVM with optimized storage and network I/O.

**Question 7: Explain what T2 instances are.**
- **Answer**: T2 instances are burstable performance instances providing a base level of CPU performance with the ability to burst above the baseline. Performance is governed by CPU credits accumulated when idle and consumed when active.

#### EC2 Interview Questions

**Question 8: What is Amazon EC2?**
- **Answer**: Amazon EC2 (Elastic Compute Cloud) provides scalable computing capacity, eliminating the need to invest in hardware. It allows launching and managing virtual servers with configurable security, networking, and storage.

**Question 9: What are Solaris and AIX operating systems, and are they available with AWS?**
- **Answer**: 
  - **Solaris**: Uses SPARC architecture, not supported by AWS.
  - **AIX**: Runs on Power CPU, not on Intel, thus not available in AWS.

**Question 10: What are key pairs in AWS?**
- **Answer**: Key pairs are password-protected login credentials (private key and public key) used to prove identity when connecting to EC2 instances.

#### S3 Interview Questions

**Question 11: What is Amazon S3?**
- **Answer**: Amazon S3 (Simple Storage Service) is an object storage service that stores and retrieves any amount of data from anywhere. It offers durability, availability, and cost-effectiveness.

**Question 12: How do you allow a user to gain access to a specific bucket?**
- **Answer**: 
  - Categorize instances
  - Define how authorized users manage specific servers
  - Lock down tags
  - Attach policies to IAM users

**Question 13: What are the storage classes available in Amazon S3?**
- **Answer**:
  - Amazon S3 Glacier Instant Retrieval
  - Amazon S3 Glacier Flexible Retrieval
  - Amazon S3 Glacier Deep Archive
  - S3 Outposts
  - Amazon S3 Standard-IA
  - Amazon S3 One Zone-IA
  - Amazon S3 Standard
  - Amazon S3 Reduced Redundancy Storage
  - Amazon S3 Intelligent-Tiering

#### VPC Interview Questions

**Question 14: What is Amazon VPC and why is it used?**
- **Answer**: Amazon VPC (Virtual Private Cloud) connects cloud resources to on-premises data centers, providing isolated network environments with private IP addresses, accessed as if on a private network.

**Question 15: How do you connect multiple sites to a VPC?**
- **Answer**:
  - Create a VPN gateway
  - Create a customer gateway for each office
  - Create an IP section for VPN connection for each office
  - Configure routes for the VPN gateway
  - Configure on-premises gateway devices
  - Test network connectivity

#### CloudFormation Interview Questions

**Question 16: What are the steps involved in a CloudFormation solution?**
- **Answer**:
  - Create or use an existing CloudFormation template (JSON or YAML)
  - Save the code in an S3 bucket
  - Use CloudFormation to call the bucket and create a stack
  - CloudFormation reads the file, understands the services, and provisions them

**Question 17: How is AWS CloudFormation different from AWS Elastic Beanstalk?**
- **Answer**: 
  - **CloudFormation**: Provisions and describes all infrastructure resources.
  - **Elastic Beanstalk**: Provides an environment to deploy and run applications.

#### EBS Interview Questions

**Question 18: How can you automate EC2 backup using EBS?**
- **Answer**:
  - List instances and connect via API
  - List EBS volumes attached to instances
  - List snapshots and assign retention period
  - Create snapshots
  - Remove snapshots older than the retention period

**Question 19: What is the difference between EBS and instance storage?**
- **Answer**:
  - **EBS**: Permanent storage, data persists after instance termination.
  - **Instance Storage**: Temporary storage, data lost if the instance is stopped or terminated.

#### Elastic Load Balancing Interview Questions

**Question 20: What are the different types of load balancers in AWS?**
- **Answer**:
  - Application Load Balancer
  - Network Load Balancer
  - Classic Load Balancer

#### Security Interview Questions

**Question 21: What is Identity and Access Management (IAM) and how does it work?**
- **Answer**: IAM ensures that the right people and roles in an organization can access the tools they need. It manages identities, including people, software, and hardware, allowing controlled access without logging into each app as an administrator.

**Question 22: What are the different AWS IAM categories you can control?**
- **Answer**:
  - Create and manage IAM users
  - Create and manage IAM groups
  - Manage security credentials of users
  - Create and manage policies to grant access to services and resources

**Question 23: What is the difference between IAM roles and IAM users?**
- **Answer**:
  - **IAM Role**: Entity with permissions for making service requests, used by trusted entities like users or applications.
  - **IAM User**: Permanent long-term credentials, used to interact with AWS services directly.

#### Route 53 Interview Questions

**Question 24: What is Amazon Route 53?**
- **Answer**: Amazon Route 53 is a scalable DNS web service that connects user requests to internet applications running on AWS or on-premises. It uses TCP/UDP Port 53 for DNS server requests.

**Question 25: What is the difference between latency-based routing and Geo DNS?**
- **Answer**:
  - **Latency-Based Routing**: Utilizes latency measurements to provide the lowest latency possible.
  - **Geo DNS**: Takes decisions based on the geographic location of the request.

#### Advanced AWS Interview Questions

**Question 26: Define the snapshot in AWS LightSail.**
- **Answer**: Snapshots are point-in-time backups of EC2 instances, storage devices, and databases. They can be created manually or automatically and used to restore resources.

**Question 27: Explain Amazon EC2 root device volume.**
- **Answer**: The root device volume is the image used to boot an EC2 instance, supported by EBS or instance store. Data on EBS is not affected by the instance's lifespan.

**Question 28: Mention the different types of instances in Amazon EC2 and explain their features.**
- **Answer**:
  - **General Purpose Instances**: Balance of compute, memory, and networking.
  - **Compute Optimized Instances**: Ideal for compute-intensive applications.
  - **Memory Optimized Instances**: Handle large data sets in memory.
  - **Accelerated Computing Instances**: Execute floating-point calculations, data pattern matching, and graphic processing.
  - **Storage Optimized Instances**: Handle tasks requiring sequential read/write access to large data sets.

#### Scenario-Based Questions

**Scenario 1: I have private servers on my premises and have distributed some workloads on the private cloud. What is this architecture called?**
- **Answer**: Hybrid Cloud, combining private and public cloud resources.

**Scenario 2: Your business prefers to use its email address and domain to send and receive compliant emails. What service do you recommend to implement this easily and budget-friendly?**
- **Answer**: Amazon Simple Email Service (SES), a cloud-based email sending service.

**Scenario 3: On an EC2 instance, an application is active. Once the CPU usage hits 80%, you must reduce the load on it. What strategy do you use to complete this task?**
- **Answer**: Set up an auto-scaling group to deploy additional instances when CPU usage exceeds 80% and use an application load balancer to distribute traffic across instances.

**Scenario 4: Configure an Amazon S3 bucket to serve static assets for your public-facing web application. Which method will ensure that all objects uploaded to the bucket are set to public read?**
- **Answer**: Configure the bucket policy to set all objects to public read.

**Scenario 5: When should you use Amazon EFS, Amazon S3, and Amazon Elastic Block Store (EBS)?**
- **Answer**:
  - **Amazon EFS**: For file storage with Amazon compute services (e.g., EC2, containers).
  - **Amazon S3**: For object storage accessible via internet API.
  - **Amazon EBS**: For block-level storage with low-latency access for a single EC2 instance.