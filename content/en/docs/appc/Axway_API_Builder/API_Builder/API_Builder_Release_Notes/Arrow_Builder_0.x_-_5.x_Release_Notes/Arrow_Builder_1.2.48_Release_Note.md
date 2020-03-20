{"title":"Arrow Builder 1.2.48 Release Note","weight":"60"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## Arrow Builder 1.2.48 - 09 September 2015

Arrow Builder 1.2.48 is a minor release that includes new features, improvements and bug fixes.

### New Features and Improvements

* Add the ability to customize the styling of the API Docs page. For details, see the ArrowWeb tab in the Admin console and [API Builder Developer Guide](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/).

* Hide overridden APIs in the API Docs page.

* Map missing methods, such as a cookie, vary, etc. to the common Express method in the response object.

* Implement a new LDAP plugin for Arrow client authentication. For details, see [Arrow Authentication Schemes: LDAP](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Configuration/Authentication_Schemes/#ldap).

* Improve support of loading and overriding configuration from the environment. Prefix environment variables with ARROW to override the value from the configuration file. For example, if you have apikey defined in the configuration file, you can override the value with the environment variable ARROW\_APIKEY.

* Add default health-check API endpoint arrowPing.json.

* Add the ability to hide APIs in the API Docs. To hide documentation, set the documented property to false for Connectors, Models, APIs or Blocks.

* Exposed the connectionTimeout property in the MSSQL connector.

* Add the ability to specify the models to generate from a connector. In the connector's configuration file, set the generateModels key to an array of model names you want to include.

* Exposed the schemaRefresh property in the SalesForce connector and added an If-Modified-Since check to update the schema only when needed.

* Print out application version in the Arrow console log during startup.

* New guided development flow for creating an Arrow Connector.

* Improved server start time by skipping appc install when possible.

### Fixed Issues

* API-580: Model Data View: Tabular data layout scrolls, but Table header doesn't follow it

* API-655: Generated API Docs source has to be manually deleted to be refreshed

* API-738: Marketplace formatting is not right

* API-750: actions: \['read'\] set on a model still creates a PUT API endpoint

* API-752: Multiple Instances of one connector overwrite generated models

* API-809: Setting model actions to read includes write API

* API-825: Unable to set 201 response with object location in custom API

* API-837: Blocks after{Action} and after are mutually exclusive

* API-861: Investigate if there is memory leak with the registry server

* API-896: In the Arrow admin page, modelAutogen is documented incorrectly

* API-905: Error using two different databases with alias

* API-910: ArrowDB: Session Collisions in Connector

* API-927: Process signal events for shutdown aren't correctly being handled

* API-928: Publishing with multiple servers with the same name doesn't properly pass the correct org

* API-931: Arrow: NO show() API for ACLs

* API-934: Creating a new model in the console does not reload properly so it cannot test the API without restarting the server

* API-949: Regression: API code examples are not laying out properly

* API-950: Regression: Performance Log Tab now showing all the data correctly

* API-954: Data Editor: Updating a field that is type Number results in a return type of String

* API-956: Memory leak detected related to handling HTTP requests

* API-960: Regression: performance log view is missing last server step

* API-963: In preproduction, cannot create an Arrow project

* API-966: Regression on import arrow app

* API-968: If you update a model while your Arrow app is running locally, then the local Arrow app will not restart itself

* API-971: After unpublish, if you try and republish, you get an error

* API-972: Regression: hitting /api/testapi from API Doc causes exception

* API-978: In production, cannot publish an Arrow app with 4.1.1 stack

* API-982: If you make any API requests, then no activity will appear in the Logs tab

* API-987: If you create a different connector alias in default.js, different errors are returned for 4.1.X stack and 5.0.0 stack
