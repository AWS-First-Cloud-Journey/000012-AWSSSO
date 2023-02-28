+++
title = "Clean up resources"
date = 2021-06-14T22:33:19+07:00
weight = 5
chapter = false
pre = "<b>4. </b>"
+++

#### Clean up resources

1. Access to **AWS SSO Mangement Console**
2. **Delete Groups**:
    - Select **Groups**, tick the groups related to this lab, and select **Delete groups**.
    - At the prompt **Delete groups**, type DELETE in the box, and select **Delete groups**
3. **Delete Users**:
    - Select **Users**, tick the users related to this lab, and select **Delete users**.
    - At the **Delete users** prompt, type DELETE in the box, and select **Delete users**
4. **Remove Access** at AWS Accounts:
    - Select **AWS Accounts** and click the name of an AWS account.
    - Remove access with all account access rights.
    - Repeat with the accounts that are assigned access rights to delete.
    ![RemoveAccess](../../../images/3/3_RemoveAccess.png?width=90pc)
5. **Delete Permission Sets**
    - Select **AWS accounts**, select the **Permission sets** tab, and select the relevant permission sets
    - Press **Delete**. At the prompt, type the name of the permission set in the box and click **Delete**.

{{% notice note %}}
Note: Back up the data in these accounts if you need them in the future because deleting an account means that all resources and data belonging to that account will be permanently deleted.
{{% /notice %}}

6. **Delete AWS Accounts**. However, you can keep these accounts for future labs.
    - To delete an AWS account, you need to log in to the account as root user
        - Visit the AWS console login page at https://console.aws.amazon.com/
        - When the **Sign in** page appears, choose to log in with **Root user** and enter the email of the account you want to delete. (Example: example+lab12Logging@amazon.com.vn)
        - Pass Security Check and select **Forgot Password?**
        ![ForgotPassword](../../../images/3/3_ForgotPassword.png?width=90pc)
        - AWS will send forgot password confirmation email to registered email (for example, if your email is example+lab12Logging@amazon.com.vn, AWS email will be sent to example@amazon.com.vn) . Please change your new password via that email and sign in to your AWS account.
    - After logging in as root user, select the account name in the upper right corner, select **My Account**, scroll down to the bottom of the page to see the item **Close Account**. Tick ​​all the boxes and select **Close Account**

{{% notice info %}}
When you create a new AWS account in the AWS Organization, the AWS Organization automatically generates a random password for the root user of that account, and you cannot access them. Therefore, you will access the root user of that account by recovering the forgotten password (*forgot password*)
{{% /notice %}}