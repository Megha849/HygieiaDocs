---
title: Hygieia-Jenkins Plugin
tags:
keywords: 
summary: Jenkins Plugin for Hygieia
sidebar: hygieia_sidebar
permalink: pluginjenkins.html
---

To configure the Hygieia-Jenkins Plugin, The Hygieia-Jenkins plugin requires installation of:

- Maven 3.3.9
- JDK 1.8

To configure the Hygieia-Jenkins Plugin, execute the following steps:

*	**Step 1: Run Unit Test Cases**

	Run unit test case from `/Hygieia' to check Hygieia code:

	```bash
	mvn test
	```
	
*	**Step 2: Create HPI File**

	Create an HPI file to install in Jenkins. The HPI file is stored at `/Hygieia/hygieia-jenkins-plugin/target/hygieia-publisher.hpi`. Execute the following command to build the Hygieia-Jenkins Plugin:

	```bash
	mvn clean package
	```
	
	The resulting .jar and .hpi files are saved in the target folder.

**Note**: The Hygieia-Jenkins plugin uses the Hygieia core package. The main project is JDK 1.8 compiled, if you have Jenkins running on Java versions prior to Java v1.8, ensure to recompile Hygieia's core package with the previous version and then build the Jenkins plugin.

### Jenkins 2.0 with Pipeline 

1. Install the plugin by using 'Advanced' option in Jenkins Plugin Management option to manually upload the file from local disk.
2. Restart Jenkins.
3. Configure Global Hygieia Publisher in Jenkins Manage Jenkins/Configure System. Enter Hygieia API url such as `http://localhost:8090/api`. There is no API token implented at this time and it is work in progress.
![NewLink](/media/images/jenkins-global.png)
4. In Jenkins pipeline syntax page, Hygieia publish steps are displayed:
![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins2.0-steplist.png)
5. Select a step (for example, Hygieia Deploy Step), fill in the required information and click 'Generate Pipeline Script'. The generated script can now be copied to the pipeline script:
![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins2.0-hygieia-deploy-step.png)
6. Screenshot below shows a simple pipeline script with maven build, hygieia artifact and deploy publishing.
![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins2.0-pipeline-deploy-publish.png)

## Jenkins (pre Jenkins 2.0)

1. Install the plugin by using 'Advanced' option in Jenkins Plugin Management to manually upload the file from local disk.
2. Restart Jenkins.
3. Configure Global Hygieia Publisher in Jenkins Manage Jenkins/Configure System. Enter Hygieia API url such as `http://localhost:8090/api`. There is no API token implemented at this time and it is work in progress.

![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins-global.png)

4. For a build job, add a Post build action 'Hygieia Publisher'. 
5. Select what to send to Hygieia. Currently, 'Build', 'Artifact Info', 'Sonar Anslysis', 'Deployment' and 'Cucumber Test Results' can be published.

![Image](https://megha849.github.io/HygieiaDocs/media/images/jenkins-job-config.png)

### Troubleshooting Instructions

The build fails due to the following maven error:

`[ERROR] Failed to execute goal on project hygieia-publisher: Could not resolve dependencies for project org.jenkins-ci.plugins:hygieia-publisher:hpi:1.3-SNAPSHOT: Could not find artifact com.capitalone.dashboard:core:jar:2.0.2-SNAPSHOT in anonymous (https://mycompany.nexus.com/nexus/content/groups/CLM) -> [Help 1][ERROR]`

In this case, before you build the Hygieia-Jenkins Plugin, clone Hygieia root, change directory to `/Hygieia/core', and execute the following command:

```bash
mvn clean install
```
