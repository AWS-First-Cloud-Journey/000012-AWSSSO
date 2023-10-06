+++
title = "Invite AWS Account to AWS Organization"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++

#### Adding an AWS Account to Organizations

#### Step 1: Invite an Existing AWS Account

1. Go to the **AWS Management Console** and search for the **AWS Organizations** service in the search bar.
2. Select **Add an AWS account**.
   ![AWS Account](/images/10/0001.png?featherlight=false&width=90pc)
3. Choose **Invite an existing AWS account**.
4. Enter the email address or Account ID of the AWS Account you wish to add to the Organization, e.g., `fcj@amazon.com.vn` or 888800009920.
5. Click on **Send invitation**.
   ![AWS Account](/images/10/0002.png?featherlight=false&width=90pc)

#### Step 2: Check Your Invitation to Join Organizations

1. In the left pane, select **Invitations**. You will see the Account ID you added in step 1, with the status **OPEN**.
   ![AWS Account](/images/10/0003.png?featherlight=false&width=90pc)

#### Step 3: Accept an Invitation to Join Organizations

1. Access the **AWS Management Console** of the Account you added in step 1 and find the **AWS Organizations** service in the search bar.
   ![AWS Account](/images/10/0004.png?featherlight=false&width=90pc)
2. On the right side of the screen, select the invitation **View 1 invitation**.
3. Note that the AWS Organization service is free of charge.
   ![AWS Account](/images/10/0005.png?featherlight=false&width=90pc)
4. Select **Accept invitation**.
   ![AWS Account](/images/10/0006.png?featherlight=false&width=90pc)
5. Result:
   ![AWS Account](/images/10/0007.png?featherlight=false&width=90pc)
6. Please note that you will only see this invitation if the AWS Account has not already joined any **AWS Organizations**.

#### Step 4: Check AWS Organizations

1. Go back to the AWS Account from step 1 and verify if the Account added in step 3 has joined Organizations.
   ![AWS Account](/images/10/0008.png?featherlight=false&width=90pc)
2. Here, you can view the entire structure of **Organizations**, including Organization Units with member accounts and management accounts.
3. The **management account** will serve as the main account to manage and access **member accounts** through the **switch role** function.

Congratulations, the AWS Account has been successfully added with join date details.
