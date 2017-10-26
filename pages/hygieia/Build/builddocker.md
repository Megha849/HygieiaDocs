---
title: Build Docker
tags:
keywords:
summary:
sidebar: hygieia_sidebar
permalink: builddocker.html
---

To build a Docker image for all components of Hygieia, execute the following steps:

* **Step 1: Build the containers**

```bash
mvn docker:build
```

* **Step 1: Start the Container Images**

```bash
# Start containers in the background and keep them running
docker-compose up -d
```

* **Step 3: Create a user in Mongo**

If you log into the container then you don't have to install Mongo locally.

Execute the following commands to Connect to MongoDB, and then add dashboard user:

```bash
# Connect to MongoDB
docker exec -t -i mongodb2 bash
```
```bash
mongo 192.168.64.2/admin  --eval 'db.getSiblingDB("dashboarddb").createUser({user: "dashboarduser", pwd: "dbpassword", roles: [{role: "readWrite", db: "dashboarddb"}]})'
```

## Create a `docker-compose.override.yml` to configure your environment

The most commonly used properties are listed and the uncommented properties are mandatory for the collector to work:

```
hygieia-github-scm-collector:
  environment:
  - GITHUB_HOST=github.com
  - GITHUB_CRON=0 * * * * *
  - GITHUB_COMMIT_THRESHOLD_DAYS=300
hygieia-jira-feature-collector:
  environment:
  - JIRA_BASE_URL=https://mycompany.atlassian.net/
  - JIRA_CREDENTIALS=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
  - JIRA_ISSUE_TYPE_ID=10200
  - JIRA_SPRINT_DATA_FIELD_NAME=customfield_10007
  - JIRA_EPIC_FIELD_NAME=customfield_10008
hygieia-jenkins-build-collector:
  environment:
  - JENKINS_CRON=0 * * * * *
  - JENKINS_MASTER=http://192.168.99.100:9100
  - JENKINS_USERNAME=XXXXXXXXXXXXXXXXXXXXXX
  - JENKINS_API_KEY=XXXXXXXXXXXXXXXXXXXXXXXXXX
hygieia-jenkins-cucumber-test-collector:
  environment:
  - JENKINS_CRON=0 * * * * *
  - JENKINS_MASTER=http://192.168.99.100:9100
  - JENKINS_USERNAME=XXXXXXXXXXXXXXXXXXXXXX
  - JENKINS_API_KEY=XXXXXXXXXXXXXXXXX
  - JENKINS_CUCUMBER_JSON_FILENAME=cucumber-report.json
hygieia-sonar-codequality-collector:
  environment:
  - SONAR_URL=http://192.168.99.100:9000
  - SONAR_CRON=0 * * * * *
```

**Note**: For dev/testing the project, change the CRON entries to ``"0 * * * * *"``.

* **Step 4: Restart all Services**

Ensure there is an existing user at start-up.

```bash
#Restarts all stopped and running services.
docker-compose restart
```

To get the port for the UI Layer, execute the following command:

```bash
docker port hygieia-ui
```
