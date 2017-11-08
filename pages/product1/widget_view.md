---
title: Widget View
tags: 
type: 
homepage: 
toc: true
sidebar: product1_sidebar
permalink: widget_view.html
---

The widget view gives more detailed information about the features, code contribution, continuous integration, deployment, and environment status.

## Standard Dashboard Widgets

|Widget | Description |
|-------|-------------|
|Features | Displays features in the current sprint to help you track epics or issues in a sprint type feature from feature management tools |
|Repo | Displays code contribution activities from one of the supported code repositories. |
|Build | Displays build status |
|Quality and Performance | Displays the code quality and performance details based on unit and functional test results. |
|Deploy | Displays deployment and environment status details |
|Monitor | Displays monitor details |

## Configure Widgets - Common Procedure

To configure a widget in the dashboard:
1.	Click Configure Widget under the widget name for which you want to configure your DevOps Dashboard.
The Configure <Widget Name> Widget dialog box is invoked.
2.	In the Configure <Widget Name> Widget screen, enter configuration values for the fields, and then click Save.
The Dashboard widget displays values and status based on your configuration.

### Configure Feature Widget

1. Click 'Configure widget' to invoke the Configure Feature Widget screen. In this screen, enter the following details:
   - Agile Content Tool Type: Select one of the following feature data source:
     - JIRA
     - VersionOne
   - Project Name - Enter a new project name or select one of the existing projects from the list of projects.
   - Team Name: Enter a team name
   - Estimate Metric: Estimate metrics are:
     - Hours
     - Issue Count
     - Story Points
   - Sprint Type - Select a sprint type:
     - Sprint
     - Kanban
     - Both
   - List Feature Type - Select one of the following feature type:
     - Epics
     - Issues

2. Click 'Save' to save all the details and view the Feature-related details in the widget.

Based on the configuration, Hygieia displays the following details in the Features widget:

- Total number of features in a sprint type
- Total number of features that are in Progress
- Total number of features that have been completed for a sprint
- List of all features that are in progress

### Configure Repo Widget

1. Click 'Configure widget' to invoke the Configure Feature Widget screen. In this screen, enter the following details:
   - Select the Repo Type from the dropdown list:
     - GitHub
	 - Subversion
	 - Bitbucket
	 - Gitlab
   - Enter the Repo URL for the selected Repo Type
   - Enter the Branch for the repo. The repo branch is not applicable for Subversion.
   - Enter the repo login credentials. The login credentials is not applicable for Gitlab.
   - Enter the API Key for a private Gitlab repo.
   
2. Click 'Save'. The Repo Widget is configured for the selected repo.

### Configure Build Widget

1. Click 'Configure widget' to invoke the 'Configure Feature Widget' screen. In this screen, enter the following details:
   - Enter the Build Job 
   - Enter the Build Duration Threshold (in minutes). By default, 3 minutes is displayed.
   - Alert Takeover Criteria indicates the number of consecutive build fails. By default, 5 consecutive build fails is displayed.
2. Click 'Save'. The Build Widget is configured for the selected repo.

### Configure Quality and Performance Widget

1. Click 'Configure widget' to invoke the 'Configure Code Analysis Widget' screen. In this screen, enter the following details:
   - Static Code Analysis
   - Security Scan
   - Open Source Scan
   - Functional Tests
2. To configure functional tests:
   - Click the add button, enter a name for the test, and then select a functional test from the drop-down.
3. Click 'Save'. The code quality Widget is configured for the selected code analysis job.

To configure the Performance widget:

1. In the Performance tab, click 'Configure widget' to invoke the 'Configure Performance Widget' screen. In this screen, enter the following details:
   - Select a Performance Analysis Job from the drop-down and then click 'Save'.
   
### Configure Deploy Widget

1. In the Performance tab, click 'Configure widget' to invoke the 'Configure Deploy Widget' screen. In this screen, enter the following details:
   - Select the deployment application.
   - Enter the criteria to ignore the environment failures pattern.
   - Check the 'Aggregate servers' box to avoid server duplication.
2. Click 'Save'. 

### Configure Monitor Widget

1. Click 'Configure widget' to invoke the 'Monitor Configuration' screen. In this screen, enter the following details:
   - In 'Our Services' section, Enter the test name and service URL. 
     Click the add button to add additional services.
   - In the 'Dependent Services' section, select a dependent service from the drop-down list. 
     Click the add button to add additional services.
2. Click 'Save'. 