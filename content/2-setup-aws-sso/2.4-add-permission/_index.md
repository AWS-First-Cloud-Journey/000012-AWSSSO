+++
title = "Assign permissions"
date = 2021
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++


#### Assign Access Rights to Users and Groups

To configure access rights for AWS accounts within SSO groups based on specific job functionalities, follow the steps below:

#### Account and Group Configuration

| Accounts                                            | Groups                                                                   | Job Function Policy |
| --------------------------------------------------- | ------------------------------------------------------------------------ | ------------------- |
| Management Account, shared-services, logging,security | AWS-Shared-Services-Admin; AWS-Security-Admin; AWS-Logging-Admin          | AdministratorAccess |
| Management Account, shared-services, logging, security | AWS-Shared-Services-Read-Only; AWS-Security-Read-Only; AWS-Logging-Read-Only | SecurityAudit       |

#### Instructions

1. Open the AWS SSO Console and navigate to the **AWS accounts** section in the left sidebar.

2. In the **AWS organization** tab, locate the list of AWS accounts. Choose one or more accounts to which you want to assign access (e.g., Management Account, shared-services, logging, and security). Then click on **Assign users or groups**.

    ![AWS Account](/images/8/0001.png?featherlight=false&width=90pc)

3. Select the relevant groups and click **Next**.

    ![AWS Account](/images/8/00011.png?featherlight=false&width=90pc)

4. Choose the desired **Permission set**.

    ![AWS Account](/images/8/00012.png?featherlight=false&width=90pc)

5. Click **Submit**.

    ![AWS Account](/images/8/00013.png?featherlight=false&width=90pc)

6. Repeat the same process for the **Security Account**.

    ![AWS Account](/images/8/0006.png?featherlight=false&width=90pc)

7. Select the groups and click **Next**.

    ![AWS Account](/images/8/0007.png?featherlight=false&width=90pc)

8. Choose the **Permission set** and click **Next**.

    ![AWS Account](/images/8/0008.png?featherlight=false&width=90pc)

9. Click **Submit**.

    ![AWS Account](/images/8/0009.png?featherlight=false&width=90pc)

10. Congratulations! You have successfully configured AWS SSO access.

    ![AWS Account](/images/8/00010.png?featherlight=false&width=90pc)
