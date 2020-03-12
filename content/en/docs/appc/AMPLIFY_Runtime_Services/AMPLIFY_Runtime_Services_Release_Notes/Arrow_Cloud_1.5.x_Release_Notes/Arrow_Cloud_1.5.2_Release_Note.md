{"title":"Arrow Cloud 1.5.2 - 28 July 2016","weight":"40"}

This release of Arrow Cloud includes version 1.5.2 of both the CLI and server as well as new features and improvements.

## New Features and Improvements

* Added a self-install tool for VPC and on-premise installation with upgrade support.

* Added proxy support to arrowdb-node-sdk. The proxy should be a string including a host, port, and user info as necessary.

* Added HTTP proxy support for apps within a Docker container. with the http\_proxy environment variable for apps behind an HTTP proxy firewall, connectors using the module request will not work.

* On-premise Arrow Cloud can now show current and required memory and base container status when the app's status is "Waiting for resource"
