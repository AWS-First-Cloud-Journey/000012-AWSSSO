+++
title = "Add Users and Groups"
date = 2021
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++


#### Add Users and Groups

To proceed, you need to create users and groups as detailed in the table below. Users listed under the **User logon name** column will be assigned to the respective groups listed under the **Group** column.

| User logon name | Groups |
|:---------------:|:------:|
| Super-User      | AWS-Shared-Services-Admin; AWS-Shared-Services-Read-Only; AWS-Security-Admin; AWS-Security-Read-Only; AWS-Logging-Admin; AWS-Logging-Read-Only; |
| Security-User   | AWS-Security-Read-Only |

#### Create Groups

1. At present, there are no existing groups. Choose "Create group" to establish the groups mentioned in the table above.

   ![AWS Account](/images/6/0001.png?featherlight=false&width=90pc)

2. Follow these steps to create a group:
   - Provide group names and descriptions when prompted.
   - Click "Create."

   ![AWS Account](/images/6/0002.png?featherlight=false&width=90pc)

3. Repeat this process for the remaining groups.

   ![AWS Account](/images/6/0003.png?featherlight=false&width=90pc)

#### Add User

1. Open the AWS SSO Console and access the "Users" section from the left sidebar.
   - Click on "Add user" and furnish the required information.

   ![AWS Account](/images/5/0001.png?featherlight=false&width=90pc)

2. Complete the user information as follows:
   - **Username:** This will serve as the login ID and cannot be changed later. (Example: Super-User)
   - **Password:** Choose one of the following methods to deliver the user's password:
     - "Send an email to the user with password setup instructions": AWS will automatically send an email to the user for accessing the AWS SSO User portal.
     - "Generate a one-time password that you can share with the user": Provides a URL and password to be sent manually. Choose this option in this exercise, or select the email option.
   - **Email address:** Enter the user's email.
   - **Confirm email address:** Re-enter the user's email.
   - For clarity, utilize the prefix of the user's logon name as the first name and the suffix as the last name. For instance, for "Super-User," the first name would be "Super" and the last name "User."

   ![AWS Account](/images/5/0002.png?featherlight=false&width=90pc)

3. Click **Next**.

   ![AWS Account](/images/5/0003.png?featherlight=false&width=90pc)

4. Select the relevant groups and click **Next**.

   ![AWS Account](/images/5/0004.png?featherlight=false&width=90pc)

5. Click **Add user**.

   ![AWS Account](/images/5/0005.png?featherlight=false&width=90pc)

6. Complete the user creation process.

   ![AWS Account](/images/5/0006.png?featherlight=false&width=90pc)

7. If you chose the "Send an email to this user with password setup instructions" option, follow the email verification steps for logging in.

   ![AWS Account](/images/5/0007.png?featherlight=false&width=90pc)

8. Click **Send**.

   ![AWS Account](/images/5/0008.png?featherlight=false&width=90pc)

9. Execute the **Verify** action.

   ![AWS Account](/images/5/0009.png?featherlight=false&width=90pc)

10. Perform the password configuration. Note: Keep the password and portal page details for future logins.

   ![AWS Account](/images/5/00010.png?featherlight=false&width=90pc)

   ![AWS Account](/images/5/00011.png?featherlight=false&width=90pc)

   ![AWS Account](/images/5/00012.png?featherlight=false&width=90pc)
