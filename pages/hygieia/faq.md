---
title: FAQs
tags:
keywords:
summary: Frequently Asked Questions 
sidebar: hygieia_sidebar
permalink: faq.html
---

**Unable to configure the GitHub Collector for a Private Repo**

To configure the GitHub collector for a private repository, generate a secret key and add the secret key and your user ID to the API properties file. For detailed instrcutions, see [Encryption for Private Repos](#encryption-for-private-repos).

To pass the github authentication information in the application.properties file, modify DefaultGitHubClient.java and force the response string to fetch the password from properties file:

//ResponseEntity<String> response = makeRestCall(queryUrlPage, settings.getUserId(), decryptedPassword);
ResponseEntity<String> response = makeRestCall(queryUrlPage, settings.getUserId(), settings.getKey());

**How to change the UI port to a port other than 3000?**

By default, the UI uses port 3000 to display the dashboard. To change the port, make the following changes to the `gulpfile.js`:

```bash
browserSync.init({
          port: 9999,
          server: {
              baseDir: hygieia.dist,
              startPath: '/',
              middleware: [proxyMiddleware]
          },
          ghostMode: ghostMode
      });
```

Restart the API service. In addition, clear the browser cache and cookies or use incognito tab to launch UI, and then run the following in the command line or terminal:

```
gulp serve
```
 
**How to remove unconfigured widgets from the dashboard?**

To remove unconfigured widgets from a dashboard, execute the following:

1. Signup and login as 'admin' user. For detailed instructions, see[Signup and Login](signup.md).
2. Create a custom template by choosing the widgets that appear on the dashboard. For detailed instruction, see [Manage Dashboard Templates](signup.html#manage-dashboard-templates).

**Error while building API layer**

When setting up the API layer, the following error is displayed:

```
INFO  org.mongodb.driver.cluster - Exception in monitor thread while connecting to server 10.0.0.0:27017
com.mongodb.MongoSocketOpenException: Exception opening socket
```

In this case, make sure to connect to your MongoDB instance and the MongoDB user `dashboarduser` is created with password `dbpassword`. 

For detailed instructions on Hygieia database setup based on your platform, see [Database Setup](database.md).

Once the database setup is complete, following steps in the [API Configuration](api.md) document to complete the API setup.
