{"title":"API Builder Tools 3.1.0 Release Note","weight":"30"}

{{% alert title="❗️ API Builder 3.x is deprecated" color="danger" %}}Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

## API Builder Tools 3.1.0 - 22 February 2018

API Builder Tools 3.1.0 is a minor release that includes new features, improvements, and bug fixes.

As of this release, API Builder Tools 3.0.x will not be supported six months from 3.1.0's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#nominal-lifetimes) documents for details.

## New features

* Added the ability to validate generated flows using the Axway Flow SDK

* Implemented selector auto-complete when creating and editing flows in the API Builder UI

## Improvements

* Previously, the initial project created by the appc new command contained unnecessary dependencies. Now, the initial project created by the appc new command has been updated to remove unnecessary dependencies and to provide extra examples on how to test endpoints and models. Additionally, the grunt command is no longer used for the build. The npm test command is used instead. Also, the example.md web route has been removed.

* Previously, when editing flows, it was not possible to see previously used and available selectors. Now, when editing a selector any previously used selector, or any available selector is displayed in a context-assisted drop-down menu that shows the selector or selectors that match the input text.

* Previously, the axway-flow-sdk would generate projects that required transpiling with babel before they could be used. Now, the generated projects do not require transpiling; so the babel dependency has been removed, but the generated projects require a Node.js version equal to or greater than 8.9.x instead.

* Previously, the API SDK generator was used to generate software development kits based on integrated SDK templates. Now, the API Builder SDK generator has been deprecated and the API Builder application exposes its APIs definitions using a standard Swagger format. These API definitions can be consumed by third-party SDK generators to create clients.

* Previously, the API SDK generator was used to generate software development kits based on integrated SDK templates. Now, the API Builder SDK generator has been deprecated and the API Builder application exposes its APIs definitions using a standard Swagger format. These API definitions can be consumed by third-party SDK generators to create clients.

## Fixed issues

* Previously, attempting to develop flow-nodes locally in the ./nodes directory would cause API Builder to also attempt to read the node\_modules folder and cause the application to crash. Now, locally developed flow-node dependencies in the ./nodes/node\_modules folder will be ignored and any flow-node dependency that is required must be added and resolved via the API Builder application's package.json instead.

* Previously, API Builder would not handle JSON schema references on startup and could generate invalid Swagger definitions that were missing the global schema references. Now, API Builder will load and handle the JSON schema references as expected.

* Previously, the appc generate command would generate excessive logging. Now, the command has been reduced to avoid excessive logging. If required, the logging level can be increased with the appc generate -l debug option.
