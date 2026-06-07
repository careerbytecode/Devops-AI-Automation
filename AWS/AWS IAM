
# AWS IAM (Identity and Access Management)

## Overview

AWS Identity and Access Management (IAM) is a global AWS service that enables organizations to securely manage access to AWS resources. IAM controls **who can access AWS resources** and **what actions they can perform**.

IAM follows the principle of **Authentication** (Who are you?) and **Authorization** (What are you allowed to do?).

It is one of the most critical AWS services because every AWS environment relies on IAM to implement security and access control.

---

# Why IAM is Important

In a real-world organization, different teams require different levels of access.

For example:

* Developers may need access to EC2 instances.
* DevOps Engineers may require permissions to manage infrastructure.
* Testers may need access to test environments.
* Finance teams may only require billing access.

Providing full administrative access to everyone creates significant security risks. IAM allows organizations to enforce the principle of **Least Privilege**, ensuring users receive only the permissions necessary to perform their jobs.

---

# IAM Users

An IAM User represents an individual person or application that requires access to AWS resources.

Each IAM User can have:

* A unique username
* AWS Management Console password
* Programmatic access using Access Keys
* Permissions assigned through IAM Policies

### Example

A DevOps Engineer named Sourabh requires access to manage EC2 instances.

Instead of sharing the AWS root account, a dedicated IAM User can be created with only the permissions required for DevOps activities.

### Benefits

* Individual accountability
* Activity tracking through AWS CloudTrail
* Secure access management
* Easier auditing and compliance

---

# IAM Policies

IAM Policies are JSON-based documents that define permissions.

Policies determine:

* Which actions are allowed or denied
* Which AWS resources can be accessed
* Under what conditions access is granted

Policies can be attached to:

* Users
* Groups
* Roles

### Sample Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeInstances"
      ],
      "Resource": "*"
    }
  ]
}
```

### Policy Components

| Component | Description           |
| --------- | --------------------- |
| Effect    | Allow or Deny         |
| Action    | AWS API operations    |
| Resource  | AWS resource ARN      |
| Condition | Optional restrictions |

### Types of Policies

#### AWS Managed Policies

Created and maintained by AWS.

Example:

* AmazonEC2ReadOnlyAccess
* AmazonS3ReadOnlyAccess
* AdministratorAccess

#### Customer Managed Policies

Created and managed by organizations to meet custom business requirements.

#### Inline Policies

Policies directly embedded into a specific user, group, or role.

---

# IAM Groups

IAM Groups are collections of IAM Users.

Instead of assigning permissions individually to each user, permissions can be assigned to a group.

### Example

A company may have:

* Developers Group
* DevOps Group
* QA Group

All developers can be added to the Developers Group and automatically inherit the permissions assigned to that group.

### Benefits

* Simplified administration
* Easier permission management
* Consistent access control

---

# IAM Roles

An IAM Role is an AWS identity that provides temporary permissions.

Unlike IAM Users, Roles do not have:

* Username
* Password
* Permanent Access Keys

Roles are assumed by trusted entities such as:

* EC2 Instances
* Lambda Functions
* ECS Tasks
* AWS Services
* External Users

### Why Roles Are Important

Storing Access Keys on servers is a security risk.

Instead, AWS recommends assigning IAM Roles to AWS resources.

AWS automatically provides temporary credentials when a service assumes a role.

### Example

An EC2 instance needs to read files from an S3 bucket.

Instead of storing AWS credentials on the server:

1. Create an IAM Role.
2. Attach S3 permissions.
3. Assign the role to the EC2 instance.

The EC2 instance receives temporary credentials automatically.

### Advantages

* No hardcoded credentials
* Enhanced security
* Temporary credential management
* Follows AWS security best practices

---

# IAM Role Example

## Trust Relationship

A trust policy determines who can assume the role.

Example:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "ec2.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

This trust relationship allows EC2 instances to assume the role.

---

# Multi-Factor Authentication (MFA)

Multi-Factor Authentication (MFA) provides an additional layer of security beyond passwords.

Even if an attacker obtains a user's password, access is denied without the second authentication factor.

### Authentication Factors

1. Something you know (Password)
2. Something you have (Authenticator App or Hardware Device)

### Supported MFA Methods

* Google Authenticator
* Microsoft Authenticator
* Hardware MFA Devices

### MFA Login Flow

1. User enters username.
2. User enters password.
3. User enters MFA code.
4. AWS validates both factors.
5. Access is granted.

### Benefits

* Protection against stolen passwords
* Reduced risk of unauthorized access
* Stronger account security
* Recommended for all privileged accounts

---

# Root User vs IAM User

## Root User

The root user is created when an AWS account is first established.

The root user has unrestricted access to all AWS services and resources.

### Best Practices for Root User

* Enable MFA immediately
* Do not use for daily tasks
* Store credentials securely
* Use only for account-level activities

Examples:

* Changing support plans
* Closing AWS accounts
* Managing payment methods

---

## IAM User

IAM Users should be used for daily administrative and operational tasks.

### Advantages

* Granular permissions
* Activity tracking
* Enhanced security
* Easier auditing

---

# IAM Best Practices

## Follow Least Privilege

Grant only the permissions required to perform a specific job.

## Enable MFA

Enable MFA for:

* Root User
* Administrators
* Privileged users

## Use Roles Instead of Access Keys

Whenever possible:

* Assign Roles to EC2
* Assign Roles to Lambda
* Avoid storing Access Keys

## Rotate Credentials Regularly

Periodically update:

* Passwords
* Access Keys

## Use Groups for Permission Management

Manage permissions at the group level instead of individually.

## Monitor IAM Activities

Use:

* AWS CloudTrail
* AWS Config
* CloudWatch

for auditing and monitoring access activities.

---

# Real-World DevOps Use Cases

## EC2 Accessing S3

Attach an IAM Role with S3 permissions to the EC2 instance.

## Lambda Uploading Files to S3

Assign an IAM Role containing S3 write permissions.

## Cross-Account Access

Use IAM Roles to allow users from one AWS account to access resources in another account.

## CI/CD Pipelines

Grant deployment permissions through IAM Roles instead of long-term credentials.

---

# Interview Questions

### What is IAM?

IAM is a service used to manage authentication and authorization for AWS resources.

### What is the difference between IAM User and IAM Role?

An IAM User has permanent credentials and represents a person or application. An IAM Role provides temporary credentials and is assumed by trusted entities such as AWS services.

### What is the principle of least privilege?

It means granting only the minimum permissions required to perform a task.

### Why should IAM Roles be used instead of Access Keys?

Roles provide temporary credentials and eliminate the need to store long-term secrets.

### What is MFA?

MFA adds an additional authentication factor beyond passwords, improving account security.

### What happens if both Allow and Deny exist in a policy?

Explicit Deny always takes precedence over Allow.

---

# Summary

AWS IAM is the foundation of AWS security. It enables organizations to control who can access AWS resources and what actions they can perform. IAM Users represent individuals, Policies define permissions, Groups simplify permission management, Roles provide temporary secure access, and MFA strengthens authentication. Implementing IAM correctly is essential for building secure, scalable, and compliant AWS environments.
