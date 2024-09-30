+++
title = "Preparation steps"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Preparation Steps for AWS Landing Zone Deployment

#### Overview

This guide outlines the setup process for creating a Landing Zone using AWS Organizations. It will help you structure your AWS accounts and resources for a well-architected multi-account environment. The primary focus is to create and organize four Organizational Units (OUs), establish core accounts, and implement cross-account communication strategies.

By the end of this exercise, you will have:

- A functional **AWS Organization** with:
  - Four **Organization Units (OUs)**: **Security**, **Shared Services**, **Logging**, and **Application**.
  - Each OU will group its designated AWS accounts.
- **AWS Accounts** created with the following purposes:
  - **Security Account** for centralized security management.
  - **Shared Services Account** for shared networking and management services.
  - **Logging Account** to consolidate AWS CloudTrail, Config, and VPC Flow Logs.
  - **Application Account** for specific business unit workloads.

These foundational steps will enable governance, security controls, and cost management within your AWS environment.

#### Target Accounts and Resources

- **Logging Account**: 
  - This serves as a centralized repository for storing Amazon VPC Flow Logs, AWS CloudTrail logs, and AWS Config data.
  
- **Security Account**:
  - Host a **GuardDuty master account**, manage AWS Security Hub, and aggregate security alerts.
  
- **Shared Services Account**:
  - Provision a shared VPC for resource access across accounts.
  - Establish AWS Direct Connect, Transit Gateway, and other shared network resources.

- **Application Accounts**:
  - Business unit-specific accounts for production and non-production workloads.
  - Analytics, Dev/Test, and other application-specific resources.

#### Lab Architecture Diagram
![Lab Diagram](/images/1/1.png?width=70pc)

#### Steps to Implement

1. **[Create AWS Account in AWS Organization](1-create-aws-account)**:
   - Establish the core accounts (`Security`, `Shared Services`, `Logging`, and `Application`) under your AWS Organization.
   - Use the AWS Management Console or AWS CLI to automate account creation and structure.

2. **[Setting up Organization Unit](2-configure-OU)**:
   - Configure Organization Units (OUs) for logical grouping.
   - Create policies to enforce specific security or compliance requirements for each OU.

3. **[Invite Existing AWS Accounts to the AWS Organization](3-invite-aws-account)**:
   - Link any existing accounts to the AWS Organization using an invite process.
   - Validate and assign each account to its corresponding OU.

4. **[Access Member Accounts in the Organization](4-switch-role)**:
   - Enable cross-account access using IAM roles.
   - Set up **AWS SSO** or **IAM Role Switch** to streamline management and operational tasks across accounts.

#### Important Considerations

- **Cost Optimization**: Ensure that each account's usage is tracked separately to optimize billing and monitoring.
- **Security Posture**: Implement security controls, such as SCPs (Service Control Policies) and centralized logging, to maintain compliance.
- **Networking**: Plan for network isolation and interconnectivity using VPC Peering, Transit Gateway, and Direct Connect configurations.

Refer to the AWS [Landing Zone Documentation](https://docs.aws.amazon.com/controltower/latest/userguide/landing-zone.html) for more advanced configurations and best practices.

