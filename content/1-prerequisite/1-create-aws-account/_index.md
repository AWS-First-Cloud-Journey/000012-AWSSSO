+++
title = "Create AWS Account in AWS Organizations"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1 </b>"
+++

In this step, you will practice creating AWS accounts (**Security**, **Shared Services**, **Logging**, and **Application**) inside the AWS Organization service. AWS accounts created within the AWS Organization can only be accessed using the IAM Role or root user information.

**Content**
- [Create AWS Account in AWS Organization](#create-aws-account-in-aws-organization)

#### Create AWS Account in AWS Organization

1. Go to **AWS Management Comsole** and find the **AWS Organizations** service in the search bar.

![AWS Account](/images/1/0001.png?featherlight=false&width=90pc)

![AWS Account](/images/1/0002.png?featherlight=false&width=90pc)

2. At **AWS Organizations Console**, select **Add an AWS account**

![AWS Account](/images/1/0003.png?featherlight=false&width=90pc)

3. Select **Create an AWS account** and enter the following parameters:
    - **AWS account name**: Logging
    - **Email address of the account's owner**: example+lab12Logging@amazon.com.vn

![AWS Account](/images/4/0002.png?featherlight=false&width=90pc)

{{% notice note %}}
To create multiple AWS accounts with the same email, you can take your email name, add a **"+"**, and add a description after it.
{{% /notice %}}

- **IAM role name**: keep default as **OrganizationAccountAccessRole**. This will be the role name that you will use to access your AWS member account via the [role switch] method.

![AWS Account](/images/4/0002.png?featherlight=false&width=90pc)


4. Check the information and select **Create AWS account**


![AWS Account](/images/4/0002.png?featherlight=false&width=90pc)


5. Repeat the above steps for **Security**, **Shared Services**, and **Application** accounts, depending on each individual or business account, you can create as many accounts as you want. limit.