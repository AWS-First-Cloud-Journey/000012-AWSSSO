+++
title = "Clean up resources"
date = 2021-06-14T22:33:19+07:00
weight = 5
chapter = false
pre = "<b>4. </b>"
+++

#### Clean up resources

1. Access the **AWS SSO Management Console**.

2. **Delete Groups**:
   - Navigate to **Groups**.
   - Select the groups associated with this lab.
   - Click on **Delete groups**.
   - In the **Delete groups** prompt, enter "DELETE" in the provided box.
   - Confirm the deletion by clicking **Delete groups**.

3. **Delete Users**:
   - Go to **Users**.
   - Check the users related to this lab.
   - Click on **Delete users**.
   - In the **Delete users** prompt, enter "DELETE" in the provided box.
   - Confirm the deletion by clicking **Delete users**.

4. **Remove Access** for AWS Accounts:
   - Select **AWS Accounts**.
   - Click on the name of an AWS account.
   - Revoke all account access rights.
   - Repeat this step for accounts with assigned access rights that need to be deleted.
   ![RemoveAccess](../../../images/3/3_RemoveAccess.png?width=90pc)

5. **Delete Permission Sets**:
   - Navigate to **AWS accounts**.
   - Go to the **Permission sets** tab.
   - Select the relevant permission sets.
   - Press **Delete**.
   - In the prompt, enter the name of the permission set in the box and click **Delete**.

::: tip
Note: Ensure you back up data from these accounts if you anticipate needing them in the future. Deleting an account results in permanent deletion of all associated resources and data.
:::

6. **Delete AWS Accounts** (optional for future labs):
   - To delete an AWS account, log in as the root user.
     - Visit the AWS console login page at [https://console.aws.amazon.com/](https://console.aws.amazon.com/).
     - On the **Sign in** page, choose **Root user** and enter the email of the account you want to delete (e.g., example+lab12Logging@amazon.com.vn).
     - Complete the Security Check and select **Forgot Password?**
     ![ForgotPassword](../../../images/3/3_ForgotPassword.png?width=90pc)
     - AWS will send a forgot password confirmation email to the registered email address (e.g., example@amazon.com.vn). Follow the email instructions to change your password and sign in to your AWS account.
   - After logging in as the root user, click on the account name in the upper right corner.
     - Select **My Account**.
     - Scroll down to find the **Close Account** section.
     - Check all the boxes and select **Close Account**.

::: tip
When creating a new AWS account in the AWS Organization, the root user's password is automatically generated and inaccessible. You can access the root user by recovering the forgotten password (*forgot password*).
:::
