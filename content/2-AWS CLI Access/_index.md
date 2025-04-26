+++
title = "AWS CLI"
date = 2020
weight = 2
chapter = false
pre = "<b> 2. </b>"
+++


# AWS CLI Access with IAM Identity Center

## Overview

This guide explains how to authenticate and access AWS resources via the AWS Command Line Interface (CLI) when using IAM Identity Center.

**ℹ️ Information:** AWS Command Line Interface (CLI) provides the ability to interact with AWS services through the command line. When using IAM Identity Center, you can securely authenticate and access AWS resources across multiple accounts.

#### Authentication Overview with IAM Identity Center

When using AWS IAM Identity Center, you can authenticate to the AWS CLI using:
- IAM Identity Center's integrated directory
- An external identity provider connected to IAM Identity Center

After authentication, IAM Identity Center maps your login credentials to the corresponding IAM role to execute AWS CLI commands with appropriate permissions.

#### Credential Refresh Methods

**ℹ️ Information:** There are two main methods for obtaining and refreshing temporary credentials for IAM Identity Center users:

#### 1. Manual Credential Refresh

This method allows you to obtain temporary credentials for a specific IAM role associated with a permission set in an AWS account. The process:

1. Log in to the AWS access portal
2. Select the AWS account and permission set you need to access
3. Copy the provided AWS CLI commands
4. Paste and execute the commands in your terminal to set up credentials

**⚠️ Warning:** Temporary credentials have a limited lifespan (typically 1 hour). You need to repeat this process when credentials expire.

#### 2. Automatic Credential Refresh (Recommended)

**💡 Pro Tip:** This method uses the Open ID Connect (OIDC) standard with Device Code Authorization, providing a more seamless and secure authentication experience.

The process:
1. Configure AWS CLI with the `aws configure sso` command
2. Provide the IAM Identity Center URL and AWS Region
3. Authenticate through a web browser
4. Select the AWS account and IAM role to access
5. AWS CLI will automatically refresh credentials when needed

**🔒 Security Note:** The automatic refresh method not only improves user experience but also enhances security by:
- Eliminating the need to copy/paste sensitive credentials
- Automatically managing credential lifecycle
- Supporting integrated multi-factor authentication (MFA)
- Adhering to Zero Trust principles with short-lived sessions

**ℹ️ Information:** From AWS CLI v2.9.0 and above, you can use the SSO configuration file (`~/.aws/config`) to store multiple profiles for different AWS accounts and permission sets, allowing quick switching between different roles.