+++
title = "Provision Permission Sets"
date = 2025
weight = 5
chapter = false
pre = "<b>1.5 </b>"
+++

#### Provision Permission Sets

**ℹ️ Information:** By default, when you create a permission set, it is not yet provisioned (not applied to any AWS account).  
To activate a permission set within an AWS account, you need to grant IAM Identity Center access to users or groups in that account and then assign the permission set to those users or groups.

---

### Steps

1. Navigate to the **IAM Identity Center Console**, select **AWS accounts**, and choose the account where you want users to have access.  
Click **Assign users or groups**.

![3.4.11](/images/0001/image22.png)

2. On the **Select users and groups** page:  
   - Choose the **Groups** tab  
   - Select the **Administrators** group  
   - Click **Next**  

![3.4.11](/images/0001/image23.png)

3. On the **Select permission sets** page:  
   - Under *Permission sets*, select **AdministratorAccess**  
   - Click **Next**  

![3.4.11](/images/0001/image24.png)

4. On the **Review and submit** page:  
   - Review the information you provided  
   - Click **Submit**  

![3.4.11](/images/0001/image25.png)

**ℹ️ Information:** You will see a confirmation page indicating that the AWS account assignment has been successfully created.

![3.4.11](/images/0001/image266.png)

**ℹ️ Information:** IAM Identity Center links the user group with the permission set and assigns it to the selected AWS account(s).  
You will see a page with a green banner confirming that the provisioning process completed successfully.

---

#### Provision Another Permission Set for the Same Account

1. In the **IAM Identity Center Console**, go to **AWS accounts** and select the same account used earlier.  
Click **Assign users or groups**.

![3.4.11](/images/0001/image266.png)

2. On the **Select users and groups** page:  
   - Choose the **Groups** tab  
   - Select the **readOnly** group  
   - Click **Next**  

![3.4.11](/images/0001/image27.png)

3. On the **Select permission sets** page:  
   - Under *Permission sets*, select **readOnly**  
   - Click **Next**  

![3.4.11](/images/0001/image28.png)

4. On the **Review and submit** page:  
   - Review your selections  
   - Click **Submit**  

![3.4.11](/images/0001/image29.png)

---

**💡 Pro Tip:** Check the IAM roles that appear under the AWS account where you provisioned the permission sets.  
This confirms that the permissions have been applied correctly and IAM Identity Center successfully created the corresponding IAM roles within that account.

![3.4.11](/images/0001/image30.png)

**🔒 Security Note:** Group-based permission assignments make access management more efficient and easier to maintain as your organization grows.  
This is the best practice for implementing **least privilege access** and following **Zero Trust** principles.  
When your organization’s structure changes, you only need to update group memberships rather than adjusting permissions for each individual user.

**ℹ️ Information:** Once a permission set is provisioned, IAM Identity Center automatically creates and manages the corresponding IAM roles in each assigned AWS account.  
This greatly simplifies large-scale access management and ensures consistency across your entire AWS Organization.

---

You have successfully provisioned Permission Sets for your AWS account.  
Next, let’s move on to verifying the configuration.
