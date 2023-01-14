+++
title = "Create Permission Set"
date = 2021
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Permission Set
**Permission Set** defines the access that Users and Groups have to AWS accounts in the AWS Organization. Permission sets are stored in AWS SSO and provided to AWS accounts as IAM roles. You can assign multiple permissions to a User.

1. Open the AWS SSO Console. Select AWS accounts in the left sidebar.
- Select the **Permissionssets** tab.
- Select **Create permission set**.

![AWS Account](/images/7/0001.png?featherlight=false&width=90pc)

2. On the Create new permission set page:

- Select **Permission set type**

![AWS Account](/images/7/0002.png?featherlight=false&width=90pc)

3. Select **AdministratorAccess** to provide full access to AWS resources and services.

![AWS Account](/images/7/0003.png?featherlight=false&width=90pc)

4. Enter **AdministratorAccess** and select **Next**

![AWS Account](/images/7/0004.png?featherlight=false&width=90pc)

5. Check and select **Create**

![AWS Account](/images/7/0005.png?featherlight=false&width=90pc)

6. Complete creation **Permission set**

![AWS Account](/images/7/0006.png?featherlight=false&width=90pc)

7. Repeat the above steps to set the Permission Set with SecurityAudit permission. You will get the result as shown below

![AWS Account](/images/7/0007.png?featherlight=false&width=90pc)

