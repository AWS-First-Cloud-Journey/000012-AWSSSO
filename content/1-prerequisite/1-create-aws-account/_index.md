+++
title = "Create AWS Account in AWS Organizations"
date = 2025
weight = 1
chapter = false
pre = "<b>1.1 </b>"
+++

#### Setting up AWS Account

#### Choosing AWS Account for the Workshop

**ℹ️ Information:** To perform this workshop, you need a standalone AWS account that is **not** part of AWS Organizations. AWS IAM Identity Center (formerly AWS Single Sign-On) requires an independent account to be configured as the Management Account.

#### Using an Existing AWS Account

**ℹ️ Information:** If you are using an existing account — whether a personal or company account — make sure you clearly understand the impacts and organizational policies related to resource provisioning in that account.

**💡 Pro Tip:** If you already have an AWS account that is not part of AWS Organizations and are using an IAM User or IAM Role with Administrator privileges, you can skip the rest of this task and move on to the next one.

**ℹ️ Information 2025:** AWS IAM Identity Center now supports integration with Amazon Q Developer, Amazon QuickSight, and other modern AWS services. The service itself is completely free; you only pay for the underlying AWS resources you use.

#### Creating a New AWS Account

If you don’t have an AWS account yet, you can create your own [here](https://portal.aws.amazon.com/billing/signup). A payment method, usually a credit card, is required to activate the account for these hands-on exercises. The registration process includes a phone call where you’ll need to enter a verification code using your phone keypad.

**⚠️ Warning:** If you are currently signed in to the AWS Management Console, you must sign out before [clicking here](https://portal.aws.amazon.com/billing/signup) to create a new AWS account.

#### Preparing an IAM User for the Workshop

**🔒 Security Note:** Strictly limiting the use of the default root account that comes with every AWS account is considered best practice under the principle of least privilege. If you have an AWS account but no IAM User or Role to work with, follow the steps below to prepare for the workshop.

1. Sign in to your AWS account

## Create a User in AWS IAM

- Go to **IAM → Users → Create user**
![3.4.11](/images/0001/image02.png)

2. Enter information as shown below:
- **User name**: Choose an easy-to-remember name, e.g. `adminUser`.    
- **Are you providing console access to a person?** → Select  
  - Choose *I want to create an IAM user* (create a traditional IAM user).  
- **Console password**:  
  - Choose *Custom password* to set your own password.    
- Click **Next** to proceed to the permissions step.  
![3.4.11](/images/0001/image01.png)

3. Assign Permissions to the User

- In the search box, type **AdministratorAccess**.  
- Select **AdministratorAccess** (an AWS managed policy).  
  - This policy grants full administrative access, suitable when you need the user to have the highest privileges (similar to an admin account).  
- Click **Attach policies** to grant the permissions. 
![3.4.11](/images/0001/image03.png)

4. Click **Create user** to finish. 
![3.4.11](/images/0001/image04.png)

⚠️ Note: If you do not want the user to have full admin rights, you can choose more restrictive policies (e.g., only for S3, EC2, etc.).  

**💡 Pro Tip:** When setting up an IAM User with Administrator privileges, make sure to store your credentials securely and enable Multi-Factor Authentication (MFA) to enhance the security of your account. MFA is an important additional security layer in a Zero Trust model.

**🔒 Security Note:** In a real production environment, you should apply the principle of least privilege by granting only the minimum permissions necessary for each IAM User instead of AdministratorAccess. AWS IAM Identity Center supports implementing a Zero Trust strategy with features such as Attribute-Based Access Control (ABAC), integration with Identity Providers (Microsoft Entra ID, Okta), and automatic session management. However, for the purpose of this workshop, Administrator privileges are required to configure AWS IAM Identity Center.
