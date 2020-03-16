{"title":"API Runtime Services 1.6.0.sp2 Release Note","weight":"40"}

## API Runtime Services 1.6.0.sp2 - 17 November 2017

This release of API Runtime Services (APIRS) includes version 2.0.7 of the CLI and 1.6.0.sp2 of the server and includes several improvements and fixed issues.

## Improvements

* Improved the host.ini configuration file and the findSwarmManager function in the swarm.util script to automate adding and managing new swarm manager nodes in a swarm.

* Upgraded to Docker 17.06 on all Ubuntu builds. **Note:** All UDP ports must be open for MongoDB access on Ubuntu.

## Fixed issues

* Resolved issue with the service health check, not including a StartPeriod configuration parameter. Now, the service health check includes a configurable StartPeriod parameter.

* Corrected issue with publishing Docker images of applications. Now, a Docker image of an application can be published before publishing the application.

* Corrected a CVE security vulnerability in the socket.io file. Appcelerator Cloud Services no longer uses the socket.io file, and it has been removed.
