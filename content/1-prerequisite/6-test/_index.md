+++
title = "Verify Access Permissions"
date = 2020
weight = 6
chapter = false
pre = "<b> 1.6 </b>"
+++

#### Verify Access Based on Users, Groups, and Permission Sets

**ℹ️ Information:** In this section, you will validate your IAM Identity Center configuration by confirming that users and groups have the correct permissions applied across AWS accounts.  
This is done by deploying an AWS CloudFormation stack that creates AWS resources for testing.  
The CloudFormation template provisions resources such as two VPCs (public and private subnets), EC2 instances, and several VPC Security Groups.

---

### Deploy the CloudFormation Template

1. Download the [Template](https://static.us-east-1.prod.workshops.aws/public/3fac600e-c0e3-4410-9a4f-8ca05b549ec7/static/iam-identitycenter-validation.yml)  
2. Navigate to the [CloudFormation console](https://console.aws.amazon.com/cloudformation/)  
3. Click **Create stack** and choose **With new resources (standard)**  

![3.4.11](/images/0001/image31.png)

4. On the **Create stack** page:  
   - Select **Template is ready** under *Prepare template*  
   - Choose **Upload a template file** under *Template source*  
   - Click **Choose file** and select the template you downloaded in Step 1  

![3.4.11](/images/0001/image32.png)

5. On the **Specify stack details** page:  
   - Enter a stack name, for example: `iam-identitycenter-validation-setup`  
   - Leave the **LatestAmiId** parameter as default and click **Next**  

![3.4.11](/images/0001/image33.png)

6. Leave all default settings on the **Configure stack options** page. Scroll down and click **Next**  

![3.4.11](/images/0001/image34.png)

7. On the **Review** page, scroll down and click **Submit**  

![3.4.11](/images/0001/image35.png)

**ℹ️ Information:** The CloudFormation stack deployment will take approximately 5 minutes to complete.  
You can confirm completion when the status changes to **CREATE_COMPLETE**.  

![3.4.11](/images/0001/image36.png)

---

### Validate Access

**⚠️ Warning:** For best results, perform the following validation steps in a private/incognito browser window or a separate browser to avoid session conflicts.



#### Verify Administrator Access

1. Sign in to the **AWS Access Portal** using the portal URL saved when you created `adminUser`.  
2. Enter the username of the user you created earlier in this module.  
3. Provide the one-time password for the user.  
4. Set a new password for the user.  

5. After signing in successfully, on the AWS Access Portal page, select the **Management console** link under the **AdministratorAccess** role.  
6. Once logged in to the Management Console, navigate to the **EC2 console**.  
7. Select a running instance.  
8. From the **Instance state** dropdown menu, choose **Stop instance**.  

**ℹ️ Information:** You should see a page with a green banner confirming that the instance has been stopped successfully.  
This demonstrates that the Administrator user can perform actions that modify resource states.  

9. Sign out of both the AWS Management Console and the AWS Access Portal.



#### Verify ReadOnly Access

1. Sign in to the **AWS Access Portal** using the `readOnlyUser`.  
2. Provide the one-time password for the username.  
3. Set a new password for the user.  

4. After logging in successfully, on the AWS Access Portal page, select the **Management console** link under the **readOnly** role.  
5. Once inside the Management Console, navigate to the **EC2 console**.  
6. Select a running instance.  
7. From the **Instance state** dropdown menu, choose **Stop instance**.  

**🔒 Security Note:** You will see a page with a red banner displaying **“Failed to stop the instance.”**  
This confirms that the read-only user cannot perform state-changing actions, validating that the **principle of least privilege** is functioning correctly.

**💡 Pro Tip:** Testing access in this way helps verify that your IAM Identity Center configuration works as intended and that permission sets are correctly applied to different user groups.  
In production environments, it’s a good practice to perform such validation regularly as part of your **security audit process** to ensure access permissions remain correctly enforced.
