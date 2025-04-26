+++
title = "Resource Cleanup"
date = 2024
weight = 6
chapter = false
pre = "<b> 6. </b>"
+++

## Resource Cleanup

After completing this workshop, you need to delete the AWS resources you created in your account to avoid unnecessary charges.

#### Removing CloudFormation Resources

After completing the workshop, delete the CloudFormation stack that was created in the "Testing User and Group-based Access" section.

**⚠️ Warning**: Deleting a CloudFormation stack will remove all resources created by that stack. Ensure you no longer need these resources before proceeding.

To delete the CloudFormation stack:
1. Navigate to the CloudFormation service page in the AWS Management Console
2. Select the stack (with the name you entered)
3. Click the **Delete** button

#### Cleaning Up IAM Identity Center Resources

**ℹ️ Information**: Deleting the IAM Identity Center configuration will remove all users, groups, and permission configurations established within Identity Center.

To clean up all IAM Identity Center resources:

1. Navigate to the IAM Identity Center Console
2. Select the AWS Region recommended by the AWS Team if this is part of an AWS event, or the Region you configured if you're performing this workshop on your own
3. Select **Settings** from the left navigation menu
4. On the Settings page, select the **Management** tab
5. Click the **Delete** button in the "Delete IAM Identity Center configuration" section
6. Enter the instance ID in the text field and click the **Confirm** button in the "Confirm delete settings" dialog box

**💡 Pro Tip**: Before deleting your IAM Identity Center configuration, make sure you've documented any configurations you might want to reference in the future, as configurations cannot be recovered once deleted.

**🔒 Security Note**: After cleanup, verify that all permission sets and assignments have been properly removed to ensure no lingering access remains in your AWS environment.