+++
title = "Customer Managed Policies"
date = 2020
weight = 4
chapter = false
pre = "<b> 4. </b>"
+++

When using IAM Identity Center, there are scenarios where you might want to reuse existing IAM permission policies in your permission sets, such as:

- When you need the same role across all AWS accounts but require a way to adjust policies in each account to reference their specific resources
- When you use Identity Center as an alternative to per-account federation, but need to reuse customer managed policies you've already created

Customer Managed Policies (CMP) support with permission sets addresses these requirements. In this guide, you'll walk through a scenario where CMPs can be used to address specific requirements.

**ℹ️ Information**: Customer Managed Policies allow you to maintain consistent roles across accounts while still having the flexibility to reference account-specific resources in your policies.

**⚠️ Warning**: Before assigning permission sets with IAM policies, you must prepare your member account. The name of the IAM policy in the member account must match case-sensitively with the name of the policy in the management account. IAM Identity Center cannot assign the permission set if the policy doesn't exist in the member account. The permissions granted by the policy don't necessarily need to match exactly between accounts.

#### Scenario

Consider a scenario where an operator group needs access to different member accounts, and their access to those accounts should be limited to specific AWS CloudWatch log groups within those accounts. This requirement can be addressed with Customer Managed Policies (CMPs) where an `operatorAccess` policy can be created in each AWS account, with the actual policies and permissions/authorizations only allowing CloudWatch operations to be performed on the specified account's log groups. You can then create permission sets attached to the `operatorAccess` CMP that permit CloudWatch operations on the specified accounts' log groups.

#### Creating a Customer Managed IAM Policy

1. Navigate to the IAM console to create an IAM policy
![3.4.11](/images/0004/1.png)
2. Select the JSON tab and copy and paste the following policy into the text area
![3.4.11](/images/0004/2.png)
3. Replace `<account-id>` with the account ID for the account this policy is being created in

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "logs:CreateLogStream",
                "logs:DescribeLogStreams",
                "logs:PutLogEvents",
                "logs:GetLogEvents"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:logs:us-east-1:<account-id>:log-group:OperationsLogGroup:*"
        },
        {
            "Action": [
                "logs:DescribeLogGroups"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:logs:us-east-1:<account-id>:log-group::log-stream:*"
        }
    ]
}
```
4. Click **Next: Tags** (Tags are optional)  
5. Click **Next: Review**

6. On the **Create Policy** page, provide the following:
   - **Policy Name**: `operatorAccess`
   - **Description** – optional: `Policy that grants operator access to CloudWatch log groups`
   - Click **Create Policy**
![3.4.11](/images/0004/3.png)

7. A confirmation message appears: **“operatorAccess” has been successfully created.**
![3.4.11](/images/0004/4.png)


**🔒 Security Note**: When creating policies, always follow the principle of least privilege by granting only the permissions necessary to perform the required tasks.

#### Creating a Permission Set with Customer Managed Policy

1. Navigate to the IAM Identity Center Console
2. Select the AWS Region recommended by the AWS Team if this is part of an AWS Event, or the Region you intend to configure the rules if you're running this on your own
3. Click on **Permission sets** in the left-hand menu and then click the **Create permission set** button  
![3.4.11](/images/0004/5.png)

4. On the **Select permission set type** page:
   - Select the radio button **Custom permission set**
   - Click **Next**
![3.4.11](/images/0004/6.png)

5. On the **Specify policies** page:
   - Expand the **Customer managed policies** section
   - Click **Attach policies**
   - In the textbox labeled **Enter Policy name(s)**, enter `operatorAccess`  
     > This name must exactly match the name of the policy you created earlier in the **Create Customer Managed IAM policy** step.
   - Click **Next**
![3.4.11](/images/0004/7.png)

6. On the **Specify permission set details** page:
   - Provide a name for the permission set, e.g., `operatorAccessPermissionSet`
   - Leave the remaining fields [Description, Session Duration, Relay state, and Tags] as default
   - Click **Next**
![3.4.11](/images/0004/8.png)

7. On the **Review and create** page:
   - Review the details provided in the previous steps
   - Click the **Create** button
![3.4.11](/images/0004/9.png)

8. A confirmation message appears stating that the permission set named **operatorAccessPermissionSet** has been successfully created in AWS IAM Identity Center.  
![3.4.11](/images/0004/10.png)


**💡 Pro Tip**: Create a standard naming convention for your permission sets that indicates their purpose and level of access. This makes it easier to manage permissions at scale.

#### Creating a Group

Create a new group named **operations**:

1. Navigate to the **IAM Identity Center Console**  
2. Select **Groups** under **Workforce pool** and click **Create Group**  
![3.4.11](/images/0004/11.png)

3. On the **Create group** page:
   - Provide **Group Name**: `operations`
   - Provide **Description**, for example: `Group for cloud operations`
   - Click **Create group**
![3.4.11](/images/0004/12.png)

4. A group named `operations` has been successfully created in AWS IAM Identity Center.  
![3.4.11](/images/0004/13.png)

#### Create user and add to group

For this module, we will create a new user: `operationsUser`

1. Navigate to the **IAM Identity Center Console**  
2. Select **Users** under **Workforce pool** and click **Create User**  
![3.4.11](/images/0004/14.png)

3. On the **Create User** page:
   - Provide **Username**, e.g., `operationsUser`
   - For **Password**, choose the radio button **Generate a one-time password that you can share with the user**
   - Provide **Email Address** in the format: `email+operations@domain.com`, e.g., `example+operations@amazon.com`
   - Confirm the email address
   - Provide **First name**: `operations`
   - Provide **Last name**: `user`
   - Keep the **Display name** as entered
   - Click **Next**
![3.4.11](/images/0004/15.png)

4. On the **Add users to groups – optional** page:
   - Select the **operations** group
   - Click **Next**
![3.4.11](/images/0004/16.png)

5. On the **Review and add user** page:
   - Review the information provided in previous steps
   - Click **Add user**
![3.4.11](/images/0004/17.png)

6. A pop-up window will appear with the **One-time password**. Use the **Copy** button to save this information for authentication later.  
   Take note of the **User portal URL**, **Username**, and **Password**
![3.4.11](/images/0004/18.png)

7. A green banner confirms that the user `operationsUser` has been successfully created in IAM Identity Center.  
![3.4.11](/images/0004/19.png)

#### Assign Permission Set to AWS Account

1. Navigate to the **IAM Identity Center Console**, and select **AWS accounts**  
2. Choose the account to which you want the user to have access  
3. Click **Assign users or groups**  
![3.4.11](/images/0004/20.png)

4. On the **Assign users and groups to AccountName** page:
   - Select the **operations** group
   - Click **Next**
![3.4.11](/images/0004/21.png)

5. On the **Select permission sets** page:
   - Under **Permission sets**, select `operatorAccessPermissionSet`
   - Click **Next**
![3.4.11](/images/0004/22.png)

6. On the **Review and submit** page:
   - Review the information
   - Click **Submit**
![3.4.11](/images/0004/23.png)

7. IAM Identity Center will link the **User group** with the **Permission set** and assign it to the selected AWS account. You will see a page with a green confirmation banner.  
![3.4.11](/images/0004/24.png)

**💡 Pro Tip**: IAM Identity Center allows you to assign multiple permission sets to the same user or group, giving you flexibility in how you structure your access control.

#### Verifying Access

> **Note**:
> For a better experience, you should perform the following verification steps in private browsing mode or a different web browser

1. Log in to the AWS Portal using the User portal URL saved when creating operationsUser
2. Provide the username for the user previously created in this module

3. Provide the one-time password for the username
4. Set a new password for the user

5. After successful login, on the Identity Center portal page, select the Management console link for the operatorAccessPermissionSet role

6. After successfully logging into the Management Console, navigate to the CloudWatch Log groups page and confirm that you can list existing OperationsLogGroup log groups and successfully create new log streams in them

**🔒 Security Note**: Regularly review and audit your permission sets and group assignments to ensure users have the appropriate level of access to AWS resources.

This module demonstrates how AWS IAM Identity Center works with customer managed policies that you create in your AWS account. Although the module created a CMP and permission set and provided it in a single account, you can create CMPs with the same name in all member accounts and use the same operatorAccessPermissionSet permission set and provide it across all your member accounts.