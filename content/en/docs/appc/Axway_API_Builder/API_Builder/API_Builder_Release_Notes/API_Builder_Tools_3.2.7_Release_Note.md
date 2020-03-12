{"title":"API Builder Tools 3.2.7 Release Note","weight":"10"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## API Builder Tools 3.2.7 - 1 February 2019

API Builder Tools 3.2.7 is a patch release that includes bug fixes and known issues.

As of this release, API Builder Tools 3.1.x will not be supported six months (2019-07-01) from 3.2.7's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## Fixed issues

* Previously, CORS requests were not working correctly on APIs that are bound on paths with parameters. Now, CORS is behaving correctly for these cases.

* Previously, if CORS was enabled in the application, the static files were not served with the correct headers. Now, the appropriate headers are attached.


## Known issues

* The legacy Distinct() APIs have inconsistent or non-compliant return types.

* Clicking on joined models in the Source column on the **Models** tab of the API Builder Console does not work. The details of the joined model should be displayed.

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

  `"consumes"``: [` `"multipart/form-data; charset=utf-8"` `],`

  The appended character set (charset=utf-8) will cause the endpoint load to fail.

* When deleting endpoints which contain references within paths, a Page Not Found (404) error may be displayed in the API Builder Console. For example, a Swagger document with references within paths may look similar to this:

  `{` `"swagger"``:` `"2.0"``,` `"paths"` `{` `"x-path"``: {` `"get"``: {} },` `"/find"``: {` `"$ref"``:` `"#/paths/x-path"` `},` `"/search"``: {` `"$ref"``:` `"#/paths/x-path"` `} } }`

  The API Builder Console will fail to find GET /find since it is inside a $ref. If the API Builder Console has modified the referenced $ref, it could cause unexpected behavior for other paths referencing #/paths/x-path such as /search - deleting GET /find could unexpectedly delete GET /search too.

* Endpoints named with special characters cannot be viewed in the API Builder Console. For example, if you attempt to view the \[test\].json endpoint, you will receive a Page Not Found error message.

* Editing large object parameters on the API Orchestration page in the API Builder Console may cause multiple, confusing node configuration panel scrollbars to appear.

* The inline object editor **Expand** button obscures text.

* When editing flows in the console log in the terminal, multiple lines with an unknown format are ignored and the following message is received: unknown format "multiline" ignored in the schema at path "#"

* In the flow editor, if a flow-node method description is too long, it may not be visible in its entirety.

* Editing large object parameters on the _API Orchestration_ page in the API Builder Console may cause multiple, confusing flow-node configuration panel scrollbars to appear.

* The following packages have a dependency on the [doT](https://www.npmjs.com/package/dot) npm module, which is vulnerable to command injection (see advisory [#798](https://www.npmjs.com/advisories/798)): [@axway/api-builder-plugin-fn-dot](https://www.npmjs.com/package/@axway/api-builder-plugin-fn-dot), [@axway/api-builder-plugin-fn-base64](https://www.npmjs.com/package/@axway/api-builder-plugin-fn-base64), [@axway/api-builder-plugin-fn-restclient](https://www.npmjs.com/package/@axway/api-builder-plugin-fn-restclient), [@axway/api-builder-plugin-fn-swagger](https://www.npmjs.com/package/@axway/@axway/api-builder-plugin-fn-swagger), and [axway-flow-sdk](https://www.npmjs.com/package/axway-flow-sdk).


## Security vulnerability

* bootstrap 20184

  * **Vulnerability**: API Builder UI uses react-bootstrap which as a dependency on bootstrap@3.3.7, and it is 3.3.7 that contains the vulnerability. At the time of writing this ticket, bootstrap did not publish a 3.x version after 3.3.7, so no fix was ever released. The bootstrap library is now at 4.x. However, the react-bootstrap library that API Builder uses is actively working on a version compatible with bootstrap v4.x. The following issue is logged against bootstrap@3.3.7:

    * [20184](https://github.com/twbs/bootstrap/issues/20184) \- XSS in data-target attribute

  * **Analysis**: The vulnerability and risk are documented [20184](https://github.com/twbs/bootstrap/issues/20184) . The API Builder UI only runs on the developer machine and is locked to localhost by default. The API Builder UI **will not be installed in production**. Furthermore, the UI bundled with API Builder does not use data-target attributes. The risk to API Builder is low.
