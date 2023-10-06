+++
title = "Setting up the Organization Unit"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++

#### Setting Up Organization Units

In this step, you will practice setting up the Organization Units for the AWS accounts created in the previous section. The Organization Units include **Security**, **Shared Services**, **Logging**, and **Application**. These units will be situated within the Root, where all the OUs and AWS accounts are located.

#### Contents
- [Setting Up Organization Units](#setting-up-organization-units)
- [Contents](#contents)
- [Create Organization Unit](#create-organization-unit)
- [Move AWS Accounts to Respective Organization Unit](#move-aws-accounts-to-respective-organization-unit)

#### Create Organization Unit

1. Open the **AWS Management Console** and search for the **AWS Organizations** service.

2. Select the **Root**, click on **Actions**, and then choose **Create new** under the **Organizational Unit** section.

   ![Create Organization Unit](/images/4/0003.png?featherlight=false&width=90pc)

3. On the **Create organizational unit in Root** page:
   - In the **Details** section, provide a name for the OU (For example: Logging Unit).

   ![Create OU Details](/images/4/0004.png?featherlight=false&width=90pc)

4. Review the information and click **Create organizational unit**.

   ![Create OU](/images/4/0005.png?featherlight=false&width=90pc)

5. Repeat the above steps for the remaining Organization Units.

   ![Create OU](/images/4/0006.png?featherlight=false&width=90pc)

#### Move AWS Accounts to Respective Organization Unit

1. Go to the **AWS Management Console** and find the **AWS Organizations** service using the search bar.

2. Check the AWS account you wish to move (For instance: **Logging**), click on **Actions**, and then select **Move** under **AWS Account**.

   ![Move AWS Account](/images/4/0007.png?featherlight=false&width=90pc)

3. Tick the appropriate OU (Example: **Logging Unit**) and click **Move AWS account**.

   ![Move to OU](/images/4/0008.png?featherlight=false&width=90pc)

4. Repeat the above steps for the remaining AWS and Organization Unit accounts:
   - Move the Security Account to the Security Unit
   - Move the Shared Services Account to the Shared Services Unit
   - Move the Application Account to the Application Unit
