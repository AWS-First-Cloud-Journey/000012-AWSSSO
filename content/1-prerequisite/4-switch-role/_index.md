+++
title = "Access member account in Organization"
date = 2020
weight = 4
chapter = false
pre = "<b>1.4 </b>"
+++

#### Switching Roles for Accessing Member Accounts in AWS Organization

In this step, you will use the **Switch Role** function to access **member accounts** from your **management account**.

#### Content

- **Switch Role** to **Member Accounts** Created by AWS Organization (Step 1.1)
- **Switch Role** to **Member Accounts** Invited to Join AWS Organization (Step 1.3)

#### A) Switch Role to Member Accounts Created by AWS Organization

1. Log in to your **management account**:

   - Use an **IAM User** to log in.
   - Go to the **AWS Management Console** and search for the **AWS Organizations** service in the search bar.
   - Copy the Account ID (a 12-digit number located below the account name) of the account you wish to access.
   - In the top right corner, next to the account name, click the triangle and select **Switch role**.
   
   ![AWS Account](/images/11/0000.png?featherlight=false&width=90pc)
   
   - Note: If you are using a **root** account, you won't see the **Switch role** function.
   - If you're unfamiliar with creating an IAM User (with Admin permission) for this lab, review the article: [Manage Access with AWS Identity and Access Management (AWS IAM)](https://000002.awsstudygroup.com/1-introduction/).
   
2. **Switching Roles**:

   - Go to **Account** and paste the Account ID you copied in Step 1 (e.g., `999999999943`).
   - In the **Role** section, enter the role name you used when creating the account in Step 1.1 (e.g., `OrganizationAccountAccessRole`, recommended by AWS).
   - Optionally, give a **Display Name** for easy identification.
   - Choose a color for the role's item.
   - Select **Switch roles**.
   
   ![AWS Account](/images/11/0003.png?featherlight=false&width=90pc)
   
   - Result:
   
   ![AWS Account](/images/11/0004.png?featherlight=false&width=90pc)
   
   Congratulations on successfully switching roles!
   
   - Verify if you have permissions for universal services:
   
   ![AWS Account](/images/11/0004.png?featherlight=false&width=90pc)
   
#### Explanation:

- You can easily access the **member account** created through **AWS Organizations** and have full admin permissions because:

  - The IAM User used in Step 1 has admin permissions.
  - When creating a new account via **AWS Organizations**, AWS automatically adds the **AdministratorAccess** permission to the **OrganizationAccountAccessRole** role. Check:
  
- You are now in the **member account** with the Display Name: FCJ-Dev. In the search box, type and select the **IAM** service.
- On the right, select **Roles**.
  
  ![AWS Account](/images/11/0005.png?featherlight=false&width=90pc)
  
- Choose the Role name: **OrganizationAccountAccessRole**.
  
  ![AWS Account](/images/11/0006.png?featherlight=false&width=90pc)
  
- You should see the admin permission: **AdministratorAccess** with the explanation: **Provides full access to AWS services and resources**.
  
  ![AWS Account](/images/11/0007.png?featherlight=false&width=90pc)
  
#### Extension:

After following the tutorial: [Administrating Access with AWS Identity and Access Management (AWS IAM)](https://000002.awsstudygroup.com/en/1-introduction/) to create an IAM User for logging into the **management account**, and assigning admin permission (**AdministratorAccess**) to perform the switch role, there's no need to add **assume role** permissions ([explained here](https://000002.awsstudygroup.com/1-introduction/1.3-iam-role/)) since admin permission already encompasses this capability.

However, for the principle of **least privilege**, consider granting **assume role** permission only to users who need to switch between accounts. For instance, in an AWS Organization with accounts for Dev, Test, and Production environments, provide the Dev Lead IAM User access to the **management account** with only **assume role** permissions for Dev and Test environments. This ensures convenience while maintaining security.

#### Practice:

3. Creating **User Groups**:

- Within the **management account**, follow [item 2.1 in the article Managing Access Rights with IAM](https://000002.awsstudygroup.com/2-create-admin-user-and-group/2.1-create-admin-group/).
- In Step 4, enter a **User Group Name** (e.g., DevGroup).
- Select **Create policy**, a new window will appear.
  
  ![AWS Account](/images/11/0008.png?featherlight=false&width=90pc)
  
4. Creating a **Customer Managed Policy**:

- Choose a service: type **STS**, then select **STS** from the options.
- Actions -> Select actions -> type `AssumeRole` -> in the middle, select **AssumeRole**.
- Resources -> Specific -> Add ARN
  - Account \*: enter the member Account ID (the ID copied in Step 1 above, e.g., `999999999943`).
  - Role name with path \*: enter the role name from Step 1.1 (e.g., `OrganizationAccountAccessRole`).
  - Select **Add**.
- Select **Next: Tags**.
  
  ![AWS Account](/images/11/0009.png?featherlight=false&width=90pc)
  
- Select **Next: Review**.
- Name \*: enter a policy name (e.g., `switch_role_999999999943`).
- Select **Create policy**.
  
  ![AWS Account](/images/11/00010.png?featherlight=false&width=90pc)
  
5. Attaching the Policy to **User Groups**:

- Go back to the **Create user group** page.
- In the **Attach permissions policies - Optional** section, click the refresh icon.
  
  ![AWS Account](/images/11/00011.png?featherlight=false&width=90pc)
  
- In the search box, enter: **switch_role_999999999943**.
- Check the box.
- Select **Create Group**.
  
  ![AWS Account](/images/11/00012.png?featherlight=false&width=90pc)
  
6. Creating a **User**:

- Follow [item 2.2 in the article Managing Access Rights with IAM](https://000002.awsstudygroup.com/2-create-admin-user-and-group/2.2-create-admin-user/).
- In Step 2, enter the **User name** as **DevLead**.
- In Step 3, select the **DevGroup**.
- Complete the remaining steps and confirm the creation of the new IAM User.
  
  ![AWS Account](/images/11/00013.png?featherlight=false&width=90pc)
  
   Now, the IAM User **DevLead** has been created and assigned the policy **switch_role_999999999943** via the group **DevGroup**.
   
   **Note**: While the Users and User Groups interface allows you to assign permissions directly, it's best practice to assign permissions to User Groups first, and then add Users to Groups. This centralized approach simplifies permission management.
   
7. Logging in with the newly created **IAM User**:

   ![AWS Account](/images/11/00014.png?featherlight=false&width=90pc)
   
   Result:
   
   ![AWS Account](/images/11/00015.png?featherlight=false&width=90pc)
   
8. Performing **Switch Role** via **Member Account**:

   Note: You've logged into the **IAM User** but are still in the **management account**. Now, you'll initiate the **Switch Role** to access the **member account**.
   
   - Repeat the steps from Step 2.
   
   ![AWS Account](/images/11/00016.png?featherlight=false&width=90pc)
   
   Congratulations on successfully switching roles via the **member account** (ID: 999999999943) with the IAM User DevLead.
   
   ![AWS Account](/images/11/00017.png?featherlight=false&width=90pc)
   
   You can use the **Create an AWS account** function to create an account for the test environment and follow Steps 3 to 8 to perform the switch role for the Test environment with the corresponding Account ID.

#### B) Switch Role to Member Accounts Invited to Join AWS Organization

When reviewing the following items:

- 1.1 Create an AWS Account in AWS Organizations
- 1.3 Invite AWS Account to AWS Organization

You'll notice the ability to create an AWS Account in AWS Organizations (**Create an AWS account**) includes a section to create an IAM role for the management account to access member account resources via **Switch Role**.

However, this functionality is missing in the process of inviting an AWS Account to an AWS Organization (**Invite an existing AWS account**). Therefore, you need to manually add an IAM Role for the invited AWS Account.

![AWS Account](/images/12/0001.png?featherlight=false&width=90pc)

1. Creating a Role with Admin Rights:

- Use a **member account** that has been added to the **AWS Organization** in [1.3].
- Go to the **AWS Management Console**, search for the **IAM** service, select **Roles**, and click **Create role**.

  ![AWS Account](/images/12/0003.png?featherlight=false&width=90pc)
  
- Select **AWS account**, then **Another AWS account**.
- Enter the Account ID of the **management account** in the provided field (e.g., `999999999963`).
- Click Next.

  ![AWS Account](/images/12/0004.png?featherlight=false&width=90pc)
  
- In the **Permissions policies** section, enter `AdministratorAccess` and check the corresponding box.
- Click Next.

  ![AWS Account](/images/12/0005.png?featherlight=false&width=90pc)
  
- Provide a Role name (e.g., `OrganizationAccountAccessRole`).
- Scroll down and click **Create role**.

  ![AWS Account](/images/12/0006.png?featherlight=false&width=90pc)
  
- Copy the Account ID of the **member account** (e.g., `888800009920`) by clicking the square.

  ![AWS Account](/images/12/0007.png?featherlight=false&width=90pc)
  
2. Initiating Switch Role:

- Log in to your **management account** (similar to Steps 1 and 2 in Part A).
- Click the triangular bookmark in the top right corner, next to the account name, and select **Switch role**.

  ![AWS Account](/images/12/0008.png?featherlight=false&width=90pc)
  
- In the **Account** field, paste the copied Account ID from Step 1 (e.g., `888800009920`).
- In the **Role** field, enter the role name created in Step 1 (e.g., `OrganizationAccountAccessRole`).
- Optionally, provide a **Display Name** for easy identification.
- Choose a color for the role's item.
- Select **Switch Role**.

  ![AWS Account](/images/12/0009.png?featherlight=false&width=90pc)
  
- Congratulations! You have successfully switched roles and accessed the **member account** that was invited to join **AWS Organizations**.

  ![AWS Account](/images/12/00010.png?featherlight=false&width=90pc)

**Conclusion**: From Step 1.1 to Step 1.4, it's clear that the **management account** serves as the admin account in the AWS Organization service, while **member accounts** are permanent member accounts. To add **member accounts** to the Organization, there are two approaches:

1. Create a new account using the **Create an AWS account** function.
2. Invite an existing account using the **Invite an existing AWS account** function.

Additionally, you can switch roles to access **member accounts** using the **Switch Role** function. Depending on the approach chosen, the conditions for successful role switching differ:

1. With the **Create an AWS account** method, switching roles is relatively simple since **AdministratorAccess** permission is automatically granted to the **OrganizationAccountAccessRole** during account creation via **AWS Organizations**. Furthermore, **assume role** permissions corresponding to the member account ID need to be granted to the IAM User in the management account.

2. With the **Invite an existing AWS account** method, switching roles requires more steps. You need to manually create the **OrganizationAccountAccessRole** and assign **AdministratorAccess** permissions to the management account's account ID. Additionally, **assume role** permissions corresponding to the member account ID should be granted to the IAM User in the management account.

Remember that switching roles isn't the only method for accessing member accounts. In the steps outlined in item 2, you'll explore another approach using AWS SSO (Single Sign-On).
