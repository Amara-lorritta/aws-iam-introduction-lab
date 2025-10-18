## **Introduction to AWS Identity and Access Management (IAM)**

## **Overview**

This hands-on lab demonstrates how to manage users, groups, and permissions using AWS Identity and Access Management (IAM) — the core service for securing access to AWS resources.
Through this exercise, I created and enforced a custom password policy, assigned users to functional groups, attached managed and inline policies, and validated access permissions via the IAM Sign-In Portal.

## **Objectives & Learning Outcomes**

By completing this lab, I learned to:

Create and enforce an IAM password policy

Explore created users and user groups

Analyze managed and inline IAM policies

Assign users to groups with specific access levels

Use IAM sign-in URLs for controlled logins

Test policy effects and permission boundaries


## **Architecture**

Flow:
User (Administrator) → AWS IAM → User Groups → IAM Users → AWS Services (EC2 / S3)

<img width="600" height="800" alt="8e6d1483-15b2-404b-b73c-340275d61a24" src="https://github.com/user-attachments/assets/4da5742f-30eb-4ef9-a777-f5457e5462c6" />



Group and Role Relationships:

S3-Support → AmazonS3ReadOnlyAccess

EC2-Support → AmazonEC2ReadOnlyAccess

EC2-Admin → Custom Inline Policy (Start/Stop EC2 Instances)

IAM Access Behavior:

user-1 → View S3 only

user-2 → View EC2 only (read-only)

user-3 → Start/Stop EC2 instances


## **Commands and Steps**

```bash
# Step 1: Create a custom password policy
# Enforce minimum length and complexity for all IAM users
- Minimum length: 10
- Require uppercase, lowercase, number, and special character
- Enable 90-day expiration and password reuse prevention

# Step 2: Review existing IAM users
# Users already created
user-1
user-2
user-3

# Step 3: Review IAM groups and their policies
# Groups and attached policies
EC2-Admin      → Inline policy (Start/Stop EC2)
EC2-Support    → AmazonEC2ReadOnlyAccess
S3-Support     → AmazonS3ReadOnlyAccess

# Step 4: Add users to appropriate groups
# Map users according to functional roles
user-1 → S3-Support
user-2 → EC2-Support
user-3 → EC2-Admin

# Step 5: Test permissions using IAM Sign-in URL
# Each user signs in to the console with role-specific access
https://<ACCOUNT_ID>.signin.aws.amazon.com/console

# Step 6: Validate access control
user-1 → Can list S3 buckets only
user-2 → Can view EC2 instances (no start/stop)
user-3 → Can start/stop EC2 instances
```


## **Screenshots**

Screenshot Name	Description

PasswordPolicy.png	Custom password policy created with strict requirements.

IAMUsers.png	Displays pre-created users (user-1, user-2, user-3).

IAMGroups.png	Shows IAM groups and associated managed/inline policies.

GroupPolicies.png	Managed and inline policies defining access boundaries.

UserGroupMapping.png	Users successfully assigned to their respective groups.

IAMSigninURL.png	IAM console sign-in portal used to test user access.

AccessTest.png	Permissions validation: users restricted by role-based policies.

## **Tools Used**

AWS IAM

AWS Management Console

IAM Policies (Managed & Inline)

IAM Sign-in URL


## **What Actually Happened**

Created and enforced a strong password policy across all IAM users.

Explored users and groups to understand access structure.

Reviewed and compared managed policies vs. inline policies.

Mapped each user to the correct group according to their job role.

Signed in via IAM Sign-In URL for each user to verify permissions.

Observed least-privilege access:

S3 support → Read-only

EC2 support → View only

EC2 admin → Start/stop EC2 instances

## **Author**

Amarachi Emeziem

Cloud Security & Cloud Support Specialist | AWS & Azure Certified
