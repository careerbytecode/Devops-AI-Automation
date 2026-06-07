# AWS EC2 Fundamentals

## Introduction

Amazon Elastic Compute Cloud (EC2) is a web service provided by AWS that enables users to launch and manage virtual servers in the cloud. EC2 eliminates the need to purchase and maintain physical hardware by providing scalable computing resources on demand. Organizations use EC2 to host applications, websites, databases, CI/CD tools, containerized workloads, and enterprise systems.

EC2 offers flexibility in choosing operating systems, storage options, networking configurations, security settings, and pricing models. It is one of the most widely used AWS services and forms the foundation of many cloud architectures.

---

# Amazon EC2 Instances

An EC2 Instance is a virtual machine running in AWS. It provides compute resources such as CPU, memory, networking, and storage for applications and services.

An EC2 instance behaves like a traditional server. Users can install software, configure operating systems, host web applications, run databases, and deploy enterprise workloads.

### Key Benefits

* On-demand provisioning
* Elastic scalability
* Pay-as-you-go pricing
* High availability
* Global deployment capabilities

### Common Use Cases

* Web hosting
* Application hosting
* DevOps tools (Jenkins, GitLab)
* Kubernetes worker nodes
* Monitoring platforms
* Development and testing environments

---

# EC2 Storage Configuration

Storage in EC2 is typically provided through Amazon Elastic Block Store (EBS). Every EC2 instance requires storage to hold the operating system, application files, logs, and user data.

When launching an instance, users can configure:

* Volume size
* Volume type
* Encryption settings
* Delete-on-termination behavior

Storage can be expanded later without rebuilding the server, making it highly flexible for growing workloads.

### Example

A web server may require:

* 20 GB storage for operating system
* Application binaries
* Log files
* Configuration files

---

# EC2 Instance Types

Instance types define the amount of CPU, memory, networking performance, and storage capabilities assigned to an EC2 instance.

AWS offers different families optimized for specific workloads.

## General Purpose

Balanced compute and memory.

Examples:

* t2.micro
* t3.micro
* m5.large

Suitable for:

* Web applications
* Development environments
* Small business workloads

## Compute Optimized

High CPU performance.

Examples:

* c5.large
* c6i.large

Suitable for:

* Build servers
* High-performance computing
* Batch processing

## Memory Optimized

Large memory capacity.

Examples:

* r5.large
* r6i.large

Suitable for:

* Databases
* In-memory caching
* Enterprise applications

## Storage Optimized

Designed for high disk throughput.

Suitable for:

* Big data
* Data warehousing
* Analytics workloads

---

# Security Groups

Security Groups act as virtual firewalls for EC2 instances.

They control inbound and outbound traffic by defining rules based on protocols, ports, and source IP addresses.

Security Groups are stateful, meaning return traffic is automatically allowed if the incoming request is permitted.

### Example Rules

| Protocol | Port | Purpose                |
| -------- | ---- | ---------------------- |
| SSH      | 22   | Linux Administration   |
| HTTP     | 80   | Website Access         |
| HTTPS    | 443  | Secure Website Access  |
| MySQL    | 3306 | Database Communication |

### Best Practices

* Restrict SSH access to trusted IP addresses.
* Avoid exposing databases directly to the internet.
* Follow the principle of least privilege.

---

# Key Pairs

AWS uses public-key cryptography to securely access EC2 instances.

A Key Pair consists of:

* Public Key
* Private Key

AWS stores the public key on the EC2 instance while the user downloads and manages the private key.

### Benefits

* Secure authentication
* Passwordless login
* Reduced risk of brute-force attacks

### Example SSH Connection

```bash
chmod 400 my-key.pem
ssh -i my-key.pem ec2-user@<Public-IP>
```

---

# Amazon Machine Images (AMIs)

An Amazon Machine Image (AMI) is a pre-configured template used to launch EC2 instances.

An AMI contains:

* Operating System
* Software Packages
* Security Configurations
* Application Code
* Storage Mappings

AMIs help organizations create identical servers quickly and consistently.

## Types of AMIs

### AWS Provided AMIs

Examples:

* Amazon Linux
* Windows Server
* Ubuntu

### Marketplace AMIs

Examples:

* Jenkins
* WordPress
* MongoDB
* Splunk

### Custom AMIs

Created by organizations to include:

* Internal applications
* Security policies
* Monitoring agents
* Pre-installed software

## Benefits

* Faster deployments
* Infrastructure consistency
* Auto Scaling support
* Disaster recovery

---

# Amazon EBS (Elastic Block Store)

Amazon EBS provides persistent block-level storage for EC2 instances.

It functions as a virtual hard drive attached to an EC2 instance.

EBS volumes store:

* Operating systems
* Applications
* Databases
* Logs
* User files

Data remains available even if the EC2 instance is stopped.

## Volume Types

### General Purpose SSD (gp3)

Recommended for most workloads.

Suitable for:

* Web applications
* Development environments
* General-purpose servers

### Provisioned IOPS SSD (io2)

High-performance storage.

Suitable for:

* Enterprise databases
* Mission-critical applications

### Throughput Optimized HDD (st1)

Designed for large-scale data processing.

Suitable for:

* Big data workloads
* Analytics

### Cold HDD (sc1)

Low-cost storage.

Suitable for:

* Archiving
* Long-term retention

---

# EBS Snapshots

An EBS Snapshot is a backup of an EBS volume.

Snapshots are stored in Amazon S3 and can be used to:

* Restore data
* Recover from failures
* Create new volumes
* Support disaster recovery

### Snapshot Workflow

```text
EBS Volume
      ↓
Create Snapshot
      ↓
Stored in S3
      ↓
Restore When Needed
```

---

# Spot Instances

Spot Instances allow users to utilize AWS's unused compute capacity at significantly reduced prices.

Savings can be up to 90% compared to On-Demand pricing.

### Advantages

* Extremely cost-effective
* Suitable for temporary workloads

### Limitations

AWS can terminate Spot Instances with a two-minute notice if capacity is required elsewhere.

### Suitable Workloads

* CI/CD pipelines
* Batch processing
* Big data analytics
* Machine learning training
* Testing environments

---

# Savings Plans

Savings Plans provide discounted pricing in exchange for committing to a specific amount of compute usage over a one-year or three-year period.

Unlike Reserved Instances, Savings Plans offer greater flexibility.

### Benefits

* Lower costs
* Flexible instance families
* Flexible operating systems
* Flexible regions

### Ideal For

Organizations with predictable long-term cloud usage.

---

# Reserved Instances (RI)

Reserved Instances provide discounted pricing when customers commit to specific instance types for one or three years.

### Benefits

* Significant cost savings
* Capacity reservation
* Predictable pricing

### Suitable Workloads

* Production servers
* Long-running applications
* Enterprise systems

### Limitations

Less flexible than Savings Plans.

---

# Dedicated Hosts

Dedicated Hosts provide an entire physical server exclusively for a single AWS customer.

No other AWS customers share the hardware.

### Benefits

* Physical isolation
* Regulatory compliance
* License compliance
* Hardware visibility

### Common Use Cases

* Government workloads
* Financial services
* Healthcare systems
* Bring Your Own License (BYOL) scenarios

### Considerations

Dedicated Hosts are more expensive than standard EC2 instances but provide maximum control and compliance support.

---

# EC2 Purchasing Model Comparison

| Feature       | On-Demand         | Spot Instances | Savings Plans   | Reserved Instances | Dedicated Hosts         |
| ------------- | ----------------- | -------------- | --------------- | ------------------ | ----------------------- |
| Commitment    | None              | None           | 1-3 Years       | 1-3 Years          | Long-Term               |
| Cost          | Highest           | Lowest         | Low             | Low                | Highest                 |
| Flexibility   | High              | High           | High            | Medium             | Low                     |
| Interruptible | No                | Yes            | No              | No                 | No                      |
| Best For      | General Workloads | Batch Jobs     | Long-Term Usage | Stable Workloads   | Compliance Requirements |

---

# Conclusion

Amazon EC2 is a foundational AWS service that provides scalable virtual servers in the cloud. By combining EC2 Instances, EBS Storage, AMIs, Security Groups, Key Pairs, and appropriate pricing models such as Spot Instances, Savings Plans, Reserved Instances, and Dedicated Hosts, organizations can build secure, scalable, highly available, and cost-effective cloud infrastructures.

Understanding these concepts is essential for cloud engineers, DevOps engineers, system administrators, and AWS certification candidates.
