{"title":"Add a Connector","weight":"30"}

{{% alert title="❗️ API Builder 3.x is deprecated" color="danger" %}}Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

* [Introduction](#introduction)

* [Search for connectors](#search-for-connectors)

* [Service connectors](#service-connectors)

    * [Install a service connector](#install-a-service-connector)

    * [Configure a service connector](#configure-a-service-connector)

* [Model-first connectors](#model-first-connectors)

    * [Install a model-first connector](#install-a-model-first-connector)

    * [Configure the model-first connector](#configure-the-model-first-connector)

        * [Disable API endpoints](#disable-api-endpoints)

    * [Use the model-first connector](#use-the-model-first-connector)

    * [Remove a model-first connector](#remove-a-model-first-connector)

## Introduction

Connectors give your applications the ability to access external data from different sources, such as from a database or in the cloud. To add a Connector:

1. Install the Connector.

2. Configure the Connector.

3. Use the Connector.

## Search for connectors

To see an available list of Connectors, go to the [Axway Marketplace](https://marketplace.axway.com/home) and select Connector in the Categories list. To see a list of the available API Builder connectors, select API Builder in the API Management list.

The following API Builder model-first connectors are offered on the [Axway Marketplace](https://marketplace.axway.com/home): ArrowDB, Box.com, CompositeJS, Elastic Search, Google Custom Search, HL7 FHIR Swagger Docs, LokiJS, Microsoft Azure, Microsoft SQL Server, MongoDB, MySQL, OData, Oracle Database, Redis, Salesforce, SOAP, Swagger, and Twilio.

Beginning with API Builder 3.0.0 (Included in CLI 7.0.0), the following new API Builder service connectors are offered on the [Axway Marketplace](https://marketplace.axway.com/home): Amazon S3™, Concur™, Eloqua™, Facebook™, Google Drive™, Hubspot CRM™, Hubspot™, Mailchimp™, Marketo™, Microsoft Dynamics™, Netsuite™, OneDrive™, Pardot™, Salesforce Service Cloud™, Service Now™, SharePoint Native™, SugarCRM™, Twitter™, Zendesk™, and Zoho™.

## Service connectors

The following sections describe how to install and configure the new service connectors offered with API Builder 3.0.0 (Included in CLI 7.0.0).

### Install a service connector

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

5. Open the API Orchestration flow editor in the API Builder Console and verify that the service connector is listed and is available for use in flows.

### Configure a service connector

A service connector configuration file is not mandatory since all the options for invoking the service connector functions invocation are provided in the API Orchestration user interface. However, if you need to configure the service connector to set common parameters, you must copy the config file from \*\*connector/config/connector\_name.default.js and place it in the app/conf directory.

## Model-first connectors

The following sections describe how to install, configure, use, and remove the model-first connectors.

### Install a model-first connector

To install a model-first connector, execute the appc install connector/<CONNECTOR\_NAME> command from the project's directory. The command downloads and installs the connector in the node\_modules/connector directory, updates the appc.json file, and creates a connector configuration file in the project's conf directory.

```bash
$ appc install connector/appc.mysql
Appcelerator Command-Line Interface, version 0.2.230
Copyright (c) 2014-2015, Appcelerator, Inc.  All Rights Reserved.

Installing dependencies... <APIBuilderProject>
Checking for 1 module: connector/appc.mysql
Fetching connector/appc.mysql@1.0.43
Installed 1 module
connector/appc.mysql provided a default configuration example which was written to conf/appc.mysql.default.js
You must update the config file located in ./<APIBuilderProject>/conf/appc.mysql.default.js before you can use it!
Installed:  connector/appc.mysql
```

### Configure the model-first connector

Depending on the connector you installed, you may need to modify the configuration settings of the connector. Open the project's conf/<CONNECTOR\_NAME>.js file to modify its settings. Some connectors have multiple files for different deployment environments, such as the appc.arrowdb connector. For example, the MySQL connector's configuration file contains keys for you to define the database host URL, port number, admin user, admin password, and database name as well as additional database access settings.

**conf/appc.mysql.default.js**

```javascript
module.exports = {
    connectors: {
        'appc.mysql': {
            connectionPooling: true,
            connectionLimit: 10,
            database: 'test',
            user: 'root',
            password: '',
            host: 'localhost',
            port: 3306,
            generateModelsFromSchema: true,
            modelAutogen: true
        }
    }
};
```

#### Disable API endpoints

By default, when you install a connector, it will add its API endpoints to the application, for example, api/myconnector/model. If you do not want to generate these API endpoints, set the modelAutogen key to false in the connector's configuration file in the project.

**conf/myconnector.default.js**

```javascript
module.exports = {
    connectors: {
        'connector.name': {
            setting1: 'foo',
            setting2: 'bar',
            setting3: 'baz',
            modelAutogen: false
        }
    }
};
```

### Use the model-first connector

To use the connector, simply assign the connector key in a Model file to the name of the connector. For example, the model file below is using the employee table (or model) accessed by the MySQL connector.

**models/employee.js**

```javascript
var Arrow = require('arrow');

var employee = Arrow.Model.reduce('appc.mysql/employee','employee',{
    fields: {
        first_name: {type: String, description: 'Give name'}
        last_name: {type: String, description: 'Family name'}
    },
    connector: 'appc.mysql'
});

module.exports = employee;
```

### Remove a model-first connector

To remove a connector from your project, you need to manually update the appc.json file and remove some files.

1. Open the appc.json file and delete the connector you want to remove from the dependencies object. For example, if you want to remove the MySQL connector, remove the "connector/appc.mysql": "^1.0.34". Note that you will need to remove the trailing comma at the end of the arrowdb line.

    ```
    {
      "type": "api",
      "group": "arrow",
      "dependencies": {
        "connector/appc.arrowdb": "^1.0.52",
        "connector/appc.mysql": "^1.0.34"
      }
    }
    ```

2. Delete the connector's configuration file(s) from the project conf directory. The file(s) will contain the name of the connector.

3. Delete the connector's directory in the node\_modules/connectors/ directory. The directory will contain the name of the connector.
