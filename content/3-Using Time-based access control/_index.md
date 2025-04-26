+++
title = "Time-based access control"
date = 2020
weight = 3
chapter = false
pre = "<b> 3. </b>"
+++

There may be scenarios where you want to provide access to specific users or groups for a defined time period, such as granting permissions to Security Auditors during audit periods or to consultants for the duration of a project. In these situations, you can use permission sets with inline policies containing conditions to implement time-based access control.

**ℹ️ Information**: Time-based access control allows you to automatically grant and revoke permissions based on date and time conditions, reducing the operational overhead of managing temporary access.

This guide explores the case of providing temporary access to AWS accounts for Security Auditors. To implement this requirement with time-based access control, you'll complete the following steps:

1. Create a Permission Set with necessary access for Security Auditors as an inline policy with time-based access control conditions
2. Create a Group for Security Auditors
3. Assign users to the Security Auditors Group
4. Assign access to AWS Accounts for the Security Auditors group with the newly created permission set

#### Creating a Permission Set

1. Navigate to the IAM Identity Center Console
2. Select the AWS Region recommended by the AWS Team if this is part of an AWS Event. If you're doing this on your own, select the Region where you intend to configure the rules.

3. Click on Permission sets in the left menu under the Multi-account permissions section and click the Create permission set button.

4. On the Select permission set type page:
   - Select the Custom permission set radio button and click Next.

5. On the Specify policies page:
   - Expand the Inline Policy section, then delete the existing braces.
   - Copy and paste the following permission policy into the text area:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                    "acm:Describe*",
                    "acm:List*",
                    "cloudtrail:Describe*",
                    "cloudtrail:Get*",
                    "cloudtrail:GetTrailStatus",
                    "cloudtrail:ListTags",
                    "cloudtrail:LookupEvents",
                    "cloudwatch:Describe*",
                    "cloudwatch:ListTagsForResource",
                    "config:BatchGetAggregateResourceConfig",
                    "config:BatchGetResourceConfig",
                    "config:Deliver*",
                    "config:Describe*",
                    "config:Get*",
                    "config:List*",
                    "detective:GetGraphIngestState",
                    "detective:ListGraphs",
                    "detective:ListMembers",
                    "ec2:Describe*",
                    "ec2:Get*",
                    "guardduty:DescribePublishingDestination",
                    "guardduty:Get*",
                    "guardduty:List*",
                    "iam:GenerateCredentialReport",
                    "iam:GenerateServiceLastAccessedDetails",
                    "iam:Get*",
                    "iam:List*",
                    "inspector:Describe*",
                    "kms:Describe*",
                    "kms:Get*",
                    "kms:List*",
                    "s3:Get*",
                    "s3:List*",
                    "secretsmanager:DescribeSecret",
                    "secretsmanager:GetResourcePolicy",
                    "secretsmanager:List*",
                    "securityhub:Describe*",
                    "securityhub:Get*",
                    "securityhub:List*",
                    "trustedadvisor:Describe*"
            ],
            "Resource": "*",
            "Condition": {
                "DateGreaterThan": {
                    "aws:CurrentTime": "2022-07-26T00:00:00Z"
                },
                "DateLessThan": {
                    "aws:CurrentTime": "2022-07-27T23:59:59Z"
                }
            }
        }
    ]
}
```

6. Click Next
7. On the Specify permission set details page:
   - Provide a name for the permission set, e.g., secAuditorTimeBased
   - Leave the remaining fields [Description, Session Duration, Relay state, and Tags] as default and click Next

8. On the Review and create page:
   - Review the details provided in the previous steps
   - Click the Create button

**🔒 Security Note**: The time-based condition in this policy uses the global condition key `aws:CurrentTime` that evaluates against the current date and time. The dates in the policy should be in ISO 8601 format with UTC timezone.

#### Creating a Group

Let's create a new Group named securityAuditors:

1. Navigate to the IAM Identity Center Console
2. Select Groups under the Workplace pool section and click Create Group.

3. On the Create group page:
   - Provide Group Name: securityAuditors
   - Provide Description, e.g., Group for security Auditors
   - Click Create group

#### Creating a User and Adding to the Group

For this module, we'll create a new user: secAuditUser

1. Navigate to the IAM Identity Center Console
2. Select Users under the Workplace pool section and click Add User.

3. On the Add User page:
   - Provide Username, e.g., secAuditUser
   - For Password, select the Generate a one-time password that you can share with the user radio button
   - Provide Email Address, using the format email+secaudit@domain.com
   - Confirm the email address provided in the previous field
   - Provide First name: secAudit
   - Provide Last name: user
   - Leave Display name as entered and click Next

4. On the Add users to groups - optional page:
   - Select the SecurityAuditors Group and click Next

5. On the Review and add user page:
   - Review the information provided in the previous steps and click Add user

6. A pop-up window will appear with a One-time password. Copy the information using the Copy button and save it for later use in the workshop.

**💡 Pro Tip**: When working with temporary access, it's a good practice to create functional groups that reflect job roles or responsibilities rather than creating groups for individuals. This approach simplifies access management as people transition between roles.

#### Assigning Permission Set to AWS Account

1. Navigate to the IAM Identity Center Console, select AWS accounts under the Multi-account permissions section
2. Select the account you want users to have access to
3. Click Assign users or groups

4. On the Assign users and Group to AccountName page:
   - Select Groups, select securityAuditors and click Next

5. On the Select permission sets page:
   - Under Permission sets, select secAuditorTimeBased and click Next

6. On the Review and submit page:
   - Review the information and click Submit

7. IAM Identity Center will associate the User group with the Permission set and assign it to the selected AWS Account. You'll see a page with a green banner.

#### Verifying Access

> **Note**:
> For a better experience, you should perform the following verification steps in private browsing mode or a different web browser

1. Log in to the AWS access Portal using the User portal URL saved when creating secAuditUser
2. Provide the username for the user previously created in this module

3. Provide the one-time password for the username
4. Set a new password for the user

5. After successful login, on the SSO portal page, select the Management console link for the secAuditorTimeBased role

6. After successfully logging into the Management Console, navigate to the EC2 console page and confirm that you can list all instances by selecting Instances in the left menu

**ℹ️ Information**: The secAuditorTimeBased permission set includes `ec2:Describe*` permissions, which allow the user to view EC2 resources but not modify them—perfect for audit-related activities.

To simulate access control for Security Auditors, let's update the Permission set and provision it again in our account. We'll simulate this by selecting a timeframe in the past (2022-07-04).

1. Navigate to the IAM Identity Center Console
2. Click on Permission sets in the left menu and select the secAuditorTimeBased permission set

3. Edit the inline policy by clicking the Edit button

4. Copy and replace the permission policy with the code below

   The only change in the policy is the date/time values occurring in the past "2022-07-04T00:00:00Z" "2022-07-04T23:59:59Z"

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                    "acm:Describe*",
                    "acm:List*",
                    "cloudtrail:Describe*",
                    "cloudtrail:Get*",
                    "cloudtrail:GetTrailStatus",
                    "cloudtrail:ListTags",
                    "cloudtrail:LookupEvents",
                    "cloudwatch:Describe*",
                    "cloudwatch:ListTagsForResource",
                    "config:BatchGetAggregateResourceConfig",
                    "config:BatchGetResourceConfig",
                    "config:Deliver*",
                    "config:Describe*",
                    "config:Get*",
                    "config:List*",
                    "detective:GetGraphIngestState",
                    "detective:ListGraphs",
                    "detective:ListMembers",
                    "ec2:Describe*",
                    "ec2:Get*",
                    "guardduty:DescribePublishingDestination",
                    "guardduty:Get*",
                    "guardduty:List*",
                    "iam:GenerateCredentialReport",
                    "iam:GenerateServiceLastAccessedDetails",
                    "iam:Get*",
                    "iam:List*",
                    "inspector:Describe*",
                    "kms:Describe*",
                    "kms:Get*",
                    "kms:List*",
                    "s3:Get*",
                    "s3:List*",
                    "secretsmanager:DescribeSecret",
                    "secretsmanager:GetResourcePolicy",
                    "secretsmanager:List*",
                    "securityhub:Describe*",
                    "securityhub:Get*",
                    "securityhub:List*",
                    "trustedadvisor:Describe*"
            ],
            "Resource": "*",
            "Condition": {
                "DateGreaterThan": {
                    "aws:CurrentTime": "2022-07-04T00:00:00Z"
                },
                "DateLessThan": {
                    "aws:CurrentTime": "2022-07-04T23:59:59Z"
                }
            }
        }
    ]
}
```

5. Save the changes to the Permission set, which provisions the permission set again to the AWS Account

6. Log back into the AWS access portal by following the steps and verify access to EC2 instances. You'll see that secAuditUser no longer has permission to list EC2 instances.

**⚠️ Warning**: When using time-based access control, be aware of timezone differences. AWS uses UTC for time-based conditions, so adjust your dates and times accordingly to avoid unexpected access denials.

**💡 Pro Tip**: For recurring access needs, consider implementing an automated solution using AWS Lambda functions to update the time-based conditions in your permission sets based on a schedule, rather than manually updating policies.