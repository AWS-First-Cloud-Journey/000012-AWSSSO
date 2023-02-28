+++
title = "Access member account in Organization"
date = 2020
weight = 4
chapter = false
pre = "<b>1.4 </b>"
+++

In this step, you will stand at **management account** to access **member accounts** through **switch role** function

**Content**

- **switch role** to **member accounts** created by **AWS Organization** (step 1.1)

- **switch role** to **member accounts** invited to join **AWS Organization** (step 1.3)

#### A) **Switch role** to **member accounts** created by **AWS Organization**

1. Login to **management account**

- Use **IAM User** to login

- Go to **AWS Management Comsole** and look for **AWS Organizations** service in the search bar.

- Copy the Account ID (Has 12 numbers & appears below the name of the Account) that you want to access

- At the right corner, after the name of the Account, select the triangle, Select **Switch role**

![AWS Account](/images/11/0000'.png?featherlight=false&width=90pc)

- **Note**, if you are using **root** account, you will not be able to see **Switch role** function

- If you are not familiar with creating IAM User (with Admin permission) to serve this lab, please review the article: [Manage Access with AWS Identity and Access Management (AWS IAM)](https://000002.awsstudygroup.com/1-introduction/)

2. **Switching Roles**

- Go to **Account**, paste the account ID you copied in step 1, for example: `999999999943`
- In the **Role** section, enter the **role name** you used when creating the Account (in step 1.1), eg: `OrganizationAccountAccessRole` (this is the role name recommended by AWS)
- In the **Display Name** section, although this is not mandatory information, it is recommended that you name it for easy identification & avoid confusing access to the environment! In practice there will be many converted accounts. Ex: `FCJ-DEV`
- Print item color: choose the color you like
- Select **Switch roles**

**note**: if you need to change **Display Name**, just go back to step 2 and add the name you want

![AWS Account](/images/11/0003.png?featherlight=false&width=90pc)

- Result:

![AWS Account](/images/11/0004.png?featherlight=false&width=90pc)

Congratulations on your successful Switch Role!

- Check if you have permissions on universal services

![AWS Account](/images/11/0004'.png?featherlight=false&width=90pc)

#### Explanation:

- You can **access** easily into the account (member account) created from **AWS Organizations** & have full admin permission,because:

  - The IAM User you used in step 1 has admin permission.
  - While creating a new account with **AWS Organizations**, with your consent - AWS automatically added **AdministratorAccess** permission to the **OrganizationAccountAccessRole** role. Check:

- You are standing at **member accouunt with Display name: FCJ-Dev**, in the search box, type and select **IAM** service
- On the right, select **Roles**

![AWS Account](/images/11/0005.png?featherlight=false&width=90pc)

- Select Role name: **OrganizationAccountAccessRole**

![AWS Account](/images/11/0006.png?featherlight=false&width=90pc)

- You should see admin permission: **AdministratorAccess** with explanation **Provides full access to AWS services and resources**

![AWS Account](/images/11/0007.png?featherlight=false&width=90pc)

#### Extend:

Once you have followed the tutorial: [Administrating Access with AWS Identity and Access Management (AWS IAM)](https://000002.awsstudygroup.com/en/1-introduction/) to create an IAM User to log in \* \*management account** then you give admin permission: **AdministratorAccess** to perform the switch role, so you don't need to add **assume role** permissions ([**explained link\*\*]](https://000002.awsstudygroup.com/1-introduction/1.3-iam-role/)) because admin permission already include this permission.

But in practice to ensure the **least privilege** for the granting of minimal permission, as an administrator, you should only grant **assume role** permission to the user who is switched via the account - representing environment that the team needs.

**Example**: Your **AWS Organizations** has 4 accounts running workload respectively for 3 environments: Dev, Test, Produciton and the 4th acc is **management account** (recommended by AWS: it should not run any Workload, just for consolidated billing)! By the nature of work, Dev Lead needs to move back and forth between Dev and Test environments without logging in with User Name, Password to 2 AWS accounts!

At this point, switching the role to move between the two environments will be very quick and convenient. So as an administrator - you will give DevLead an IAM User access to **management account** who only has **assume role** permission of Dev and Test environments to perform the switch but no any other rights on the Production environment.

#### Practice:

3. Create **User Groups**

- Stand at **management account** and do again [item 2.1 in the article Managing access rights with IAM](https://000002.awsstudygroup.com/2-create-admin-user-and-group/2.1-create-admin-group/)
- In step 4, **User Group Name** enter the Group name (Example: DevGroup)
- Select **Create policy**, a new window appears

![AWS Account](/images/11/0008.png?featherlight=false&width=90pc)

4. Create **Customer managed Policy**

- Choose a service: type **STS** -> on the left, select **STS**
  - **STS** is Security Token Service: is a web service that allows users to send temporary requests and grants limited permissions to IAM users. Token has a default validity of 1 hour
- Actions -> Select actions -> type `AssumeRole` -> in the middle, select **AssumeRole**
- Resources -> Specific -> Add ARN
  - Account \*: enter the member Account ID ( the ID you copied in step 1 above) (eg: `999999999943`)
  - Role name with path \*: enter the role name in step 1.1 (eg: `OrganizationAccountAccessRole`)
  - Select **Add**
- Select **Next: Tags**

![AWS Account](/images/11/0009.png?featherlight=false&width=90pc)

- Select **Next: Review**
- Name \* : điền policy name (vd:`switch_role_999999999943`)
- Select **Create policy**

![AWS Account](/images/11/00010.png?featherlight=false&width=90pc)

5. Attach the newly created policy to **User Groups**

- Back to **Create user group** page
- In the **Attach permissions policies - Optional** section, select the refesh icon

![AWS Account](/images/11/00011.png?featherlight=false&width=90pc)

- In the search box, enter: **switch_role_999999999943**
- Check the box
- Select **Create Group**

![AWS Account](/images/11/00012.png?featherlight=false&width=90pc)

6. Create **User**

- Do again [item 2.2 in the article Managing access rights with IAM](https://000002.awsstudygroup.com/2-create-admin-user-and-group/2.2-create-admin-user/)
- In step 2, **User name** enter: **DevLead**,
- In step 3, select **DevGroup**
- Complete the rest of the steps and check the newly created IAM User

![AWS Account](/images/11/00013.png?featherlight=false&width=90pc)

-> So IAM User: DevLead has been created & has policy name: **switch_role_999999999943** attached via group: DevGroup

**Note**: You see that in the Users or User Groups interface, there is a function that allows you to assign permissions (**Add permissions**), but according to the best pratice:

- You should only assign permissions to User Groups
- After that, add the User in the Group, then the User will automatically have all the permissions that you have given to Groups

-> This makes it easy to manage permissions at a centralized level in groups, avoiding granting permissions by user and difficult in management because you have to go to each user to watch which permission policy we have ever given.

7. Login to the newly created **IAM User**

![AWS Account](/images/11/00014.png?featherlight=false&width=90pc)

Result:

![AWS Account](/images/11/00015.png?featherlight=false&width=90pc)

8. Perform **switch role** via **member account**

**note**: you have just logged in to IAM User but still belong to **management account**, now you start performing **switch role** via **member account**.

- Repeat step 2 above

![AWS Account](/images/11/00016.png?featherlight=false&width=90pc)

Congratulations on **switching role** via **member account** (ID: 999999999943) with IAM User DevLead

![AWS Account](/images/11/00017.png?featherlight=false&width=90pc)

You can use the **Create an AWS account** function to create an acc for the test environment and do steps 3 to 8 to switch the role through the Test environment with the corresponding Account ID

#### B) **Switch role** to **member accounts** invited to join **AWS Organization**

When reviewing items:

- 1.1 Create an AWS Account in AWS Organizations
- 1.3 Invite AWS Account to AWS Organization

-> You will see the ability to create AWS Account in AWS Organizations (**Create an AWS account**) there is a section to create an IAM role for management account to use to access resources to the member account by **Switch role**

-> But the above is completely absent in the function of invite an AWS Account to an AWS Organization (**Invite an existing AWS account**), so you need to add an IAM Role for the invited AWS Account.

![AWS Account](/images/12/0001.png?featherlight=false&width=90pc)

1. Create Role with admin rights

- Use **member account** that you have joined **AWS Organizations** in [1.3]

- Go to **AWS Management Comsole** and find **IAM** service in the search bar, select **Roles**, select **Create role**

![AWS Account](/images/12/0003.png?featherlight=false&width=90pc)

- Select **AWS account**
- Select **Another AWS account**
- Enter the Account ID of **management account** in the box, eg: **999999999963**
- Select Next

![AWS Account](/images/12/0004.png?featherlight=false&width=90pc)

- In the **Permissions policies** section, enter: `AdministratorAccess`, press enter
- Check the box AdministratorAccess
- select Next

![AWS Account](/images/12/0005.png?featherlight=false&width=90pc)

- Role name: enter `OrganizationAccountAccessRole`
- Scroll to the bottom of the page, select **Create role**

![AWS Account](/images/12/0006.png?featherlight=false&width=90pc)

- Check the newly created role, copy the Account ID **member account** (ID: 888800009920) by clicking the square

![AWS Account](/images/12/0007.png?featherlight=false&width=90pc)

2. Implement switch role

- Log in to **management account** (like step 1 and 2 in part A)

- lick triangular bookmark on the corner right side - next to acc name, select **Switch role**

![AWS Account](/images/12/0008.png?featherlight=false&width=90pc)

- In the **Account** section, paste the Account ID you copied in step 1, for example: `888800009920`
- In the **Role** field, enter the **role name** you used while creating the Account (create step 1), eg: `OrganizationAccountAccessRole`
- In the **Display Name** section, although this is not mandatory information, it is recommended that you name it for easy identification & avoid accessing the wrong environment! In fact, there will be many Accounts to be switched. Ex: `FCJ_Invite_Acc`
- In the color section: choose the color you like
- Select **Switch Role**

![AWS Account](/images/12/0009.png?featherlight=false&width=90pc)

- Congratulations, by Switching Role - you have successfully migrated to **member account** already invited to **AWS Organizations**

![AWS Account](/images/12/00010.png?featherlight=false&width=90pc)

**Conclusion**: From step 1.1 to step 1.4, we have seen that the management account will be the admin account in the AWS Organization service and the member accounts will be the permanent member accounts.
In addition, for the member account to appear in the Organization, we have two ways:
1. Create a new acc using the function: Create an AWS account
2. Add an existing account using the function: Invite an existing AWS account

Besides, we can stand from the management account to access the member account via the switch role function and for each of the two ways above, we need different conditions for the switch role to succeed:

1. With the **Create an AWS account** method, switching the role will be quite simple because during the create of the member account we have allowed AWS to automatically add the role name **OrganizationAccountAccessRole** with **AdministratorAccess** permission. In addition, we need to grant **assume role** permission corresponding to member account ID for IAM User under management account

2. With the **Invite an existing AWS account** method, switching roles will be more difficult! We need to create the role name **OrganizationAccountAccessRole** and assign the **AdministratorAccess** permission to the account ID of the management account
In addition, we need to grant **assume role** permission corresponding to member account ID for IAM User under management account

However, the switch role is not the only way to access member accounts. In the steps in item 2, you'll discover another way of accessing it through setting up AWS SSO.