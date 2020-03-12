{"title":"Arrow Cloud 1.1.11 - 21 April 2015","weight":"30"}

**New Features and Improvements**

* Add ability to publish a project from Github to Arrow Cloud. Use the appc cloud publish --git <options> command. For details, see the [CLI publish command](/docs/appc/AMPLIFY_Runtime_Services/AMPLIFY_Runtime_Services_Guide/AMPLIFY_Runtime_Services_Command-Line_Interface_Reference/).

* Add support for sticky sessions. If the application uses more than one server container, user sessions will be bound to the same application instance, allowing all requests to be sent to the same instance.

* Before republishing the application, Arrow Cloud sends the SIGTERM signal to the currently deployed application to let it shutdown gracefully. If the app does not shut down in time, Arrow Cloud will kill the application. Previously, Arrow Cloud would immediately kill the application before republishing.


**Bug Fixes**

* Fixed an issue where setting environment variables did not take effect when the previous publish command failed.

* Installed missing bzip2 dependency for Phantom support.
