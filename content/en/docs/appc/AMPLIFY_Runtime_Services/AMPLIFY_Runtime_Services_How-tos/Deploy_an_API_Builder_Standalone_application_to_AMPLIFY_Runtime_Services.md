{"title":"Deploy an API Builder Standalone application to AMPLIFY Runtime Services","weight":"20"}

* [Introduction](#introduction)

* [Prerequisites](#prerequisites)

    * [AMPLIFY Platform account](#amplify-platform-account)

    * [Docker](#docker)

    * [API Builder CLI](#api-builder-cli)

    * [AMPLIFY Cloud Services (ACS) CLI](#amplify-cloud-services-acs-cli)

* [Create your application](#create-your-application)

* [Create your Platform application](#create-your-platform-application)

* [Build a Docker image](#build-a-docker-image)

* [Publish image to Platform](#publish-image-to-platform)

* [Check publish status](#check-publish-status)

* [Try your application](#try-your-application)

## Introduction

This topic describes how to create, Dockerize, and publish an API Builder Standalone application to the AMPLIFY Runtime Services cloud. Prerequisites, instructions, and references are provided to help you successfully deploy and publish your application to the AMPLIFY Runtime Services cloud and to test your published application.

## Prerequisites

### AMPLIFY Platform account

You need to have an account on [https://platform.axway.com](https://platform.axway.com).

### Docker

The installation of Docker is via a dedicated installer for your specific operating system. For additional Docker installation information, refer to the [Docker documentation](https://docs.docker.com/install/).

### API Builder CLI

The API Builder CLI is a node module published in the [npm public repository](https://www.npmjs.com/package/@axway/api-builder). To install, execute the following command:

*Install API Builder CLI*

```bash
$ npm install -g @axway/api-builder
```

For additional API Builder CLI installation information, refer to the [API Builder Getting Started Guide](https://wiki.appcelerator.org/display/AB4/API+Builder+Getting+Started+Guide).

### AMPLIFY Cloud Services (ACS) CLI

The AMPLIFY Cloud Services CLI (ACS) is a node module published in the [npm public repository](https://www.npmjs.com/package/@axway/api-builder). To install, execute the following command:

*Install ACS*

```bash
$ npm install -g acs
```

For additional AMPLIFY Cloud Services CLI information, refer to the [AMPLIFY Runtime Services Command-Line Interface Reference](/docs/appc/AMPLIFY_Runtime_Services/AMPLIFY_Runtime_Services_Guide/AMPLIFY_Runtime_Services_Command-Line_Interface_Reference/).

## Create your application

API Builder CLI usage can be found [here](https://www.npmjs.com/package/@axway/api-builder). The setup found in the [API Builder Getting Started Guide](https://wiki.appcelerator.org/display/AB4/API+Builder+Getting+Started+Guide) will create a "myproject" sub-directory.

*Create an API Builder project*

```
$ api-builder init myproject
```

## Create your Platform application

Log in to the AMPLIFY Platform using your [https://platform.axway.com](https://platform.axway.com/) username and password. Create a project in the cloud with the same name as your "myproject" sub-directory. Then, configure your project to use PORT 8080. The project should be configured to use PORT 8080 because the container is built with PORT 8080 by default.

*Create an API Builder project*

```
$ acs login
$ acs new myproject --force
$ acs config --set PORT=8080 myproject
```

{{% alert title="⚠️ Warning" color="primary" %}}*Important*

You may already have an existing project, "myproject". If you do, and you know that it is not being used and you wish to delete it, or if you want to delete this example project on ARS, you can execute: **acs remove myproject**.{{% /alert %}}

## Build a Docker image

To build a Docker image of your project, execute the following commands.

*Build Docker image*

```
$ cd ./myproject
$ docker build --tag demo-image ./
```

## Publish image to Platform

To publish the Docker image of your project to the Platform, execute the following command.

*Publish image*

```
$ acs publish myproject --delete_oldest --force --image demo-image --app_version 0.1
```

{{% alert title="⚠️ Warning" color="primary" %}}*Important*

It can take up to 10 minutes for your project to be deployed and your service to be accessible. You should [check the publish status](#checkpublishstatus) before trying to access your service in the cloud.{{% /alert %}}

Once the image is written, note the URL, as you will use it to test your API, for example:

*URL*

```
App will be available at https://<guid>.cloudapp-enterprise.appcelerator.com
```

## Check publish status

Even though your image was sent to ARS, it can take up to 10 minutes to start (for example Status: Deploying). You should check the Status of your project before trying to access your service that is running in the cloud. The service will not be available until status shows Status: Active.

```
$ acs list myproject
```

You can also check the log of your project to see if it started properly.

```
$ acs logcat myproject
```

## Try your application

To try your application in the cloud, you will require your API key, which can be found in "myproject/conf/default.js". On successful publication of your project, you also received a URL with a GUID prefix to access your application from the Internet. Replace the <key> and <guid> with the API key and GUID values in the following command.

```
$ curl -u "<key>:" https://<guid>.cloudapp-enterprise.appcelerator.com/api/greet?username=Bob
```
