+++
title = "Inviet AWS Account to AWS Organization"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++

In step 1.1, you created a new AWS Account from the AWS Organization service! So if you already have one or more AWS Accounts with Workloads running & you want to add that AWS Account to your Organization to easily allocate resources, group accounts (like step 1.2,) and apply the following best pratice managed principles -> then the **Invite an existing AWS accoun** function will assist you.

1. Add AWS Account to Organizations

- Go to **AWS Management Comsole** and look for **AWS Organizations** service in the search bar.

- Select **Add an AWS account**

![AWS Account](/images/10/0001.png?featherlight=false&width=90pc)

- Select **Invite an existing AWS account**

- In the **Email address or account ID of the AWS account to invite** field, enter the email address or Account ID of the AWS Account you want to add to the Organization, for example: `fcj@amazon.com.vn` or 888800009920

- Select **Send invitation**

![AWS Account](/images/10/0002.png?featherlight=false&width=90pc)

2. Check your invitation to join Organizations

- In the left pane, select **Invitations**, you will see the Account ID you just added in step 1 - appeared here with the status **OPEN**

![AWS Account](/images/10/0003.png?featherlight=false&width=90pc)

3. Accept an invitation to join Organizations

- Access the **AWS Management Comsole** of the Account you just added in step 1, find the **AWS Organizations** service in the search bar

![AWS Account](/images/10/0004.png?featherlight=false&width=90pc)

- On the right side of the screen, select the invitation **View 1 invitation**
- In addition, the AWS Organization service is free of charge

![AWS Account](/images/10/0005.png?featherlight=false&width=90pc)

**Note**: you can only see the above invitation, if and only if this AWS Account has not joined any **AWS Organizations**

4. Select **Accept invitation**

![AWS Account](/images/10/0006.png?featherlight=false&width=90pc)

- Result:

![AWS Account](/images/10/0007.png?featherlight=false&width=90pc)

- Even though you are on **Dashboard**, you can only see the information of **Organizations** that you are attending, because you are a member account

5. Check **AWS Organizations**

- Go back to AWS Account in step 1, check if the Account just added in step 4 has joined Organizations or not

![AWS Account](/images/10/0008.png?featherlight=false&width=90pc)

- Here, you can see the entire structure of **Organizations** including Organization Units with member accounts & management accounts.

- With **management account** will be the main acc to manage and access **member accounts** through **switch role** function

Congratulations, AWS Account has been added with join date details