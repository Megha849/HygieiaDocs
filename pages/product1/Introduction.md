---
title: Hygieia - The DevOps Dashboard
tags: 
type: first_page
homepage: true
toc: false
sidebar: hygieia_sidebar
permalink: Introduction.html
redirect_from:
  - /index.html
  - /hygieia/Introduction.html
---

## Introduction

Hygieia dashboard is a single, configurable, easy-to-use dashboard to visualize near real-time status of the entire delivery pipeline. In addition, it provides a continuous feedback loop for any DevOps organization.

Hygieia dashboards are customizable: you can select your story tracking tools, code repository, users can select VersionOne or Jira for story tracking, Subversion or GitHub as repositories, Jenkins/Hudson for builds, Selenium and SonarQube for quality, uDeploy and Jenkins for deployment. More plugins are available.

Hygieia dashboards assist in achieving process transparency and therefore help establish feedback loops that are the underlying concept of lean and DevOps. They contain interactive elements which enable drill-down and linking to the connected tools.

## Overview

Hygieia is a single, configurable, easy-to-use dashboard to visualize near real-time status of the entire delivery pipeline. The health of the continuous delivery pipeline, from code commit to production deployment, with all the necessary information around health and quality of the software, is essential for any DevOps Organization.
	
## Audience

The Dashboard Console provides configuration procedures for all the DevOps toolsets that appear on the Console. This document describes the procedure for performing basic configuration.

This guide is intended for a technical audience to implement and support the application. The audience should have knowledge of Java, MongoDB, Javascript, Git, and RESTful APIs.

## Dashboard Views

A view is a primary mechanism for displaying data. The Hygieia dashboard offers a comprehensive overview through the following view methods:

Widget View - Widget view showcases detailed information, which include features in the current sprint, code contribution activities, continuous integration activities, code analysis, security analysis, unit and functional test results, and deployment and environment status.
Pipeline View - The pipeline view pulls back to show each component’s lifecycle progression through the development, testing, and deployment stages.
Product View - The product view displays each configured product's progression from commit to deployment.
Cloud View - The cloud view gives details about AWS cloud resources and applications. 

## Prerequisites

Before you begin to configure, make sure you have the following prerequisites:

- Have the Database Layer 

- UI Layer

- API Layer

- If you are configuring Hygieia with Docker, the Docker Instances are up and running for all components of Hygieia

To continue setting up the Dashboard, refer 'Dashboard Configuration'.

## User Authentication

Hygieia dashboards provide the following options for user authentication:

- LDAP allows you to use your LDAP server to authenticate users.
- Standard authentication uses an internal database of users and passwords. If you choose to create an internal database, the user names and passwords will not be in sync with the LDAP server.
- Single Sign On (SSO) 

To reconfigure the user authentication type for the dashbaord, see the [API Properties]() file.

## Admin User Creation and Privilages

Hygieia dashboards provide administrator and user access through various views. The admin user can create and configure:  

- Creating and setting up custom dashboard templates
- Set up tokens for authentication
- 
- 





