+++
title = "Create AWS Account in AWS Organizations"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1 </b>"
+++


#### Creating AWS Accounts in AWS Organization

In this step, you will practice creating AWS accounts for **Security**, **Shared Services**, **Logging**, and **Application** within the AWS Organization service. AWS accounts created within the AWS Organization can only be accessed using the IAM Role or root user information.

#### Contents
- [Creating AWS Accounts in AWS Organization](#creating-aws-accounts-in-aws-organization)
- [Contents](#contents)
- [Create AWS Account in AWS Organization](#create-aws-account-in-aws-organization)

#### Create AWS Account in AWS Organization

1. Go to the **AWS Management Console** and search for the **AWS Organizations** service.

   ![AWS Organizations](/images/1/0001.png?featherlight=false&width=90pc)
   ![AWS Organizations](/images/1/0002.png?featherlight=false&width=90pc)

2. In the **AWS Organizations Console**, click on **Add an AWS account**.

   ![Add AWS Account](/images/1/0003.png?featherlight=false&width=90pc)

3. Select **Create an AWS account** and provide the following details:
   - **AWS account name**: Logging
   - **Email address of the account's owner**: example+lab12Logging@amazon.com.vn

   ![Create AWS Account](/images/4/0002.png?featherlight=false&width=90pc)

   > **Note**: To create multiple AWS accounts with the same email, you can modify your email by adding a **"+"** followed by a description.

   - **IAM role name**: Leave the default as **OrganizationAccountAccessRole**. This role name will be used to access your AWS member account through the [role switch] method.

   ![IAM Role](/images/4/0002.png?featherlight=false&width=90pc)

4. Review the provided information and then select **Create AWS account**.

   ![Create AWS Account](/images/4/0002.png?featherlight=false&width=90pc)

5. Repeat the above steps to create accounts for **Security**, **Shared Services**, and **Application**. Depending on individual or business requirements, you can create as many accounts as needed.

   > **Note**: If the email address used to create your AWS Account already exists, AWS will respond with the reason "EMAIL ALREADY EXISTS" in the **Failure reason** section under **Requests**.

   ![Requests](/images/10/001.png?featherlight=false&width=90pc)
   ![Failure Reason](/images/10/002.png?featherlight=false&width=90pc)
