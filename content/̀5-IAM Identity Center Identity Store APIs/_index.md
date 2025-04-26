+++
title = "IAM Identity Center Identity Store APIs"
date = 2020
weight = 5
chapter = false
pre = "<b> 5. </b>"
+++



#### Overview

This guide explains how to manage and audit AWS IAM Identity Center users and groups at scale using Identity Store APIs. These APIs allow you to automate processes for:

- Provisioning and deprovisioning users and groups
- Adding new members to groups or removing them
- Querying information about users and groups in IAM Identity Center
- Updating information about these users and groups
- Determining which users are members of which groups

#### Prerequisites

Before starting, you should have the following prerequisites:

- An Organization in AWS Organizations
- Administrative access to AWS IAM Identity Center
- Python version 3.10.5 or later
- AWS CLI
- AWS SDK for Python (Boto3)
- Git

#### Environment Setup

Clone the repository:

```
git clone https://github.com/aws-samples/iam-identitycenter-identitystoreapi-operations
```

This repository contains the sample script `identitystore_operations.py` that will be used to perform identity store operations. The script utilizes Python SDKs. You can refer to the boto3 documentation for identity store operations.

**ℹ️ Information**: The Identity Store APIs enable programmatic management of users and groups in IAM Identity Center, supporting large-scale identity management automation.

#### Example: Creating a Group

Here's an example of using the `create_group` method to create a group in Identity Store using the Python SDK:

```python
response = client.create_group(
    IdentityStoreId='string',
    DisplayName='string',
    Description='string'
)
```

The `create_group` method accepts the following parameters:

Parameters:
* **IdentityStoreId** (string) -- [REQUIRED] The globally unique identifier for the identity store.
* **DisplayName** (string) -- A string containing the name of the group. This value is typically displayed when the group is referenced.
* **Description** (string) -- A string containing the description of the group.

**💡 Pro Tip**: Always refer to the boto3 documentation for detailed information about request syntax, response syntax, and exceptions for API operations.

#### Test Setup

In this step, you'll run the Python script `identitystore_operations.py` and view all the supported options available in the script.

> **Note**
> 
> If you're not using the default profile, make sure to configure your shell session with environment variables before running the script.

```
python identitystore_operations.py —h
```

You should see output like the following:

**Sample Output:**
```
usage: identitystore_operations.py [-h]
                                   {create_user,create_group,adduser_to_group,delete_group,list_members,list_membership}
                                   ...
positional arguments:
  {create_user,create_group,adduser_to_group,delete_group,list_members,list_membership}

options:
  -h, --help            show this help message and exit
```

As you can see from the output above, this script supports multiple IdentityStore operations such as Create_user, Create_group, delete_group, List_members, etc.

#### Use Case Prerequisites

In this section, you'll use the Python script to create two SSO groups (AWS_Data_Science & AWS_Applied_Scientists) that will be used in subsequent steps.

You'll need the Identity Store ID to proceed with the remaining steps.

1. Sign in to your AWS account.
2. Navigate to AWS IAM Identity Center settings
3. Copy the Identity store id from the identity store tab. This will be used in the next step.

Run the following command to create the AWS_Data_Science group:

```
python identitystore_operations.py create_group --identitystoreid d-123456a7890 --groupname AWS_Data_Science --description "My Data Science group"
```

> **Note**
> 
> Replace the identitystoreid value "d-123456a7890" with your IdentityStore Id.

You should see output like the following:

**Sample Output:**
```
Group:AWS_Data_Science with GroupId:94482488-3041-7026-18f3-be45837cd0e4 created successfully
```

Similarly, run the following command to create the AWS_Applied_Scientists group:

```
python identitystore_operations.py create_group --identitystoreid d-123456a7890 --groupname AWS_Applied_Scientists --description "Applied Scientist group"
```

> **Note**
> 
> Replace the identitystoreid value "d-123456a7890" with your IdentityStore Id.

You should see output like the following:

**Sample Output:**
```
Group:AWS_Applied_Scientists with GroupId:94482488-3041-7026-18f3-be45837cd0e4 created successfully
```

**⚠️ Warning**: Always verify the Identity Store ID from your AWS IAM Identity Center console before running API operations. Using an incorrect ID will result in errors.

#### AWS IAM Identity Center User and Group API Operations

In this section, you'll use the Python script to create users and update users' group memberships.

#### Create User and Add to a Group

In this step, you'll create a user and add the newly created user to an existing group. You can check the Python code of the create_user function (lines # 9 to # 77) in the identitystore_operations.py Python script for details. This function calls the create_user and create_group_membership APIs for this operation. The Request syntax, Response syntax, and exceptions for these API operations can be found in the boto3 documentation.

This function creates a user and adds the user to a group if the group exists.

If the group doesn't exist, this function will just create the user and skip adding the user to the group.

Required parameters
-------------------
--identitystoreid - Identity Store Id of the SSO configuration
--username  - User Name for the user
--givenname - First Name for the user
--familyname - Last Name for the user

Optional parameters
-------------------
--groupname - Name of the SSO group

Here's an example of how you can create a new user "John Doe" in the IAM Identity Center's identity store and add the user to the existing "AWS_Data_Science" group.

```
python identitystore_operations.py create_user --identitystoreid d-123456a7890 --username johndoe --givenname John --familyname Doe --groupname AWS_Data_Science
```

> **Note**
> 
> Replace the identitystoreid value "d-123456a7890" with your IdentityStore Id.

You should see output like the following:

**Sample Output:**
```
User:johndoe with UserId:94482488-3041-7026-18f3-be45837cd0e4 created successfully
User:johndoe added to Group:AWS_Data_Science successfully
```

**🔒 Security Note**: Always follow the principle of least privilege when assigning users to groups in IAM Identity Center. Only grant access that's necessary for users to perform their job functions.

#### Update User's Group Membership

Now, suppose the data specialist transitions to an applied scientist role and needs access to additional AWS applications and resources. Previously, you would have had to manually update their information and add them to the "AWS_Applied_Scientists" group so they have the right access. Now, your automation can update the user and provide them the access they need. Refer to the Python code of the adduser_to_group function (lines #108 to #154) in the Python script for details. This function calls the get_group_id, get_user_id, and create_group_membership APIs for this operation. The Request syntax, Response syntax, and exceptions for these API operations can be found in the boto3 documentation.

Here's an example of how the previously created user "John Doe" can be added to the "AWS_Applied_Scientists" group:

```
python identitystore_operations.py adduser_to_group --identitystoreid d-123456a7890 --groupname AWS_Applied_Scientists --username johndoe
```

> **Note**
> 
> Replace the identitystoreid value "d-123456a7890" with your IdentityStore Id.

You should see output like the following:

**Sample Output:**
```
User:johndoe added to Group:AWS_Applied_Scientists successfully
```

**💡 Pro Tip**: Use automation for group membership management to ensure consistency and reduce human error, especially in environments with high user turnover or role changes.

#### AWS IAM Identity Center User and Group Audit Operations

In this section, you'll use the Python script to audit user and group memberships.

#### Find Members of a Specific Group

Here's an example of how you can find all members of the "AWS_Applied_Scientists" group. Refer to the list_members function in the Python code (#199 to #232) in the script for details. This function calls the get_group_id and list_group_memberships APIs for this operation. The Response syntax and exceptions for these API operations can be found in the boto3 documentation.

```
python identitystore_operations.py list_members --identitystoreid d-123456a7890 --groupname AWS_Applied_Scientists 
```

> **Note**
> 
> Replace the identitystoreid value "d-123456a7890" with your IdentityStore Id.

You should see output like the following:

**Sample Output:**
```
UserName:johndoe,Display Name: John Doe 
```

#### Find User's Group Membership

Here's an example of how you can find the group membership of a specific user "johndoe". Refer to the list_membership function in the Python code (#235 to #276) in the script for details. This function makes API calls to get_user_id, list_group_memberships_for_member & describe_group for this operation. The Response syntax and exceptions for these API operations can be found in the boto3 documentation.

```
python identitystore_operations.py list_membership --identitystoreid d-123456a7890 --username johndoe
```

> **Note**
> 
> Replace the identitystoreid value "d-123456a7890" with your IdentityStore Id.

You should see output like the following:

**Sample Output:**
```
User :johndoe is a member of the following groups
AWS_Data_Science
AWS_Applied_Scientists
```

**ℹ️ Information**: Regular auditing of group memberships is an essential security practice. Use these commands to create automated reports and verify that users have appropriate permissions.

**🔒 Security Note**: Implement a routine audit process to regularly review group memberships, especially for groups with elevated permissions. This helps maintain the principle of least privilege and ensures compliance with security policies.