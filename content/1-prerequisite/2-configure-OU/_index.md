+++
title = "Prerequisites for IAM Identity Center"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++

#### Prerequisites for IAM Identity Center

**ℹ️ Information:** You can skip this section if you have already activated IAM Identity Center in the AWS Account you are using for this workshop.

#### Basic Requirements

Before setting up IAM Identity Center, you need:

1. An AWS account with Administrator permissions. If you don’t have one, create an account now.

2. Set up AWS Organizations and enable the **All features** mode. For more details on this configuration, see “Enabling All Features in Your Organization” in the AWS Organizations User Guide.

#### Enabling AWS Organizations

**ℹ️ Information:** AWS Organizations is an account management service that allows you to consolidate multiple AWS accounts into a single organization that you create and centrally manage. This is a prerequisite for using IAM Identity Center.

1. In the AWS Management Console, at the top left corner next to **Services**, click the search box, type **AWS Organizations**, and select the service.

2. Click **Create Organization**. By default, the organization is created with all features enabled.

![3.4.11](/images/0001/image05.png)

3. The organization is created, and the AWS accounts page appears. The only account currently available is your management account, which is located under the root organizational unit (OU).

**💡 Pro Tip:** AWS Organizations allows you to centrally manage multiple AWS accounts, simplifying billing, access control, and compliance with security policies. You should design an OU structure that aligns with your organization’s model to optimize access management.

#### Enabling IAM Identity Center

**ℹ️ Information:** IAM Identity Center (formerly AWS SSO) is a centralized identity and access management service for AWS accounts and cloud applications. It simplifies access control and provides a single sign-on (SSO) experience for users.

When you open IAM Identity Center for the first time, you’ll be prompted to enable the service before managing it:

1. In the AWS Management Console, click **Services** in the upper-left corner.  
2. Open the **IAM Identity Center** console.  
3. Choose **Enable**.  

![3.4.11](/images/0001/0004.png)

**ℹ️ Information:** After activation, IAM Identity Center creates a service-linked role in all accounts within your AWS Organization. It also automatically creates the same service-linked role in any new accounts that are added to your organization later. This role allows IAM Identity Center to access each account’s resources on your behalf.

#### Delegated Administration

**🔒 Security Note:** IAM Identity Center allows you to designate another member account within your AWS Organization — other than the Organization Management Account — to perform administrative tasks for Identity Center. This supports the **principle of least privilege** by reducing direct access to the Management Account. In production environments, you should configure delegated administration to minimize security risks associated with using the Management Account for day-to-day operations.

**💡 Pro Tip:** When setting up IAM Identity Center, consider an identity strategy that best fits your organization. You can choose to use the **Identity Center Directory**, connect to **Microsoft Active Directory** via **AWS Directory Service**, or integrate with an external identity provider (IdP) that supports **SAML 2.0** such as **Okta**, **Azure AD**, or **Google Workspace**.
