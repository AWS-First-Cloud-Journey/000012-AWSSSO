+++
title = "Assign permissions"
date = 2021
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++


#### Assign access rights to Users and Groups

You need to set up AWS accounts in SSO groups with the following job functionality:


|                      Accounts                      |                                   Groups                                   | Job function policy |
|:--------------------------------------------------:|:--------------------------------------------------------------------------:|:-------------------:|
| Management Account, shared-services, logging,security  | AWS-Shared-Services-Admin; AWS-Security-Admin; AWS-Logging-Admin             | AdministratorAccess |
| Management Account, shared-services, logging, security | AWS-Shared-Services-Read-Only; AWS-Security-Read-Only; AWS-Logging-Read-Only | SecurityAudit       |

1. Open the AWS SSO Console. Select AWS accounts in the left sidebar.

- In the AWS organization tab, in the list of AWS accounts, select one or more accounts to which you want to assign access. (Example: Management Account, shared-services, logging, and security). Then select **Assign users or groups**

![AWS Account](/images/8/0001.png?featherlight=false&width=90pc)

2. Select the groups and select **Next**

![AWS Account](/images/8/00011.png?featherlight=false&width=90pc)

3. Select **Permission set**

![AWS Account](/images/8/00012.png?featherlight=false&width=90pc)

4. Select **Submit**

![AWS Account](/images/8/00013.png?featherlight=false&width=90pc)


5. Same, For **Security Account**

![AWS Account](/images/8/0006.png?featherlight=false&width=90pc)

6. Select the groups and select **Next**

![AWS Account](/images/8/0007.png?featherlight=false&width=90pc)

7. Select **Permission set** and select **Next**

![AWS Account](/images/8/0008.png?featherlight=false&width=90pc)

8. Select **Submit**

![AWS Account](/images/8/0009.png?featherlight=false&width=90pc)

9. Congratulations, you have successfully set up AWS SSO.

![AWS Account](/images/8/00010.png?featherlight=false&width=90pc)