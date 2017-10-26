---
title: 
tags:
keywords: 
summary: Jenkins Plugin for Hygieia
sidebar: hygieia_sidebar
permalink: pluginjenkins.html
---
## Hygieia-Jenkins Plugin

Hygieia collectors are classified into the following types for data collection:

- Pull-based Collectors - These collectors pull all information from the DevOps tools. 
- Push-based Collectors - These collectors collect a subset of data from the DevOps tools.

The Hygieia-Jenkins plugin is a push-based collector that supports the Jenkins pipeline code for continuous integration and delivery. You can use the Hygieia-Jenkins plugin to publish data from Jenkins to the Hygieia dashboard. You can publish build and artifact information, sonar test results, deployment results, and Cucumber test results. Therefore, you need not run the corresponding collectors if you use Jenkins for build, deploy, sonar analysis and cucumber tests.

The Hygieia-Jenkins plugin requires installation of:

- Maven (recommended version 3.3.9 and above)
- JDK (recommended version 1.8)

To configure the Hygieia-Jenkins Plugin, execute the following steps:

*	**Step 1: Run Unit Test Cases**

	From your project's root directory, run the unit test cases to check Hygieia code:

	```bash
	mvn test
	```
	
*	**Step 2: Create HPI File**

	Create an HPI file to install in Jenkins. The HPI file is stored at `\Hygieia\hygieia-jenkins-plugin\target\hygieia-publisher.hpi`. To build the Hygieia-Jenkins Plugin, execute the following command:

	```bash
	mvn clean package
	```
	
	The output file `hygieia-publisher.jar` is generated in the `\hygieia-jenkins-plugin\target` folder.

**Note**: The main project is compiled using JDK v1.8. If you are running Jenkins on Java versions prior to Java v1.8, recompile Hygieia’s core package with the prior version, and then build the Jenkins plugin.

### Jenkins 2.0 with Pipeline

To install the plugin in Jenkins:

1. In the Jenkins toolbar, navigate to Manage Plugins > Advanced Tab.
2. In the 'Upload Plugin' section, click 'Choose File', navigate to the `\hygieia-jenkins-plugin\target` folder, and then select the .hpi file. Click Upload. 
   
   Once the plugin is installed, you can view the plugin listed in the 'Installed' tab.
3. Restart Jenkins.
4. Configure Global Hygieia Publisher in Jenkins Manage Jenkins/Configure System. Enter Hygieia API url such as `http://localhost:8080/api`.

5. In Jenkins pipeline syntax page, Hygieia publish steps are displayed:

![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins2.0-steplist.png)

6. Select a step (for example, Hygieia Deploy Step), fill in the required information and click 'Generate Pipeline Script'. The generated script can now be copied to the pipeline script:

![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins2.0-hygieia-deploy-step.png)

7. Screenshot below shows a simple pipeline script with maven build, hygieia artifact and deploy publishing.

![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins2.0-pipeline-deploy-publish.png)

### Jenkins (pre Jenkins 2.0)

1. Install the plugin by using 'Advanced' option in Jenkins Plugin Management to manually upload the file from local disk.
2. Restart Jenkins.
3. Configure Global Hygieia Publisher in Jenkins Manage Jenkins/Configure System. Enter Hygieia API url such as `http://localhost:8080/api`. 

![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins-global.png)

4. For a build job, add a Post build action 'Hygieia Publisher'. 
5. Select what to send to Hygieia. Currently, 'Build', 'Artifact Info', 'Sonar Anslysis', 'Deployment', and 'Cucumber Test Results' can be published.

![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins-job-config.png)

### Troubleshooting Instructions

The build fails due to the following maven error:

`[ERROR] Failed to execute goal on project hygieia-publisher: Could not resolve dependencies for project org.jenkins-ci.plugins:hygieia-publisher:hpi:1.3-SNAPSHOT: Could not find artifact com.capitalone.dashboard:core:jar:2.0.2-SNAPSHOT in anonymous (https://mycompany.nexus.com/nexus/content/groups/CLM) -> [Help 1][ERROR]`

In this case, before you build the Hygieia-Jenkins Plugin, clone Hygieia root, change directory to `\Hygieia\core`, and execute the following command:

```bash
mvn clean install
```

## GitHub Webhook

You can use GitHub webhooks to publish commit information to the Feature widget in Hygieia dashboard. If you use webhooks, you need not run the github collector.

Your Github webhook’s payload url should be set to: http://hygieia-base-url/api/commit/github/v3. Select to publish just the “push” events.