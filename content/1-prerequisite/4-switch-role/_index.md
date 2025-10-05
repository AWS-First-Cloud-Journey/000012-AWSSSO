+++
title = "Create Permission Sets"
date = 2025
weight = 4
chapter = false
pre = "<b>1.4 </b>"
+++

#### Create Permission Sets

**ℹ️ Information:** Permission sets are a mechanism for defining centralized permissions within IAM Identity Center, allowing you to consistently apply access rights across all AWS accounts in your organization.  
Each permission set is deployed as an IAM role in every assigned AWS account.

---

### Steps

In this workshop, we will create two permission sets — **AdministratorAccess** and **readOnly** — to illustrate different access levels.

1. Navigate to the **IAM Identity Center Console**.  
2. Select the AWS Region recommended by the AWS Team if this is part of an AWS event.  
   If you are performing this on your own, choose a Region geographically close to you to optimize latency.  

3. Click **Permission sets** in the left menu under *Multi-account permissions* and then click **Create permission set**.  

![3.4.11](/images/0001/image14.png)

4. On the **Select permission set type** page:  
   - Under *Permission set type*, select **Predefined permission set**  
   - Under *Policy for predefined permission set*, choose the AWS managed policy **AdministratorAccess**, then click **Next**  

![3.4.11](/images/0001/image15.png)

5. On the **Specify permission set details** page:  
   - Enter **Permission set name:** `AdministratorAccess`  
   - Keep all default values  
   - Click **Next**  

![3.4.11](/images/0001/image16.png)

6. On the **Review and create** page:  
   - Review your selections  
   - Click **Create**  

![3.4.11](/images/0001/image17.png)

**ℹ️ Information:** After the permission set is created, you will see a confirmation page.  
IAM Identity Center automatically creates a corresponding IAM role in each AWS account when you assign this permission set to users or groups.

![3.4.11](/images/0001/image18.png)

---

#### Create a Permission Set for Read-Only Access

Similarly, let’s create another permission set for read-only access:

1. On the **Select permission set type** page:  
   - Under *Permission set type*, select **Predefined permission set**  

![3.4.11](/images/0001/image19.png)

   - Under *Policy for predefined permission set*, choose the AWS managed policy **ViewOnlyAccess**, then click **Next**  

2. On the **Specify permission set details** page:  
   - Under *Permission set name*, enter **readOnly**  
   - Keep all other fields (*Description*, *Session Duration*, *Relay state*, and *Tags*) as default  
   - Click **Next**  

![3.4.11](/images/0001/image20.png)

3. On the **Review and create** page:  
   - Review your selections  
   - Click **Create**  

![3.4.11](/images/0001/image21.png)

**ℹ️ Information:** After the permission set is created, you will see a confirmation page.  
IAM Identity Center automatically creates a corresponding IAM role in each AWS account when you assign this permission set to users or groups.

![3.4.11](/images/0001/image211.png)

---

**💡 Pro Tip:** In addition to predefined permission sets, you can create **custom permission sets** by combining multiple AWS managed policies or defining **customer-managed policies** using JSON.  
This allows you to implement fine-grained permissions following the **principle of least privilege**, tailored to your organization’s specific needs.

**🔒 Security Note:** Permission sets in IAM Identity Center support advanced security features such as **session duration limits**, **access requirements**, and **integration with AWS CloudTrail** for activity logging.  
In production environments, consider setting shorter session durations and enforcing **Multi-Factor Authentication (MFA)** for permission sets with elevated privileges.

**ℹ️ Information:** IAM Identity Center automatically manages the lifecycle of IAM roles created from permission sets, including updating roles when you modify the permission set configuration.  
This simplifies access management at scale and ensures consistency across your entire AWS Organization.

---

You have successfully created two new Permission Sets.  
Next, let’s proceed to granting access to users and groups.
