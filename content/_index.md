+++
title = "AWS Single Sign-On"
date = 2020
weight = 1
chapter = false
+++

# AWS Single Sign-On for Organization

#### Overview

In this lab, you'll practice setting up the **AWS SSO** service to easily provision and manage resource access to your **AWS Organization** AWS accounts.

#### AWS Single Sign-On (SSO)

**AWS SSO** is a service that allows you to grant users in your directory (*directory*) SSO access to one or more AWS accounts in the AWS Organization.

#### AWS Organization

**AWS Organization** is an account management service that allows you to centrally manage multiple AWS accounts in your organization. With AWS Organization, you can group AWS Accounts into **Organizational Units** and aggregate the costs of all AWS accounts into **Management Account**.

#### Organizational Unit (OU)

**Organizational Unit** is a group of AWS accounts. An OU can contain up to 5 layers of nested OUs within it. You can assign management policies to an OU, and it will apply to all member OUs and member AWS accounts.

#### Management Account

**Management Account** is the AWS account with the highest permissions and can control all other AWS accounts in an AWS Organization. The management account is also responsible for paying the general costs of member accounts.

#### Content
1. [Preparatory steps](1-prerequisite)
2. [AWS SSO Setup](2-setup-aws-sso)
3. [Check Results & Clean Up Resources](3-clean-up)