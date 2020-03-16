{"title":"Arrow Cloud 1.3.1","weight":"30"}

This release of Arrow Cloud includes version 1.0.28 of the CLI and 1.3.1 of the server.

**New Features and Improvements**

* **List command**: The list command now displays two sublists for active deployments (current running applications) and pending deployments (applications in the process of being published or when the application is being scaled up or down to another server container). For pending deployments, an error will be displayed if there was an issue with deployment.

* **Make a request to a specific server container**: If your application is running on more than one server container, you can make a request to a specific server container by passing the \_serverid parameter with the request and set it to the ID of the server container. See [API Builder Project](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/).

* **Timestamps**: The usage command now displays timestamps in local time. Previously, the timestamp was in UTC.

**Bug Fixes**

* Fixed an issue where a project could not run locally if the main field in the package.json file points to a directory.
