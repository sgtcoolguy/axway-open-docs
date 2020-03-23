{"title":"Platform Marketplace","weight":"40"}

{{% alert title="❗️ Warning" color="danger" %}}*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

* [Overview](#overview)

    * [Marketplace access and search](#marketplace-access-and-search)

* [Install a service connector](#install-a-service-connector)

* [Install a model-first connector](#install-a-model-first-connector)

* [Searching for connectors](#searching-for-connectors)

    * [Search suggestions](#search-suggestions)

* [Pre-built connectors](#pre-built-connectors)

This document provides an overview of the [Axway Marketplace](https://marketplace.axway.com/).

## Overview

The [Axway Marketplace](https://marketplace.axway.com/) is a repository of building blocks for both Apps and APIs. Developers can discover and install components from the Marketplace.

### Marketplace access and search

You can access the [Axway Marketplace](https://marketplace.axway.com/) via your web browser. You can sign into the Axway Marketplace using your Platform account information. To sign in, click **Sign In** in the upper, right corner of the Axway Marketplace. If you do not have a Platform account, click **Get started for Free!**.

Currently, the Marketplace lists the following component types for API Builder:

* Connectors: Used for building APIs

To search through the connectors available on the Marketplace, select Connector in the Categories list. To search through the API Builder connectors, select API Builder in the API Management list.

The following API Builder model-first connectors are offered on the [Axway Marketplace](https://marketplace.axway.com/home): ArrowDB, Box.com, CompositeJS, Elastic Search, Google Custom Search, HL7 FHIR Swagger Docs, LokiJS, Microsoft Azure, Microsoft SQL Server, MongoDB, MySQL, OData, Oracle Database, Redis, Salesforce, SOAP, Swagger, and Twilio.

Beginning with API Builder V3.0.0 (Included in CLI 7.0.0), the following new API Builder service connectors are offered on the [Axway Marketplace](https://marketplace.axway.com/home): Amazon S3™, Concur™, Eloqua™, Facebook™, Google Drive™, Hubspot CRM™, Hubspot™, Mailchimp™, Marketo™, Microsoft Dynamics™, Netsuite™, OneDrive™, Pardot™, Salesforce Service Cloud™, Service Now™, SharePoint Native™, SugarCRM™, Twitter™, Zendesk™, and Zoho™.

## Install a service connector

To install a service connector:

1. Download the service connector from the [Axway Marketplace](https://marketplace.axway.com/).

2. Unzip the service connector into the /serviceconnectors/<connector name> folder in your project directory.

    {{% alert title="⚠️ Warning" color="primary" %}}The new service connectors are plain flow-node modules but they are not installed as such in API Builder V3.0.0. The zip file will contain the package folder that contains the actual connector. Rename the package folder after unzipping to match your connector name.{{% /alert %}}
3. From the project directory, execute the following command to install the HTTP communication module:

    ```bash
    npm i requester-ce
    ```

4. From the project directory, execute the following command:

    ```bash
    appc run
    ```

5. Open the API Orchestration flow editor in the API Builder Console and verify that the service connector is listed and is available for use in flow-node flows.

## Install a model-first connector

At the time of this publication, selecting an API Builder model-first connector from the [Axway Marketplace](https://marketplace.axway.com/) and clicking Download will redirect you to a third party site for the selected connector.

To download and install the selected connector, execute the provided Appcelerator CLI install command from within your API project. For example, the install command for the MongoDB Connector is: appc install connector/appc.mongo

The install command will place the connector in the connectors directory of your project.

## Searching for connectors

Searching for connectors can be accomplished by two different methods: searching using the [Axway Marketplace](https://marketplace.axway.com/) lists or searching using the Marketplace search function.

If you are unsure of the exact connector name, you can search the Marketplace search function.

### Search suggestions

If you know the component name starts with a certain string or character, try entering the first letters of the component name, for example, sales. This example will return a list of components in order of relevance. To narrow the list of components to those specific to API Builder, select API Builder in the API Management list.

## Pre-built connectors

To see a list of the pre-built connectors, please visit [https://marketplace.axway.com/](https://marketplace.axway.com/).
