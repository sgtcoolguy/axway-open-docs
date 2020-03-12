{"title":"Console Configuration","weight":"20"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Introduction](#Introduction)

  * [Example](#Example)

* [Settings](#Settings)

  * [admin](#admin)

  * [apikey\_development](#apikey_development)

  * [apikey\_production](#apikey_production)

  * [APIKeyAuthPlugin](#APIKeyAuthPlugin)

  * [APIKeyAuthType](#APIKeyAuthType)

  * [apiPrefix](#apiPrefix)

  * [bodyParser](#bodyParser)

  * [busboy](#busboy)

  * [connectors](#connectors)

  * [cors](#cors)

  * [defaultConnector](#defaultConnector)

  * [ignoreDuplicateModels](#ignoreDuplicateModels)

  * [logging](#logging)

  * [logLevel](#logLevel)

  * [port](#port)

  * [ssl](#ssl)


## Introduction

API Builder uses the configuration files in the project's conf directory to initialize the application and its connectors. Each JavaScript file in the directory should expose an object of key-value pairs. You may add any arbitrary key-value pair beside the one described below. The values will be passed to any method that is passed the API Builder configuration object.

API key values and session object are auto-generated when you create a new project.

For environment-specific configuration files, add either .development or .production to the end of the filename. For example, foo.development.js will be used for the development environment, while foo.production.js will be used for the production environment.

If multiple files set the same keys, the value from the last file loaded will be used unless it is an environment-specific file. Files are loaded based on the order returned from the operating system's readdir() method. For example, if Foo.js and foo.development.js set the same key, the value in Foo.js is used since it is not environment specific. However, if Foo.development.js and foo.development.js set the same key, the value from foo.development.js is used since it is loaded last.

You can override the configuration file settings with an environment variable. For the setting, you want to override, prefix the variable with ARROW\_. For example, if you want to override the apikey setting, set the ARROW\_APIKEY environment variable.

### Example

./conf/foo.js

`module.exports = {`

`// These are generated when you create a new project`

`apikey_production:` `'xxxxxxxxxxxxxxxxxxxxxxxxx'``,`

`apikey_development:` `'yyyyyyyyyyyyyyyyyyyyyyyyy'``,`

`// Selects the authorization type -- uses HTTP Basic Authorization by default`

`APIKeyAuthType:` `'basic'``,`

`// All API paths will be prefixed with '/foo'`

`apiPrefix:` `'/foo'``,`

`// Sets body-parser middleware setting`

`bodyParser: {`

`limit: 1 * 1024 * 1024`

`},`

`// Sets busboy initialization settings`

`busboy: {`

`limit: {`

`fieldNameSize: 100,`

`fieldSize: 1 * 1024 * 1024`

`}`

`},`

`// Connector settings...`

`connectors: {`

`connector_name: {`

`collection:` `'foobar'`

`},`

`another_connector: {`

`name:` `'foobaz'`

`}`

`},`

`// et cetera`

`}`

## Settings

### admin

Configures the Admin Console. The admin object may contain the following key-value pairs:

Key

Type

Default

Description

allowedHosts

Array<String>

\-

When the application is in production, restrict access to the Admin Console to the specified hosts

disableAPIDoc

Boolean

false

Set to true to not display the generated API Docs. Changing the setting only works in production. Swagger is always available in dev mode.

enabled

Boolean

true

Set to true to enable the Admin Console.

validEmails

Array<String>

developer's e-mail address

When the application is in production, restrict access to the Admin Console to the specified accounts.

validOrgs

Array<Number>

developer's organization

When the application is in production, restrict access to the Admin Console to the specified organizations.

### apikey\_development

Generated API key used when testing the application; that is, running the application locally.

### apikey\_production

Generated API key used when running the application in production; that is when it is deployed to AMPLIFY Runtime Services.

### APIKeyAuthPlugin

Location of the authorization module if APIKeyAuthType is set to plugin.

For details, see [Authentication Schemes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Configuration/Authentication_Schemes/).

### APIKeyAuthType

String value indicating the authorization type for the application. By default, it is set to basic.

For details, see [Authentication Schemes](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Configuration/Authentication_Schemes/).

### apiPrefix

Prefix path to use for the API requests for Models and APIs. Each endpoint you define in a Model or API will be prefixed by this value. By default, it is set to /api.

### bodyParser

Configures body-parser middleware settings. The bodyParser object may contain the following key-value pairs:

Key

Type

Default

Description

limit

Number/String

1mb

Sets the maximum request body size in bytes for the body parser middleware.

### busboy

Configuration object to pass to the busboy constructor, which is created when the API Builder middleware is initialized. For properties, you can set, see the [busboy documentation](https://www.npmjs.com/package/busboy#busboy-methods).

### connectors

Configures the connectors used by the application. The connectors field is an object of key-value pairs where the key is the name of the connector and the value is another key-value pair object used to configure the connector. The configuration object is specific to each connector.

Most connectors will have their own default configuration file in the conf directory.

### cors

Configures the CORS settings. The cors object may contain the following key-value pairs:

Key

Type

Description

Access-Control-Allow-Origin

String

Specifies the URI that can access the server. Defaults to none.

safeHeaders

Array<String>

HTTP headers to expose and allow, that is, the specified value is set for Access-Control-Expose-Headers and Access-Control-Allow-Headers.

### defaultConnector

Specify the name of the default connector. Used if a Model does not specify one.

### ignoreDuplicateModels

Set to true to ignore duplicate Model definitions. Defaults to false, which will throw an error if a model definition is duplicated.

### logging

Configures the logger utility. The logging object may contain the following key-value pairs:

Key

Type

Default

Description

logdir

String

./logs

Location of the transaction logs if enabled

transactionLogEnabled

Boolean

true

Set to true to enable transaction logs

### logLevel

Sets the log level for the logger utility. Accepted values are debug, error, fatal, info, trace, or warn.

### port

Sets the port number for the server if the PORT environment variable is not set. By default, the port is set to 8080.

### ssl

Configures SSL settings for the server. The ssl object may contain the following key-value pairs:

Key

Type

Default

Description

port

Number

8443

SSL port number
