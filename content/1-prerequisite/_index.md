+++
title = "Preparation steps"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Overview

This exercise is part of the Landing Zone practice.

To prepare the necessary resources, you will create an AWS Organization, with 4 Organization Units to group the accounts. Create AWS Accounts with names: **Security**, **Shared Services**, **Logging** and **Application** and add the Accounts to each respective OU.

The created accounts will be allocated the following resources (*Note: you only refer to this section as it is beyond the scope of the lab*):
- **Logging Account:** A centralized place for Amazon VPC Flow Logs, CloudTrail logs, and Config logs.
- **Security Account**: Gather AWS Config, Amazon GuardDuty master, and alerts.
- **Network/Shared Services Account:** Share a VPC for remote connections to other accounts. The primary AWS Direct Connect is installed with the AWS Transit Gateway to communicate with VPCs in other accounts.
- **Business Unit accounts:** accounts for Analytics-Prod, and Analytics-non-prod.

![Lab Diagram](/images/1/1.png?width=70pc)

#### Content
1. [Create AWS Account in AWS Organization](1-create-aws-account)
2. [Setting up Organization Unit](2-configure-OU)
3. [Invite AWS Account to AWS Organization](2-configure-OU)
4. [Access member account in Organization](4-switch-role)