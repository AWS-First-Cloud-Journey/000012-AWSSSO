+++
title = "Test"
date = 2021-06-14T22:33:19+07:00
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

In this section, you'll try accessing AWS accounts in AWS Organizations through the AWS SSO User. You can then proceed to clean up the resources if you no longer need them.

#### Check results
You will try accessing AWS accounts in AWS Organizations through AWS SSO User
1. Open your browser in incognito mode and go to the **User portal URL** link you saved in the previous section.


![AddUserGroups](../../../images/2/2_AddUserComplete.png?width=90pc)

Or store **User portal URL** at **set password**

![AWS Account](/images/9/0001.png?featherlight=false&width=90pc)

2. In **User Portal**, enter the saved username and password to login.

3. If you are accessing the AWWS SSO User for the first time, you will have to change the password first as you set up in the previous section. Enter the new password according to the instructions and select **Set new password**.

![AWS Account](/images/9/0002.png?featherlight=false&width=90pc)

4. You will be able to select the AWS account and access rights set up in the previous section. (For example, the figure below shows the account and the access permissions that Security-User can use. If you log in to Super-User, you will be able to access **AdministratorAccess** for each account)

![AWS Account](/images/9/0003.png?featherlight=false&width=90pc)

![AWS Account](/images/9/0004.png?featherlight=false&width=90pc)

5. Select **Management console** to access the **Security** account's AWS console.

![AWS Account](/images/9/0004.png?featherlight=false&width=90pc)

6. Congratulations, you have successfully accessed your account.

![AWS Account](/images/9/0005.png?featherlight=false&width=90pc)

7. For **CLI** you can choose **Command line or programmatic access**. Displays SSO configuration instructions.

![AWS Account](/images/9/0006.png?featherlight=false&width=90pc)

8. Open CMD or PowerShell according to the operating system to configure.

![AWS Account](/images/9/0007.png?featherlight=false&width=90pc)