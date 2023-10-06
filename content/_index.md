+++
title = "AWS Single Sign-On"
date = 2020
weight = 1
chapter = false
+++

# AWS Single Sign-On for Organization

#### Overview

In this lab, you will learn how to set up the **AWS SSO** service to efficiently provision and manage resource access to your **AWS Organization** AWS accounts.

#### AWS Single Sign-On (SSO)

**AWS SSO** is a service that enables you to provide Single Sign-On access to one or more AWS accounts within your AWS Organization for users listed in your directory.

#### AWS Organization

**AWS Organization** is a service designed for managing multiple AWS accounts within your organization from a central standpoint. With AWS Organization, you can organize AWS Accounts into **Organizational Units** and aggregate the expenses of all AWS accounts into a **Management Account**.

#### Organizational Unit (OU)

An **Organizational Unit** is a collection of AWS accounts. Each OU can have up to five levels of nested OUs. Management policies assigned to an OU are applied to all its member OUs and AWS accounts.

#### Management Account

The **Management Account** is the AWS account with the highest level of permissions. It possesses the authority to control all other AWS accounts within the AWS Organization. Additionally, the management account bears the responsibility for covering the general costs incurred by its member accounts.

#### Content

1. [Preparatory steps](1-prerequisite)
2. [AWS SSO Setup](2-setup-aws-sso)
3. [Check Results & Clean Up Resources](3-clean-up)
