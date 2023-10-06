+++
title = "Create Permission Set"
date = 2021
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Permission Set

A **Permission Set** defines the level of access that Users and Groups have within AWS accounts in the AWS Organization. These permission sets are stored in AWS Single Sign-On (SSO) and are provided to AWS accounts as IAM roles. Multiple permissions can be assigned to a single User.

1. To begin, follow these steps:
   - Open the AWS SSO Console.
   - Choose "AWS accounts" from the left sidebar.
   - Navigate to the **Permission sets** tab.
   - Click on **Create permission set**.

![AWS Account](/images/7/0001.png?featherlight=false&width=90pc)

2. On the "Create new permission set" page:
   - Select the desired **Permission set type**.

![AWS Account](/images/7/0002.png?featherlight=false&width=90pc)

3. Choose **AdministratorAccess** to grant comprehensive access to AWS resources and services.

![AWS Account](/images/7/0003.png?featherlight=false&width=90pc)

4. Provide the name as **AdministratorAccess** and proceed by selecting **Next**.

![AWS Account](/images/7/0004.png?featherlight=false&width=90pc)

5. Review your choices and confirm by selecting **Create**.

![AWS Account](/images/7/0005.png?featherlight=false&width=90pc)

6. This completes the creation of the **Permission set**.

![AWS Account](/images/7/0006.png?featherlight=false&width=90pc)

7. To configure the Permission Set with **SecurityAudit** permissions, repeat the above steps. The result will be displayed as shown below:

![AWS Account](/images/7/0007.png?featherlight=false&width=90pc)
