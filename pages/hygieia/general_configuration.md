---
title: General Configuration and Concepts
tags:
keywords:
summary: General Concepts about Hygieia Installation
sidebar: hygieia_sidebar
permalink: general_configuration.html
---

Before you begin to install Hygieia, make sure to configure the corporate proxy applicable to your organization (HTTP_PROXY, HTTPS_PROXY, or using Cntlm).

If you do not already have Hygieia installed, you can download or clone Hygieia from the [GitHub repo](https://github.com/capitalone/Hygieia). For information on cloning a repository, see [GitHub Documentation](https://help.github.com/articles/cloning-a-repository/).
 
## Build Hygieia

Hygieia uses Spring Boot to package the components as an executable JAR file with dependencies. To build the project, use maven build. To run maven after installing it, configure the settings.xml file. For details see, ‘Proxy Authentication’.

To package all components of Hygieia's source code into executable JAR files, run the maven build. Before you build Hygieia using Maven, make sure to configure the `settings.xml` file. For more details, see [Proxy Authentication](proxyauthentication.md). 

To configure Hygieia, execute the following steps:

*	**Step 1: Run Maven Build**

	In the command line/terminal, run the following command from the `\Hygieia` directory of your source code installation:
	 
	```bash
	mvn clean install package
	```

	This will build all the following components:

	~~~
	└── Hygieia
		├── UI
		├── API
		└── Collectors
			├─ Feature
			│    ├── JIRA
			│    └── VersionOne
			└─ Repos
			'     ├── GitHub
			'     ├── Gitlab
			'     ├── Subversion 
			'     └── Bitbucket
			'
			'
			and so on. 		   
	~~~

	The output `.jar` file is generated in the `\target` folder for each component of Hygieia, including the Collectors.

*	**Step 2: Set Parameters in the Properties File**
	
	Set the configurable parameters in the `.properties` file to connect to each component of Hygieia. For more information about the server configuration, see the Spring Boot [documentation](http://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/#boot-features-external-config-application-property-files).

*	**Step 3: Run Each Component**

	To run the executable file for API module, change directory to 'api\target' and then execute the following command from the command prompt:

	```bash
	java -jar api.jar --spring.config.location=C:\[path to]\Hygieia\api\dashboard.properties -Djasypt.encryptor.password=hygieiasecret
	```
	
	To run the UI module, in the command prompt, navigate to `\Hygieia\UI`, and then execute the following command:

	```bash
	gulp serve
	```
	
	The dashboard will serve up on port 3000.
	
	In general, all the collectors can be run using the following command:
	
	```bash
	java -jar <Path to collector-name.jar> --spring.config.name=<prefix for properties> --spring.config.location=<path to properties file location>
	```
	
	The detailed instructions for installing each component of Hygieia is described in section, 'Configuration Procedure' in the Installation Guide.
	
## General Concepts

### Encrypted Properties

Properties that are recommended not to be stored in plain text can be encrypted/decrypted using jasypt. Encrypted properties are enclosed in keyword ENC(), that is, ENC(thisisanencryptedproperty).
To generate an encrypted property, run the following command:
java -cp ~/.m2/repository/org/jasypt/jasypt/1.9.2/jasypt-1.9.2.jar  org.jasypt.intf.cli.JasyptPBEStringEncryptionCLI input="dbpassword" password=hygieiasecret algorithm=PBEWithMD5AndDES
where,	
dbpassword - Property value being encrypted, and 
hygieiasecret - the secret.
When you run the API, this secret has to be passed as a system property using -Djasypt.encryptor.password=hygieiasecret in order to decrypt the property.
When using docker, pass the environment variable docker run -t -p 8080:8080 -v ./logs:/hygieia/logs -e "SPRING_DATA_MONGODB_HOST=127.0.0.1" -e "JASYPT_ENCRYPTOR_PASSWORD=hygieiasecret" -i hygieia-api:latest.
For additional information, see jasypt spring boot documentation.
Tip: When using GitLab CI Runner, specify the value for JASYPT_ENCRYPTOR_PASSWORD as a secure variable. To add secure variables to a Gitlab project, navigate to Project Settings > Variables > Add Variable.
By default, a secure variable’s value is not visible in the build log and can only be configured by a project administrator.

### Encryption for Private Repos

1.	From module core generate a secret key.
java -jar <path-to-jar>/core-2.0.5-SNAPSHOT.jar com.capitalone.dashboard.util.Encryption
Add this generated key to api.properties
api.properties
key=<your-generated-key>
2.	Add the same key to your repo settings file. This is needed for the target collector to decrypt your saved repo password. For example, if your repo is github add the following.
github.properties
github.key=<your-generated-key>

