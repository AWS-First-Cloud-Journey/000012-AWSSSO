+++
title = "Preparation steps"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Overview

This exercise is a part of the Landing Zone practice.

To set up the required resources, you will establish an AWS Organization with four Organization Units (OUs) for grouping the accounts. Create AWS Accounts with the following names: **Security**, **Shared Services**, **Logging**, and **Application**. Then, assign each account to its respective OU.

These created accounts will be allocated the following resources (Note: Refer to this section only as it is beyond the scope of the lab):

- **Logging Account:** This serves as a centralized repository for Amazon VPC Flow Logs, CloudTrail logs, and Config logs.

- **Security Account:** Here, you will collect AWS Config data, set up an Amazon GuardDuty master, and configure alerts.

- **Network/Shared Services Account:** This account will host a shared VPC, facilitating remote connections to other accounts. The primary AWS Direct Connect is integrated with the AWS Transit Gateway to establish communication with VPCs in other accounts.

- **Business Unit Accounts:** These accounts cater to Analytics-Prod and Analytics-non-prod needs.

![Lab Diagram](/images/1/1.png?width=70pc)

#### Content

1. [Create AWS Account in AWS Organization](1-create-aws-account)
2. [Setting up Organization Unit](2-configure-OU)
3. [Invite AWS Account to AWS Organization](2-configure-OU)
4. [Access Member Account in Organization](4-switch-role)
