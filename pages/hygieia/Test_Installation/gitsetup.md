---
title: 
tags:
keywords:
summary:
sidebar: hygieia_sidebar
permalink: gitsetup.html
---

## Set up Git

To set up git, configure the GitHub URL for Hygieia master branch 

## 1. Set up Git - by configuring it to point to the Github master branch for Hygieia
	a. In the SCM panel, select _git_
	b. Enter the URL: `https://github.com/capitalone/Hygieia.git`
	c. Set the branch to `master`.
	Note: For this to work you will need to have set your credentials on the ID that the collectors is running under, the best way to do this is first clone the repo to set your credentials.

For steps to configure GitHub on the dashboard, refer section, 'Configure Code Repo Widget' in the Dashboard Configuration documentation.

## Set up Sonar

2. Setup Sonar - by running a test instance of sonar
	a. `docker-compose -f test-servers/sonar/sonar.yml up -d`
	b. Fill it with data from the Hygieia project
	
```bash
mvn sonar:sonar - Dsonar.host.url=http://$(docker-machine ip default):9000 -Dsonar.jdbc.url="jdbc:h2:tcp://$(docker-machine ip default)/sonar"
```

	c. You can now go in and configure the quality panel in the UI.

## Set up Jenkins

3. Set up Jenkins with Cucumber output - by starting a test Jenkins master
	a. `docker-compose -f test-servers/jenkins/jenkins.yml up -d`
	b. Run the job: http://192.168.99.100:9100/job/Hygieia_Example_Job/build
	c. Configure the Jenkins Build and Jenkins Cucumber panels using this jobs output.
	
## Start Collectors in the background (optional, as they are all running in containers by default)
* To start individual collector as background processes, use this format:
  * On linux platform
  
```bash
nohup java -jar <collector-name>.jar --spring.config.name=<property file name> & >/dev/null
```
