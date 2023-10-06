+++
title = "Enable AWS SSO"
date = 2021
weight = 1
chapter = false
pre = "<b>2.1 </b>"
+++

#### Activate AWS SSO

1. Log in to the **AWS Management Console** using the credentials of the **AWS Organization** master account.

   ![AWS Account](/images/2/0001.png?featherlight=false&width=90pc)

2. Open the **AWS SSO Console**.

   ![AWS Account](/images/2/0002.png?featherlight=false&width=90pc)

3. Choose the **Enable AWS SSO** option.

   ![AWS Account](/images/2/0002.png?featherlight=false&width=90pc)

AWS SSO's Single Sign-On feature provides a default repository for storing Users and Groups. If you opt to host them in AWS SSO, the process involves:

- Creating a User and Group.
- Adding the User as a Group member.
- Specifying Groups with the desired level of access to AWS accounts and applications.

   ![AWS Account](/images/2/0003.png?featherlight=false&width=90pc)
