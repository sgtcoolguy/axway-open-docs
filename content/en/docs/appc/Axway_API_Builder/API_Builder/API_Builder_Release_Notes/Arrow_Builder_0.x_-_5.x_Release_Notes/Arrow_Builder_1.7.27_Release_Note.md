{"title":"Arrow Builder 1.7.27 Release Note","weight":"30"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## Arrow Builder 1.7.27 - 22 February 2016

Arrow Builder 1.7.27 is a patch release that includes one new feature and several improvements and bug fixes.

## New Feature

You can add models before the server starts and have them stand up their route properly.

## Improvements

* The last screen of the Build (model) replaces the Next button with a Save button that saves your project.

* The field type of complexity has been added to the acceptable field types for the Salesforce Connector.

* Port 80 is now the default port in client SDKs.


## Fixed Issues

* Fixed issue with logging out and running an Arrow project that throws the error message of "Uncaught Exception Unexpected token u"

* Arrow apps no longer exit with non-zero code upon error

* Updated the link in the local admin "appc.arrowdb/photo" page to point to the correct documentation

* Fixed issue where reduced ArrowDB model/API doesn't return any data

* Fixed issue with installing appc.mongo with Node 4.2.1 (error message: "Cannot find module '../build/Release/bson")

* You can now connect multiple Salesforce instances

* If you install Appc CLI Core on Windows, the install does not break on the buffer utils

* Exposed APPC\_AUTO\_RESTART and APPC\_AUTO\_RESTART\_COUNT

* Creating empty connector projects no longer fails with "logger.trace is not a function"

* Fixed bug with the Data Editor page will not display any data for a published Arrow app

* Fixed issue on preprod where you can pass "undefined" as the API key when making an API call to a published app. The curl call will no longer succeed and you need to pass in your production API key instead.

* Fixed bug when you use Arrow SDK with Alloy and receive the runtime error of "Can't find variable: CacheElseNetwork"
