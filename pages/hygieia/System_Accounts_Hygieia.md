## Privileged System Accounts in Hygieia

To create or edit dashboards in Hygieia, there are two main user types:

- Admin User
- Other Users

The process to create and manage these user types is described in the following sections.

### Hygieia Admin Users

In Hygieia, the **admin** user allows you to manage and maintain a level of control on the dashboard users. For each instance of Hygieia, there can only be one **admin** user.

### Create an `admin` User

You must create an **admin** user in Hygieia to manage and maintain other dashboard users.

To create an account for an **admin** user:
1. Click **Signup** on the login page.
2. Enter **admin** as the username, specify and confirm the password, and then click **Signup**.

![Image](https://github.com/Megha849/HygieiaDocs/blob/gh-pages/media/images/adminuser.png)

### Manage Administrators for your Hygieia Instance

In the **Admin** screen, the **Manage Admins** tab displays a list of all users. To add additional dashboard administrators:

- In the **Users** column, select a user, and then click the right-arrow button.
  The username is displayed in the **Admin** column.

To find users, filter the list by entering all or part of a user name in the **Search** field.

To remove an admin:

- In the **Admin** column, select an admin, and then click the right-arrow button.
  The username is displayed in the **Admin** column.

![Image](https://github.com/Megha849/HygieiaDocs/blob/gh-pages/media/images/manage_admins.png)  
  
### Create Other Users in Hygieia

To create an account for a new user:

1.	Click **Signup** in the login page to create a user account.
2.	Enter a username, password, confirm the password, and then click **Signup**.

The user who creates an account in Hygieia and subsequently a team or product dashboard, will be the owner of these dashboards.

#### User Authentication in Hygieia

Hygieia dashboards provide the following options for user authentication:

- LDAP allows you to use your LDAP server to authenticate users. To enable SSO (Single Sign On) authentication, you must configure Hygieia with your LDAP server to authenticate users. 
- Standard authentication uses an internal database of users and passwords. If you choose to create an internal database, the user names and passwords will not be in sync with the LDAP server.
