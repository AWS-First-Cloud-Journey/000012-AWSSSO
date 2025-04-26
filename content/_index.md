+++  
title = "Using AWS IAM Identity Center for Robust Identity Management"  
date = 2024  
weight = 1  
chapter = false  
+++  

# Using AWS IAM Identity Center for Robust Identity Management

#### Introduction

**ℹ️ Information:** This workshop is designed to help you become familiar with AWS IAM Identity Center (formerly AWS Single Sign-On) to effectively manage your organization's employee identities across multiple AWS accounts.

#### Scenario

Your company is new to cloud computing and planning to build systems on AWS. The company wants to enforce robust security access controls in a centralized and scalable manner.

As a cloud administrator, you've been tasked with setting up access to AWS accounts for company employees following the principle of least privilege. During configuration, you're responsible for setting up IAM Identity Center and providing access to AWS accounts based on users' group membership and project/team roles.

#### Overview

- **Level:** Intermediate
- **Duration:** 1-3 hours
- **NIST Cybersecurity Framework (CSF) Function:** Identify
- **AWS Cloud Adoption Framework (CAF) Component:** Directive
- **Cost:** 

**💡 Pro Tip:** There are no costs associated with IAM Identity Center and AWS Organizations. For other services, most costs incurred in this workshop are covered under the free tier for specific services in your AWS account (e.g., Amazon EC2). However, some costs related to data storage (e.g., AWS CloudTrail logs) may be incurred. You should clean up your environment by following the instructions in the Cleanup section after completing the workshop to avoid additional costs.

- **Supported Regions:** 

**ℹ️ Information:** It's recommended to run this workshop in the us-east-1 Region.

- **Target Audience:** Cloud and IT Administrators
- **Prerequisites:**
  - AWS account not yet part of AWS Organizations
  - IAM user with administrative permissions for that account

**⚠️ Warning:** Please launch an Amazon EC2 instance in your new account a few hours before starting this workshop to ensure your account is active and ready for the workshop. If you're attending this workshop at an AWS event such as re:Invent or re:Inforce, you'll be provided with AWS credits to cover workshop-related costs.

**🔒 Security Note:** IAM Identity Center provides centralized access management, helping minimize security risks associated with managing multiple credentials across multiple AWS accounts. Implementing IAM Identity Center is an important part of a Zero Trust strategy and adheres to the principle of least privilege.