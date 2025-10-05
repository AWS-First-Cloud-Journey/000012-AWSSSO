+++
title = "Automatic Credential Refresh"
date = 2025
weight = 2
chapter = false
pre = "<b> 2.2 </b>"
+++

#### Configuring AWS CLI - Automatic Credential Refresh

**ℹ️ Information:** This section describes how to configure AWS CLI with automatic credential refresh to authenticate users with AWS IAM Identity Center. This method uses the Open ID Connect (OIDC) standard with Device Code Authorization, allowing you to initialize access directly via the `aws configure sso` command in the AWS CLI.

#### Configure User Profiles

**ℹ️ Information:** Using the auto-refresh-credentials method, we will configure two profiles:

- `adminUser` - Profile with administrative rights

- `readOnlyUser` - Profile with read-only rights

#### Configure adminUser Profile

1. Open a terminal window and run the following command:
```bash
aws configure sso --profile adminUser
```
2. Provide the SSO session name:
```
sso-session-adminUser
```
3. Enter the AWS Gateway URL and select the SSO region:
```
us-east-1
```

4. For the SSO registration scope, provide the value:
```
sso:account:access
```
5. A new browser window will open. Log in as adminUser and follow the authentication steps.

6. Once done, test the configuration using the command:
```bash
aws s3 ls --profile adminUser
```

**💡 Pro Tip:** Use the admin profile (`adminUser`) only when you need to perform operations that require admin privileges such as starting/stopping EC2, creating/deleting AWS resources. This follows the least privilege principle.

#### Check adminUser permissions

Use the adminUser profile to stop an EC2 instance:

1. Get the EC2 instance ID from the AWS Management Console
2. Run the following command (replace [instance-id] with the actual EC2 ID):
```bash
aws ec2 stop-instances --instance-ids [instance-id] --profile adminUser
```

**ℹ️ Info:** With the adminUser profile, you can perform the same administrative operations through the CLI as you would through the AWS Management Console.

#### Configure readOnlyUser profile

1. Open a terminal window and run the following command:
```bash
aws configure sso --profile readOnlyUser
```

2. Provide an SSO session name:
```
sso-session-readOnlyUser
```
3. Enter the AWS Gateway URL and select the SSO region:
```
us-east-1
```

4. For the SSO registration scope, provide the value:
```
sso:account:access
```

5. Follow the authentication steps in a new browser window.

**🔒 Security Note:** Using profiles with appropriate permissions (e.g., readOnlyUser) is an important part of the least privilege security model, helping to minimize the risk of misuse or unauthorized access.

#### Check readOnlyUser permissions

Try stopping an EC2 instance with a readOnlyUser profile:

1. Get the EC2 instance ID from the AWS Management Console
2. Run the following command (replace [instance-id] with the actual EC2 ID):
```bash
aws ec2 stop-instances --instance-ids [instance-id] --profile readOnlyUser
```

![3.4.11](/images/0002/12.png)

**⚠️ Warning:** This command will fail because readOnlyUser does not have permission to stop the EC2. This illustrates that the permissions configuration is working correctly, ensuring users can only perform actions appropriate to their role.

#### Benefits of Integrating IAM Identity Center with AWS CLI

**ℹ️ Info:** Integrating IAM Identity Center with AWS CLI offers many benefits:
- Flexible switching between accounts and roles
- No need to manually manage credentials or profiles
- Automatically refresh credentials
- Optimize development and administration processes when working across multiple AWS environments

#### Managing IAM Identity Center sessions

Once you're done using your IAM Identity Center profile, you can:

- Do nothing and let your AWS temporary credentials and IAM Identity Center credentials expire automatically
- Or run the following command to immediately clear all cached credentials:
```bash
aws sso logout
```

**💡 Pro Tip:** Use the `aws sso logout` command when you need to be safe by clearing all cached credentials, especially when working on shared computers or in security-sensitive environments.

**ℹ️ Info:** To reuse your IAM Identity Center profile after signing out, simply run the AWS CLI command with the corresponding `--profile` parameter, and the system will automatically ask you to authenticate again.