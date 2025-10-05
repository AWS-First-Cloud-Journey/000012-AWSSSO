+++
title = "Manually Refresh Credentials"
date = 2025
weight = 1
chapter = false
pre = "<b> 2.1 </b>"
+++

#### Configure AWS CLI - Manually Refresh Credentials

**ℹ️ Information:** In this section, we will guide you on how to manually configure the AWS CLI to authenticate users with AWS IAM Identity Center. With this method, you must manually refresh temporary credentials when they expire.

#### Prerequisites

1. Install the latest version of AWS CLI. For more information, see [Install or update to the latest version of the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).
2. You must have authenticated SSO access in IAM Identity Center.

#### Manual Configuration Process

1. Sign in to the AWS Access Portal using the login URL provided for your organization.

![3.4.11](/images/0002/1.png)

2. In the **Accounts** tab or by selecting the AWS account icon, identify the AWS account you want to access.

![3.4.11](/images/0002/2.png)

3. Expand the account to display the available IAM roles (for example: AdministratorAccess, readOnly).

![3.4.11](/images/0002/3.png)

4. Next to the desired IAM role, select **Access keys** to obtain temporary credentials.

![3.4.11](/images/0002/4.png)

**ℹ️ Information:** AWS Access Portal is a centralized interface for managing access to all AWS accounts in your organization through IAM Identity Center.

#### Using Temporary Credentials

In the **Get credentials** dialog box, you have three options to use the credentials:

**Option 1: Set AWS Environment Variables**
- Choose your operating system (MacOS and Linux, Windows, or PowerShell)
- Copy the provided commands to the clipboard

![3.4.11](/images/0002/5.png)

- Paste and execute the commands in the terminal to set environment variables

![3.4.11](/images/0002/6.png)

- Verify again whether the CLI has received the credentials  
aws sts get-caller-identity  
![3.4.11](/images/0002/8.png)  
- These variables override all existing credential configurations in the current terminal session, meaning the CLI has been successfully authenticated using temporary credentials  
![3.4.11](/images/0002/9.png)  
![3.4.11](/images/0002/10.png)  
**💡 Pro Tip:** Use this option when you need to quickly switch between different roles within the same working session.

**Option 2: Add a profile to the AWS credentials file**
- Copy the provided commands
- Paste them into the ~/.aws/credentials file to create a new named profile
- Use this profile with the --profile option in AWS CLI commands
- Example: aws s3 ls --profile sso-admin-profile

**🔒 Security Note:** Named profiles allow you to maintain multiple sets of credentials at the same time and minimize the risk of using the wrong permissions when performing AWS CLI operations.

**Option 3: Use individual values in AWS service client**
- Copy the individual credential values (AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_SESSION_TOKEN)
- Integrate these values into your application code when using AWS SDK

**⚠️ Warning:** Temporary credentials have a limited validity period, usually 1 hour. When they expire, you need to repeat the process to obtain new credentials. Temporary credentials should not be stored in long-term configuration files or version control systems.
