---
title: Signup and Login
tags: 
homepage: 
toc: true
sidebar: product1_sidebar
permalink: signup.html
---

## User Authentication

Hygieia dashboards provide the following options for user authentication:

- LDAP allows you to use your LDAP server to authenticate users.
- Standard authentication uses an internal database of users and passwords. If you choose to create an internal database, the user names and passwords will not be in sync with the LDAP server.
- Single Sign On (SSO) 

To modify the user authentication type for the dashbaord, see the [API Properties]() file.

Before you login to the Hygieia dashboard, choose a login type:
- Standard Login
- LDAP Login
- Single Sign On (SSO)

## Create and Manage Admin Users 

Hygieia dashboards provide administrator and user access through various views. An admin user can:

- Select a theme for the dashboard
- Manage user and admin accounts for the dashboard
- Set up API tokens for authentication
- Create and manage custom dashboard templates

### Create Admin User

Once you have installed the UI layer in Hygieia, you must create an admin user as the first user of the dashboard. This allows the admin user to manage and maintain a level of control on the dashboard users. 

To create an account for an admin user:
1. Click Signup in the login page.
2. Enter 'admin' as the username, specify and confirm the password, and then click Signup.

The 'admin' user is created for the dashboard. 

### Manage Administrators

In the Admin screen, the 'Manage Admins' tab displays a list of all users. To add additional dashboard administrators:

- In the 'Users' column, select a user, and then click the right-arrow buttom. 
  The username is displayed in the 'Admin' column. 

To find users, filter the list by entering all or part of a user name in the 'Search' field.

To remove an admin:

- In the 'Admin' column, select an admin, and then click the right-arrow button.
  The username is displayed in the 'Admin' column.

### API Token for User Authentication

Generate an API token for basic authentication to secure APIs. To generate an API token:

1. Click 'New'. The 'Generate API Token' dialog box in invoked.
2. Enter the API User name. 
3. Select an Expiration Date using the calendar button.
4. Click 'Create'. The generated API key is displayed. 

Note: The API key is visible only until the 'Generate API Token' dialog box is open.

Copy the API token to the [API properties]() file.

To know more about securing basic authentication for APIs, see ['Secure APIs Basic Authentication'](api.md#secure-apis-basic-authentication).

### Select a Dashboard Theme

Select one of the following themes for the dashboard:
- Dash
- Dash for display
- Bootstrap
- BS Slate

By default, the Dash theme is selected.

### Manage Dashboard Templates

1. Click 'Create a new template'. The 'Create Custom Templates' dialog box is invoked.
2. Enter the template name, and then select the widgets for your dashboard.
3. Click 'Create'. The dashboard template is created.

To edit the template:

1. Click the edit icon beside the template name. The 'Edit Template Details' screen is invoked.
2. Check/uncheck the widget options to add/delete widgets from the dashboard.
3. Click Save.

To delete a template, click the Delete icon beside the template name. The template is deleted.

Note: You cannot delete templates that are being used in existing dashboards. 

## Sign up and Login Instructions

To create an account for a new user:

1.	Click Signup in the login page to create a user account.
2.	Enter a username, password, confirm the password, and then click Signup.

If you already have your login credentials, enter the username and password, and then click Login.
