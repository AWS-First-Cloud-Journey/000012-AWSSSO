+++
title = "Setting up the Organization Unit"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++

In this step, you will practice setting up the Organization Units (**Security**, **Shared Services**, **Logging** and **Application**) corresponding to the AWS accounts created in this section. before. The OUs will be located inside the Root - where all the OUs and AWS accounts are located.

**Content**
- [Create Organization Unit](#create-organization-unit)
- [Move AWS accounts to respective Organization Unit](#move-aws-accounts-to-respective-organization-unit)

#### Create Organization Unit

1. Go to **AWS Management Comsole** and find the **AWS Organizations** service in the search bar.

2. Tick **Root**, select **Actions**, and select **Create new** under **Organizational Unit**

![AWS Account](/images/4/0003.png?featherlight=false&width=90pc)

3. At the **Create organizational unit in Root** page:
    - Under **Details**, enter the name of the OU (Example: Logging Unit)

![AWS Account](/images/4/0004.png?featherlight=false&width=90pc)

4. Check the information and select **Create organizational unit**

![AWS Account](/images/4/0005.png?featherlight=false&width=90pc)

5. Repeat with the remaining Organization Units.

![AWS Account](/images/4/0006.png?featherlight=false&width=90pc)

#### Move AWS accounts to respective Organization Unit

1. Go to **AWS Management Comsole** and find the **AWS Organizations** service in the search bar.

2. Tick the AWS account you want to move (Example: **Logging**), select **Actions**, and select **Move** under **AWS Account**


![AWS Account](/images/4/0007.png?featherlight=false&width=90pc)

3. Tick the appropriate OU (Example: **Logging Unit**) and select **Move AWS account**


![AWS Account](/images/4/0008.png?featherlight=false&width=90pc)

4. Repeat for the remaining AWS and Organization Unit accounts:
    - Security Account with Security Unit
    - Shared Services with Shared Services Unit
    - Application Account with Application Unit