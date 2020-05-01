{"title":"Arrow Builder 5.3.1 Release Note","weight":"10"}

{{% alert title="❗️ API Builder 3.x is deprecated" color="danger" %}}Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

## Arrow Builder 5.3.1 - 6 July 2016

Arrow Builder 5.3.1 is a patch release that includes several bug fixes.

As of this release, the previous Arrow Builder Tools patch release is no longer supported. Note: Major and minor releases continue to be supported according to their nominal lifetime. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#nominal-lifetimes) documents for details.

## Fixed Issues

* API-1222 - If you edit an existing Arrow model, the model's fields will not appear in the Build UI

* API-1272 - Trying to display/read Swagger.json throws an Internal Server Error

* API-1280 - Swagger.json is exposing invalid schema.required array for path parameters

* API-1300 - Invalid parameters in PUT method for the new model in swagger file
