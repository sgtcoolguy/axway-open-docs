{"title":"API Runtime Services 1.6.0 - 13 April 2017","weight":"70"}

This release of Arrow Cloud includes version 2.0.4 of the CLI and 1.6.0 of the server and includes behavior changes, new features and improvements, and several bug fixes.

## Behavior changes

* Updated Node.js to version 6.10.2 and npm to 4.4.4 in default publish case (unless you choose to publish via a Docker image)

* Added support to store persistent data on the filesystem

## New features and improvements

* Added support to publish an app from Dockerfile or image

* Added product\_type to user\_input.json so that the user has an option to indicate which product to utilize

    * Valid options are arrowdb, arrowcloud, or all

        * arrowdb: deploy ArrowDB and common services

        * arrowcloud: deploy Arrow Cloud and common services

        * all: deploy both Arrow Cloud and ArrowDB services

* Depreciated MVC app support as of this release. Please use a free app as the default app for acs new.

## Bug fixes

* Fixed issue with arrowcluster-vpc deploy failing to create AWS resources due to unsynced system time

* Depreciated –git support
