{"title":"API Builder Getting Started Guide","weight":"10"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Introduction](#introduction)

* [Setup](#setup)

* [Create a project](#create-a-project)

* [Run the project](#run-the-project)

    * [Create a new model](#create-a-new-model)

    * [Access model data](#access-model-data)

    * [Add application data](#add-application-data)

    * [Test other API endpoints](#test-other-api-endpoints)

* [Deploy the project](#deploy-the-project)

* [View analytics](#view-analytics)

* [Next steps](#next-steps)

## Introduction

This guide walks you through the steps to install and run API Builder. API Builder allows you to build and deploy API endpoints to the cloud that can be consumed by a client application.

## Setup

To run API Builder, you need to install Node.js and Axway Appcelerator CLI. If you are using Axway Appcelerator Studio 4.0 or a later version, you already have Appcelerator CLI automatically installed and can go to step 4.

1. Download and install Node.js from [https://nodejs.org/en/#download](https://nodejs.org/en/#download). Note that API Builder has been tested with Node 8.x.

2. From a console window, execute the following command to install the CLI:

    ```bash
    npm install appcelerator -g
    ```

3. After installation, execute the setup command to install the required components:

    ```bash
    appc setup
    ```

    This installation and setup can take several minutes.

4. Once the Appcelerator CLI installation and setup is completed, you will be prompted to log in. Enter your email and password.

5. The CLI will send you an authorization token to your e-mail account (or a text to your mobile phone if provided during account activation). Enter the authorization token. If the authorization fails, a new code will be sent.

6. Once you are logged in, you will be queried whether or not you are developing Titanium applications. If you are developing Titanium applications, enter yes. Titanium will be automatically downloaded and installed.

## Create a project

To create a new project:

1. Navigate to your workspace directory and execute the following command:

    ```bash
    appc new
    ```

    Appcelerator CLI will prompt you to select a project type and project name.

2. Select **Arrow App (arrow)**.

3. Enter a name for your project. Once you enter a project name. Appcelerator will create a new API Builder project.

4. Navigate to the project directory. For example, projectname.

    ```
    cd projectname
    ```

## Run the project

To run the project locally:

1. From the project directory, execute the following command:

    ```bash
    appc run
    ```

    The CLI will download and install any dependencies for the project, then start the application. The application will launch a server that you can access from a browser or other clients. As the app is launching, you will see the various services it is starting and the localhost console URL for the application.

2. Open a browser and navigate to the Admin Console user interface (UI) of application. Typically, the URL of the Admin Console UI should be http://localhost:8080/console. Check the console output to verify the URL.

Upon reviewing the left navigation, you can navigate to the following items:

<table class="confluenceTable"><thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" "><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><img src="images/download/thumbnails/49153255/summary_%281%29.png" alt="images/download/thumbnails/49153255/summary_%281%29.png" class="confluence-embedded-image confluence-thumbnail" width="60"></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">Summary</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Your app's admin home page.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><img src="images/download/thumbnails/49153255/api.png" alt="images/download/thumbnails/49153255/api.png" class="confluence-embedded-image confluence-thumbnail" width="60"></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">API Doc &amp; Test</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Auto-generated documentation about your API endpoints. Provides help for the client application to access your application.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><img src="images/download/thumbnails/49153255/models.png" alt="images/download/thumbnails/49153255/models.png" class="confluence-embedded-image confluence-thumbnail" width="60"></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">Models</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Interface to help you build models. A model represents data stored from another source.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><img src="images/download/thumbnails/49153255/configuration.png" alt="images/download/thumbnails/49153255/configuration.png" class="confluence-embedded-image confluence-thumbnail" width="60"></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">Configurations</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Lists configuration files that you can modify and save within a browser.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><img src="images/download/thumbnails/49153255/connectors.png" alt="images/download/thumbnails/49153255/connectors.png" class="confluence-embedded-image confluence-thumbnail" width="60"></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">Connectors</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Lists and filters installed connectors.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><img src="images/download/thumbnails/49153255/button-logs.png" alt="images/download/thumbnails/49153255/button-logs.png" class="confluence-embedded-image confluence-thumbnail" width="60"></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">Logs</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Lists of access logs, clients trying to access your application.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><img src="images/download/thumbnails/49153255/View_Documentation.png" alt="images/download/thumbnails/49153255/View_Documentation.png" class="confluence-embedded-image confluence-thumbnail" width="60"></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">View Documentation</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Links to the Axway documentation site for API Builder's guide.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><img src="images/download/thumbnails/49153255/sidebar_toggle.png" alt="images/download/thumbnails/49153255/sidebar_toggle.png" class="confluence-embedded-image confluence-thumbnail" width="60"></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p><strong class=" ">Sidebar toggle</strong></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Toggles the width of the sidebar.</p></td></tr></tbody></table>

You can disable the Admin Console by changing the configuration settings in the conf/default.js file. For now, let's explore some of the features of the Admin Console.

### Create a new model

Let's create a new model using the Admin Console. In the Admin Console,

1. Click the **Models** tab.

2. Click the **\+ Model** button on the right side.

3. In the New Model step:

    ![new_model_%281%29](/Images/appc/download/attachments/49153255/new_model_%281%29.png)

    1. Enter "simpleuser" in the **Model name** field (required). The name must be unique for all of the application's models.

    2. Select a **Connector** from the drop-down list (required). Connectors are used to persist data to the model.

    3. Add a description.

    4. Click **Next** to move onto the fields step.

4. In the Create Model Fields step:

    ![add_fields](/Images/appc/download/attachments/49153255/add_fields.png)

    1. Click the **\+ Field** button.

    2. Enter "first\_name" in the Field name field (required).

        ![create_fields](/Images/appc/download/attachments/49153255/create_fields.png)
    3. Set Type to String.

    4. Leave Default value empty.

    5. Add a description.

    6. Check the boxes for Read-only or Required as necessary.

    7. Click the **Add field to model** button.

    8. Repeat step 4 as necessary to add the "last\_name" and "email" fields to this model. After you add the fields, you can configure them by changing properties or adding validation or return logic.

    9. Click **Next** to move onto the endpoint step.

5. In the API endpoint page:

    ![add_endpoints](/Images/appc/download/attachments/49153255/add_endpoints.png)

    1. Make sure the **Create**, **Retrieve**, and **Update** methods are checked. Since the Delete methods checkbox is not checked, the DELETE api/simpleuser and the DELETEALL api/simpleuser endpoints will not be generated but all the other default endpoints for this model will be.

    2. Click Save to commit your new model to the app.

If you look in your project's models folder, notice you have a new file called simpleuser.js. This file was just created by the Admin Console. Instead of creating a model using the Admin Console, you can define one using JavaScript files in the project's models directory.

### Access model data

Now that you have created the simpleuser model, let's try to retrieve the model data from the application. In the Admin Console:

1. Click the **API Docs & Test** tab. This page lists all the API endpoints that your application exposes. You can also add or import API endpoints via the **\+ API** button. For additional information, refer to [Manage Endpoints](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Endpoints/).

    ![API_Doc_n_Test](/Images/appc/download/attachments/49153255/API_Doc_n_Test.png)
2. Click anywhere on the row of any one of the API endpoints that you recently created. The Admin Console presents all the API endpoints that can be used to access a particular model. You can also export API endpoints via the **Download Swagger** button. For additional information, refer to [Manage Endpoints](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Manage_Endpoints/).

    ![APIs_list_simpleuser](/Images/appc/download/attachments/49153255/APIs_list_simpleuser.png)

    **Expand one of the GET methods** in your endpoint. The code example for the curl should be visible. If it's not, scroll down until the Examples section is visible and select **curl**.

    ![API_Doc_n_Test_curl](/Images/appc/download/attachments/49153255/API_Doc_n_Test_curl.png)

    **Copy a curl command** and **run it in a terminal**. Note the message returned by this command. Alternatively, you can test the select GET method in the user interface. Scroll until the Test API section is visible, if available complete the Request, Path parameters, and Query parameters fields, and then click **Execute**. Note the Result returned in the user interface.

3. Now let's take a look at the logs to see if the command registered with the app. Click the **Logs** tab. You should see all recent requests made to and from your applications here, including the recent requests to and from your "simpleuser" application.

4. If the list of events in the logs is rather long, you can filter and/or search for particular events. In the **Time** drop-down (by default, it says All Time because the log is reporting back all events), select **Past 10 Minutes**. If the list is still long, you can filter by and **Status** and **Method** as well. Once you found your curl call, click it to see the full report of that event.

    ![Log_event_report](/Images/appc/download/attachments/49153255/Log_event_report.png)

### Add application data

Now that you have tested the simpleuser model using one its GET methods, let's add some user data to the simpleuser model using its POST method.

1. **Expand the POST method** in your endpoint. The Test API should be visible. If it's not, scroll down until the Test API section is visible.

2. Enter the last name, first name, email address of a simple user.

    ![test_api_post_01](/Images/appc/download/attachments/49153255/test_api_post_01.png)
3. Click **Create** and view the Result. Verify that the simpleuser has been created.

    ![test_api_post_02](/Images/appc/download/attachments/49153255/test_api_post_02.png)
4. Repeat steps 2 and 3 to add additional simpleusers to your simpleuser model.

### Test other API endpoints

With a new project (by default), you can navigate to the app's API auto-generated documentation and it's example pages by pointing a browser to http://localhost:8080/apidoc and http://localhost:8080/example respectively.

The example URL shows a simple example of an API Builder Web interface. An API Builder Web interface creates an API endpoint with access to a render engine and your Model data that displays HTML content.

After locally testing the application, let's try it out in the cloud. To stop the server, hit **command**/**control** + **C** in the terminal where you launched the app.

## Deploy the project

To deploy the project to the cloud:

1. From the project directory, execute the following command:

    ```bash
    appc publish
    ```

    It will take a few minutes for your application to be deployed to AMPLIFY Runtime Services. After the command completes, the URL to your application will be displayed in the console.

    ```bash
    Appcelerator Command-Line Interface, version 5.5.1
    Copyright (c) 2014-2016, Appcelerator, Inc.  All Rights Reserved.

    Publishing application ... this could take several minutes
    Packaging application ...
    Deploying application ...
    Starting application ...
    Application deployed to https://<SUB_DOMAIN_TOKEN>.cloudapp-enterprise.appcelerator.com
    Published api/QuickStart2@1.0.0

    Tips:
     - Run `appc cloud logcat` to view logs.
     - Run `appc cloud loglist --build_log` to view the build log.
     - Run `appc cloud usage` for performance metrics.
    ```

    Let's quickly test the published application. In your browser, navigate to your published cloud application. You should see the API Builder Logo.

    You may have to edit your Admin Console configuration to access the application documentation in the /apidoc path. If you have problems accessing the application documentation, set the enableAdminInProduction setting in the /conf/default.js file to **true**. For additional information, refer to [API Builder Console](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Console/).

2. Next, go to the project's documentation. Add the /apidoc/swagger.json path to the end of the URL to retrieve the application documentation and endpoints. Retrieve the curl example of the query endpoint and execute it in the terminal. The command should return the same results when you tested the project locally.

## View analytics

To view analytics about your project, go to the [AMPLIFY Platform Dashboard](https://platform.axway.com/#/dashboard).

1. In a browser, navigate to [https://platform.axway.com/#/dashboard](https://platform.axway.com/#/dashboard).

2. Click the **Apps** menu and select **All Projects**. You will be presented with a list of all your applications.

3. Locate your new application. There will be two entry types for your application: **API Builder** and **Mobile Backend Services**. The application is the published application that you interact with. The **Mobile Backend Services** data source is essentially cloud storage where all your model data (at least for this example) is stored. The simpleuser model data you entered previously is stored here.

4. Click the type of your application. You will be presented with an analytics overview of your application with data about API calls and the server(s) your application is running on.

5. Select **Analytics** to view detailed analytics information about your application.

    ![analyticsover2](/Images/appc/download/attachments/49153255/analyticsover2.png)

## Next steps

Review the [API Builder Project](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/) page to learn more about API Builder projects, then review the other subtopics in the [API Builder](/docs/appc/Axway_API_Builder/API_Builder/) page to learn how to build the components for your project.
