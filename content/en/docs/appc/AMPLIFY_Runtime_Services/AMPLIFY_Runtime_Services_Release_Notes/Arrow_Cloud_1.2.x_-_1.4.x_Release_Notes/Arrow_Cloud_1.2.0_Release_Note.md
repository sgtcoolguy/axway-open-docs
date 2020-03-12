{"title":"Arrow Cloud 1.2.0 - 05 August 2015","weight":"50"}

This release of Arrow Cloud includes version 1.0.26 of the CLI and 1.2.0 of the server and includes behavior changes due to the transition from OpenVZ to Docker for container support.

To publish an application to Arrow Cloud 1.2.0, you must use at least version 4.1.2 of the Appcelerator CLI Core package Run appc use to check or change the core package version.

**Behavior Changes**

* The Node.ACS logger module is deprecated in favor of the appc-logger module. To continue collecting application and transaction log data, update your application to use the appc-logger module.

* Node version 0.8.x is no longer supported for Node.ACS MVC applications. Set the engines.node field in the package.json file to version 0.10.x or greater.


**New Features**

* **Node version**: specify any version of Node for the application to use in the package.json file. Previously, only versions 0.8.26 and 0.10.22 were supported.

* **Optional healthcheck**: define an optional healthCheck.json endpoint that Arrow Cloud can check to see if your application is running.

* **Port binding**: define the PORT environment variable to explicitly set the listening port of your application.

* **Provision the container**: install any third-party tool or package on your server container using the scripts.preinstall or scripts.postinstall fields in the package.json file.


**Known Issues**

* When setting the Node version, you can no longer specify a range. You must set the engines.node field to a specific version.
