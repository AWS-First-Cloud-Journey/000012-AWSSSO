+++
title = "Test"
date = 2021-06-14T22:33:19+07:00
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

#### Accessing AWS Accounts in AWS Organizations through AWS SSO User

In this section, you will learn how to access AWS accounts within AWS Organizations using the AWS SSO User. If you no longer need these resources, you can follow the steps to clean them up.

#### Checking Results

To access AWS accounts within AWS Organizations through AWS SSO User, follow these steps:

1. Open your web browser in incognito mode and navigate to the **User portal URL** link that you saved in the previous section.

   ![User Portal URL](../../../images/2/2_AddUserComplete.png?width=90pc)

   Alternatively, you can store the **User portal URL** in the **set password** section.

   ![AWS Account](/images/9/0001.png?featherlight=false&width=90pc)

2. In the **User Portal**, enter the username and password you saved to log in.

3. If this is your first time accessing the AWS SSO User, you'll need to change the password as you set up in the previous section. Follow the instructions to enter a new password and select **Set new password**.

   ![AWS Account](/images/9/0002.png?featherlight=false&width=90pc)

4. You can now select the AWS account and access rights that were set up in the previous section. For instance, the image below illustrates the account and access permissions that the "Security-User" has. If you log in as "Super-User," you'll have access to **AdministratorAccess** for each account.

   ![AWS Account](/images/9/0003.png?featherlight=false&width=90pc)
   ![AWS Account](/images/9/0004.png?featherlight=false&width=90pc)

5. Click **Management console** to access the AWS console for the "Security" account.

   ![AWS Account](/images/9/0004.png?featherlight=false&width=90pc)

6. Congratulations! You've successfully accessed your account.

   ![AWS Account](/images/9/0005.png?featherlight=false&width=90pc)

7. For **CLI** access, you can choose **Command line or programmatic access**, which will display SSO configuration instructions.

   ![AWS Account](/images/9/0006.png?featherlight=false&width=90pc)

8. Depending on your operating system, open either the Command Prompt (CMD) or PowerShell to perform the configuration.

   ![AWS Account](/images/9/0007.png?featherlight=false&width=90pc)
