+++
title = "Setting Up AWS SSO"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

In this step, you can grant users in your directory with SSO access to one or more AWS consoles for specific AWS accounts in your AWS organization. Afterward, users see only the AWS account icon (for example, Development) that they've been assigned from within their user portal. When they click the icon, they can then choose which IAM role they want to use when signing in to the AWS Management Console for that AWS account.

**Contents**
- [1. Enable AWS SSO](#1-enable-aws-sso)
- [2. Add Users and Groups](#2-add-users-and-groups)
- [3. Permission Sets](#3-permission-sets)
- [4. To assign access to users or groups](#4-to-assign-access-to-users-or-groups)

#### 1. Enable AWS SSO
1. Sign in to the **AWS Management Console** with your **AWS Organizations** master account credentials.
2. Open the **AWS SSO console**.
3. Choose **Enable AWS SSO**. 

![Enable AWS SSO](../../../images/2/1.png?width=90pc)

4. Choosing an identity source determines where AWS SSO looks for users and groups that need SSO access. By default, you get an AWS SSO store for quick and easy user management.

![Enable AWS SSO](../../../images/2/2.png?width=90pc)

{{% notice info %}}
AWS Single Sign-On provides you with a default store where you can store your users and groups. If you choose to store them in AWS SSO, all you need to do is the following: 
- Create your users and groups.
- Add your users as members to the groups. 
- Assign the groups with the desired level of access to your AWS accounts and applications. 
{{% /notice %}}

5. Users and groups that you create in your AWS SSO store are available in AWS SSO only. Use the following procedure to add users to your AWS SSO store. 

#### 2. Add Users and Groups

1. Open the **AWS SSO console**. Choose **Users**. 

![Add Users and Groups](../../../images/2/3.png?width=90pc)

2. Choose **Add user** and provide the following required information: 
   - **Username** – This user name will be required to sign in to the user portal and cannot be changed later. 
   - **Password** – Choose from one of the following choices to send the user's password. 
     - **Send an email to the user with password setup instructions** – This option automatically sends the user an email addressed from Amazon Web Services. The email invites the user on behalf of your company to access the AWS SSO user portal. 
     - **Generate a one-time password that you can share with the user** – This option provides you with the user portal URL and password details that you can manually send to the user from your email address. 
   - **Email address**
   - **Confirm email address**
   - For clarity, use prefix of **User logon name** as the **First name** and **suffix** as the **Last name**, e.g. for Super-User, Super will be the First name, while User will be the Last name Display name
3. Choose **Next: Groups**. 

![Add Users and Groups](../../../images/2/4.png?width=90pc)

4. Select one or more groups that you want the user to be a member of. Then choose **Add user**. 

![Add Users and Groups](../../../images/2/5.png?width=90pc)

5. We need to create the following users and groups:

| User logon name |                                                                      Group                                                                      |
|:---------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------:|
| Super-User      | AWS-Shared-Services-Admin; AWS-Shared-Services-Read-Only; AWS-Security-Admin; AWS-Security-Read-Only; AWS-Logging-Admin; AWS-Logging-Read-Only; |
| Security-User   | AWS-Security-Read-Only                                                                                                                          |

![Add Users and Groups](../../../images/2/6.png?width=90pc)

#### 3. Permission Sets
Permission sets define the level of access that users and groups have to an AWS account. Permission sets are stored in AWS SSO and provisioned to the AWS account as IAM roles. You can assign more than one permission set to a user

1. Open the **AWS SSO console**
2. Choose **AWS accounts**. 

![Permission Sets](../../../images/2/7.png?width=90pc)

3. Select the **Permission sets** tab. 
4. Choose **Create permission set**. 

![Permission Sets](../../../images/2/8.png?width=90pc)

5. On the **Create new permission set** page, choose from one of the following options, and then follow the instructions provided under that option:
   - **Use an existing job function policy**. Under **Select job function policy**, select one of the default IAM job function policies in the list. For more information, see [AWS Managed Policies for Job Functions](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html). 
   - Choose **AdministratorAccess** to provides full access to AWS services and resources. Choose **Create**. 
   - Choose **SecurityAudit** to Provides Read-Only access to AWS services and resources. Choose **Create**. 

![Permission Sets](../../../images/2/9.png?width=90pc)

![Permission Sets](../../../images/2/10.png?width=90pc)

#### 4. To assign access to users or groups
1. Open the **AWS SSO console**
2. Choose **AWS accounts**. 

![Assign access to users or groups](../../../images/2/11.png?width=90pc)

3. Under the **AWS organization** tab, in the list of AWS accounts, choose one or more accounts to which you want to assign access. 
4. On the AWS account details page, choose **Assign users**.

![Assign access to users or groups](../../../images/2/12.png?width=90pc) 

5. On the Select users or groups page, type a user or group name and choose **Search connected directory**. Once you have selected all the accounts that you want to assign access to, choose **Next: Permission sets**. You can specify multiple users or groups by selecting the applicable accounts as they appear in search results. 

![Assign access to users or groups](../../../images/2/13.png?width=90pc)

6. On the **Select permission sets** page, select the permission sets that you want to apply to the user or group from the table. Then choose **Finish**. 
7. Choose **Finish** to begin the process of configuring your AWS account. 

![Assign access to users or groups](../../../images/2/14.png?width=90pc)

![Assign access to users or groups](../../../images/2/15.png?width=90pc)

8. The accounts and job function policy as follows:

|                      Accounts                      |                                   Groups                                   | Job function policy |
|:--------------------------------------------------:|:--------------------------------------------------------------------------:|:-------------------:|
| Master Account, shared-services, logging,security  | AWS-Shared-Services-Admin AWS-Security-Admin AWS-Logging-Admin             | AdministratorAccess |
| Master Account, shared-services, logging, security | AWS-Shared-Services-Read-Only AWS-Security-Read-Only AWS-Logging-Read-Only | SecurityAudit       |

![Assign access to users or groups](../../../images/2/16.png?width=90pc)
