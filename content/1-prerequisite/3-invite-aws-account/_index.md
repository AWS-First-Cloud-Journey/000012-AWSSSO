+++
title = "Create Users and Groups in IAM Identity Center"
date = 2025
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++

#### Create Users and Groups in IAM Identity Center

**ℹ️ Information:** This section guides you through creating users and groups in the built-in identity store of IAM Identity Center.  
If you want to configure an External Identity Provider (IdP) as the identity source, refer to the “Using External IdP with IAM Identity Center” section in *Extra Credit*.

#### Choosing an Identity Source

**ℹ️ Information:** The selected identity source determines where IAM Identity Center retrieves users and groups for SSO access.  
By default, IAM Identity Center provides a built-in identity store for fast and simple user management.  
This is an ideal option for small organizations or testing environments.

**💡 Pro Tip:** For enterprise environments, you can connect IAM Identity Center to **Microsoft Active Directory** (via **AWS Directory Service**) or integrate with external identity providers that support **SAML 2.0**, such as **Okta**, **Microsoft Entra ID** (formerly Azure AD), or **Google Workspace**.

#### Managing Identities in IAM Identity Center

Users and groups that you create in the IAM Identity Center’s built-in identity store exist only within IAM Identity Center.  
Follow the steps below to add users and groups to your identity store.

---

### Steps

#### 1. Create Groups

**ℹ️ Information:** In this workshop, we will create two groups: **Administrators** and **readOnly**.  
Groups help organize users by their roles and responsibilities, simplifying access management.

1. Navigate to the **IAM Identity Center Console**  
2. Select **Groups** and click **Create Group**  

![3.4.11](/images/0001/image006.png)

3. On the **Create group** page:  
   - Enter a **Group Name**, for example: `Administrators`  
   - Enter a **Description**, for example: `Group for administrator users`  
   - Click **Create group**  

![3.4.11](/images/0001/image07.png)

4. A green success banner will appear confirming that the *Administrators* group was created successfully.  
5. Repeat steps 1–3 to create the **readOnly** group.  

![3.4.11](/images/0001/image08.png)

**💡 Pro Tip:** Organizing users into groups enables more efficient access management and makes it easier to apply role-based permission policies.  
When your organizational structure changes, you only need to update group memberships rather than adjusting individual user permissions.

**🔒 Security Note:** Follow the **principle of least privilege** by creating groups with specific and limited permissions.  
This minimizes security risks and simplifies access audit and compliance.

---

#### 2. Create Users

**ℹ️ Information:** In this workshop, we’ll create two users: **adminUser** and **readOnlyUser**, to demonstrate different access levels.

1. Navigate to the **IAM Identity Center Console**  
2. Under the **Workforce pool**, select **Users**, then click **Add User**  

![3.4.11](/images/0001/image09.png)

3. On the **Add User** page:  
   - Enter **Username**, e.g. `adminUser`  
   - For **Password**, select **Generate a one-time password that you can share with the user**  
   - Enter **Email Address** using a format such as `email+admin@domain.com`  
   - Confirm the email address  
   - Enter **First name**  
   - Enter **Last name**  
   - Keep **Display name** as entered  
   - Click **Next** (you can explore optional fields if desired)  

![3.4.11](/images/0001/image10.png)

4. On the **Add users to groups (optional)** page:  
   - Select the **Administrators** group  
   - Click **Next**  

![3.4.11](/images/0001/image11.png)

5. On the **Review and add user** page:  
   - Review the information provided in previous steps  
   - Click **Add user**  

![3.4.11](/images/0001/image12.png)

6. A pop-up window will appear displaying the **One-time password**.  
   Click **Copy** to save this password for later use in the workshop.  

![3.4.11](/images/0001/image013.png)

**🔒 Security Note:** The one-time password is displayed only once and cannot be retrieved later.  
Ensure it is securely stored and shared via a secure channel.  
In production environments, you should enable **Multi-Factor Authentication (MFA)** for all users to enhance security.

**⚠️ Warning:** Repeat steps **1–6** to create the **readOnlyUser**.  
Use a unique email different from the admin user (e.g. `username+readonly@domain.com`) and make sure to assign this user to the **readOnly** group in Step 4.

**💡 Pro Tip:** IAM Identity Center supports **user lifecycle management**, including creation, updates, deactivation, and deletion.  
In enterprise environments, these processes can be automated via HR system integration or AWS APIs.

---

You have successfully created two new users and groups.  
Using IAM Identity Center, these users can now access multiple AWS accounts within your AWS Organization with appropriate permissions based on their roles.
