+++
title = "Add Users and Groups"
date = 2021
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++


#### Add Users and Groups

You need to create Users and Groups as shown in the table below. In which, User in column **User logon name** will belong to Groups in column **Group**.


| User logon name |                  Group           |
|:---------------:|:--------------------------------:|
| Super-User      | AWS-Shared-Services-Admin; AWS-Shared-Services-Read-Only; AWS-Security-Admin; AWS-Security-Read-Only; AWS-Logging-Admin; AWS-Logging-Read-Only; |
| Security-User   | AWS-Security-Read-Only           |

#### Create Group

1. Currently, you still don't have any groups. Select Create group to create the groups listed in the table above


![AWS Account](/images/6/0001.png?featherlight=false&width=90pc)

2. At the prompt to create a group, enter the names of the groups and the descriptions of the groups and then click Create

![AWS Account](/images/6/0002.png?featherlight=false&width=90pc)

3. Repeat this step for the remaining groups

![AWS Account](/images/6/0003.png?featherlight=false&width=90pc)

#### Add User.

1. Open the AWS SSO Console. Select Users in the left sidebar
   - Select Add user and provide the necessary information

![AWS Account](/images/5/0001.png?featherlight=false&width=90pc)

2. Complete the information

- **Username** - This Username will be required to log in to the User portal and cannot be changed later. (Example: Super-User)
- **Password** - Select one of the following options to send the User's password.
- **Send an email to the user with password setup instructions** - With this option, Amazon Web Services will automatically send the User an email inviting the User to access the AWS SSO User portal.
- **Generate a one-time password that you can share with the user** - This option provides a URL to the User portal and a password that you can send to the User yourself. You will choose this option in this exercise. Or select **Send an email to this user with password setup instructions**.
- ***Email address**: enter User's email
- **Confirm email address**: re-enter User's email
- For clarity, use the prefix of the User logon name as the First name and the suffix as the Last name. For example, for Super-User, Super will be the First name, while User will be the Last name Display name

![AWS Account](/images/5/0002.png?featherlight=false&width=90pc)

3. Select **Next**.

![AWS Account](/images/5/0003.png?featherlight=false&width=90pc)

4. Select the groups and select **Next**

![AWS Account](/images/5/0004.png?featherlight=false&width=90pc)

5. Select *Add user**

![AWS Account](/images/5/0005.png?featherlight=false&width=90pc)

6. Complete user creation.

![AWS Account](/images/5/0006.png?featherlight=false&width=90pc)

7. If you select **Send an email to this user with password setup instructions.** then perform email verification to log in.

![AWS Account](/images/5/0007.png?featherlight=false&width=90pc)

8. Select **Send**

![AWS Account](/images/5/0008.png?featherlight=false&width=90pc)

9. Execute **Verify**

![AWS Account](/images/5/0009.png?featherlight=false&width=90pc)

10. Perform password configuration. Note: keep password and portal page to log in.

![AWS Account](/images/5/00010.png?featherlight=false&width=90pc)

![AWS Account](/images/5/00011.png?featherlight=false&width=90pc)

![AWS Account](/images/5/00012.png?featherlight=false&width=90pc)