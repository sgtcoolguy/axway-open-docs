{"title":"API Builder Tools 3.0.0 Release Note","weight":"40"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## API Builder Tools 3.0.0 - 8 December 2017

API Builder Tools 3.0.0 is a major release that includes several new features, improvements, service connectors, additional changes, fixed issues, and a few known issues.

As of this release, API Builder Tools 2.x will not be supported one calendar year from 3.0.0's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## New features and improvements

* API Builder Tools 3.0.0 (Included in CLI 7.0.0) continues to improve the API workflow for creating, importing, and building better Data APIs and API-First APIs, faster. Specifically, the following new capabilities and features have been added:

  * **API-First APIs** – Create RESTful APIs using the API-First pattern by importing a Swagger 2.0 specification via the API Builder Console. Now, API Builder allows low or no code API creation workflows for Data APIs and API-First APIs.

  * **API Orchestrations** – Create API graphical flows using the using the API Orchestration flow editor interface to drag, drop, configure, and save flows. For API Builder 3.0, the flow editor flow-node library includes support for model flow-nodes, service connector, and utility flow-nodes (custom, code block, compose, condition, delay, HTTP, JSON, and set context). The API Builder flow editor and runtime support parallel execution paths that can result in simpler flow definitions with lower latencies.

  * **API Mocking** – Optionally, create mock implementations of APIs during the Swagger import workflow. This will enable API developers to publish a working version of the APIs for API consumers while they continue to work on the actual implementation.

  * **[Axway Flow SDK](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Flows/Axway_Flow_SDK/)** – Create custom flow-nodes for the flow editor using the standalone Axway Flow SDK utility. By offering the Axway Flow SDK as a standalone utility, new flow-nodes can be developed and consumed in the API Builder Console without upgrading to a new release of API Builder Tools. In addition, the Axway Marketplace will progressively offer new flow-nodes for specific needs.


## Service connectors

* As part of the API Builder Tools 3.0.0 release, 20 new API Builder Service Connectors are offered to consumers via the [Axway Marketplace](https://marketplace.axway.com/home). The service connectors provide access to popular SaaS-based cloud services in areas such as marketing, customer relationship management (CRM), storage, and social media. The service connectors are loaded and made available to the API Builder flow editor and can be used to implement the API business logic alongside model and other utility flow-nodes. For API Builder Tools 3.0.0, the offered service connectors are: Amazon S3™, Concur™, Eloqua™, Facebook™, HubSpot™, HubSpot CRM™, Google Drive™, MailChimp™, Marketo™, Microsoft Dynamics CRM™, MS Office OneDrive™, MS SharePoint™, NetSuite CRM™, Pardot™, Salesforce Service Cloud™, ServiceNow™, SugarCRM™, Twitter™, Zendesk™, and Zoho™.


## Additional changes

* API Builder Tools 3.0.0 includes the following additional changes:

  * The minimum required Node.js version is 8.0.0. See the release notes for Appc CLI 7.0.0 [here](/docs/appc/Appcelerator_CLI/Appcelerator_CLI_Release_Notes/Appcelerator_CLI_Release_Notes_7.x/Appcelerator_CLI_Release_Notes_7.0.x/Appcelerator_CLI_7.0.0.GA_Release_Note/).

  * The legacy API Builder UI (pre-2.x) has been removed. Now, users must use the API Builder Console.

  * The documentation generator has been removed. Now, it is recommended that /apidoc/swagger.json be used for API Documentation.

  * Flows created for the original flow engine introduced in API Builder Tools 2.0.0 will no longer work and must be re-created or upgraded.

  * The /apidoc/docs.json API Documentation is deprecated and is replaced by the /apidoc/swagger.json API Documentation. The deprecated /apidoc/docs.json API Documentation will be removed in the next major release.


## Fixed issues

* Previously, users were unable to build APIs when running API Builder in a Microsoft Windows environment where the user home path was not on the default drive. Users would receive a "You are not logged in. Please log in again," error message when they attempted to builds APIs. Now, users are able to build APIs without receiving the login error message.

* Previously, users were unable to pack or unpack large files when attempting to publish applications. Additionally, tar.gz 1.0.5 packaged with Node.js 6 has known security vulnerabilities. Now, the vulnerable tag.gz module has been replaced and users can pack and unpack large files when publishing applications.


## Known issues

* The legacy Distinct() APIs have inconsistent or non-compliant return types.

* Clicking on joined models in the Source column on the Models tab of the API Builder Console does not work. The details of the joined model should be displayed.

* If a Swagger definition uses the allOf parameter, the body generated in the method test window is incorrect.

* Filtering the API Builder Console administrator access using IPv6 addresses may cause ENOTFOUND errors.

* When attempting to create and save a flow for an imported Swagger endpoint that contains a path or paths defined by references such as GET /find, a Page Not Found (404) error will be displayed in the API Builder Console and the flow cannot be saved. For example, a Swagger document with a path reference may look similar to this:

  `{`

  `"swagger"``:` `"2.0"``,`

  `"paths"` `{`

  `"x-path"``: {`

  `"get"``: {}`

  `},`

  `"/find"``: {`

  `"$ref"``:` `"#/paths/x-path"`

  `}`

  `}`

  `}`

  Currently, Swagger documents with path references can be imported and the imported endpoint will be correctly displayed in API Lists, but a flow cannot be created and saved successfully. When the flow editor **Save** button is clicked, a Page Not Found error is displayed. The error occurs because the API Builder Console cannot find the method as it is not in an expected location.

* When rendering the flow editor, the API Builder Console may fail to render the Scalable Vector Graphics (SVG) icons correctly in the Firefox browser. The render failure may result in blank icons being displayed in the tool panel and in the flow diagram. This is due to a long-standing bug in Firefox that fails to scale SVG graphics correctly. To fix, edit the SVG icon and add height and width. For example:

  `<svg ... height=``"80"` `width=``"80"` `/>`

* The API Builder Console does not recognize a required consumes value for form parameters if it is appended and the endpoint load will fail. For example:

  `"consumes"``: [`

  `"multipart/form-data; charset=utf-8"`

  `],`

  The appended character set (charset=utf-8) will cause the endpoint load to fail.

* When deleting endpoints which contain references within paths, a Page Not Found (404) error may be displayed in the API Builder Console. For example, a Swagger document with references within paths may look similar to this:

  `{`

  `"swagger"``:` `"2.0"``,`

  `"paths"` `{`

  `"x-path"``: {`

  `"get"``: {}`

  `},`

  `"/find"``: {`

  `"$ref"``:` `"#/paths/x-path"`

  `},`

  `"/search"``: {`

  `"$ref"``:` `"#/paths/x-path"`

  `}`

  `}`

  `}`

  The API Builder Console will fail to find GET /find since it is inside a $ref. If the API Builder Console has modified the referenced $ref, it could cause unexpected behavior for other paths referencing #/paths/x-path such as /search - deleting GET /find could unexpectedly delete GET /search too.

* Endpoints named with special characters cannot be viewed in the API Builder Console. For example, if you attempt to view the \[test\].json endpoint, you will receive a Page Not Found error message.

* Editing large object parameters on the API Orchestration page in the API Builder Console may cause multiple, confusing flow-node configuration panel scrollbars to appear.

* When editing flows in the console log in the terminal, multiple lines with an unknown format are ignored and the following message is received: unknown format "multiline" ignored in the schema at path "#"

* Currently, you cannot develop generated flow-node handlers inside your application. Any node\_modules inside your nodehandler-foo folder will be loaded as flow-node modules and will crash the application.

* Currently, you need to use a code block flow-node handler or use a combination of the compose flow-node handler and the condition flow-node handler to evaluate JAVA script and switch on the value.
