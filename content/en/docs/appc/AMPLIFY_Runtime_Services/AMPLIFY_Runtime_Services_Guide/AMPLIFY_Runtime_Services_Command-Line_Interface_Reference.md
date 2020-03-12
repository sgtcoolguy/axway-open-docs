{"title":"AMPLIFY Runtime Services Command-Line Interface Reference","weight":"10"}

* [Introduction](#Introduction)

* [Setup](#Setup)

* [acs commands](#acscommands)

  * [accesslog](#accesslog)

  * [config](#config)

  * [crt](#crt)

  * [domain](#domain)

  * [download](#download)

  * [inspect](#inspect)

  * [list](#list)

  * [logcat](#logcat)

  * [login](#login)

  * [loglist](#loglist)

  * [logout](#logout)

  * [new](#new)

  * [ps](#ps)

  * [publish](#publish)

  * [remove](#remove)

  * [restart](#restart)

  * [restore](#restore)

  * [server](#server)

  * [transfer-domain](#transfer-domain)

  * [unpublish](#unpublish)

  * [usage](#usage)

  * [whoami](#whoami)

* [acs-stack commands](#acs-stackcommands)

  * [crt](#crt.1)

  * [deploy](#deploy)

  * [inspect](#inspect.1)

  * [log](#log)

  * [logcat](#logcat.1)

  * [ls](#ls)

  * [ps](#ps.1)

  * [rm](#rm)

  * [rollback](#rollback)

  * [scale](#scale)

  * [services](#services)

  * [update](#update)


## Introduction

AMPLIFY Runtime Services (API Runtime Services) uses the Appcelerator Cloud Services command-line interface, called acs for short, for creating and administering applications in the AMPLIFY Runtime Services environment. By default, the Appcelerator CLI or Studio handles the installation of the acs CLI tool.

## Setup

The Appcelerator CLI or Studio manages the installation of the acs CLI. To run acs subcommands, use the appc cloud subcommand.

To manually install the acs CLI, independent of the other tools:

1. Download and install Node.js from [http://nodejs.org/#download](http://nodejs.org/#download), which includes the npm package manager needed to install the acs CLI.

2. From a console window, run the following command to install the CLI:

3. Login to AMPLIFY Runtime Services.

  `[sudo] npm install acs -g`

  `acs login  `


Most commands require you to be logged in. If you do not run commands in the project's directory, in most commands, you need to either specify the app name as the last parameter or specify the project's location with the \-d parameter.

## acs commands

### accesslog

List application's access logs within a specified period. By default, a maximum of 100 log messages will be returned at a time.

`accesslog [options] [appname]`

Name

Description

appname

The name of the application to retrieve and for which to show access logs. If omitted, you must run the command in the application's root directory, or specify the application's directory with the \-d option.

\--server\_id <serverid>

The ID of the server from which the logs are retrieved. An application may be deployed to multiple servers in the cloud.

\--show\_serverid \[appname\]

Show server ID in logs.

\--start\_date <start\_date>

Starting date for retrieving logs.

\--end\_date <end\_date>

Ending date for retrieving logs.

\--per\_page <per\_page>

The number of log messages per page. Default: 100

\--more \[appname\]

Display the next page of log messages.

\--full\_content \[appname\]

Show full access logs.

\--org <orgID>

The ID of the organization to which application belongs. This parameter only is required if the target application has the same name as an application in another organization to which you belong.

\-h, \--help

Show help information for this command.

Dates are specified as YYYY-MM-DD or "YYYY-MM-DD HH:MM". Note that if the time is included, the date string must be quoted. If the specified date range contains more than the specified maximum number of logs, the most recent messages will be returned.

### config

The config command configures environment variables and the number of cloud servers for the application to use (auto-scaling).

`### Environment variables`

`acs config [--set <key>=<value>] [--unset <key>] [--env] [appname]`

`### Auto-scaling`

`acs config [--autoscaleup` `true``|``false``] [--autoscaledown` `true``|``false``] [--minsize N] [--maxsize N] [--maxqueuedrequests N] [--usagenotice` `true``|``false``] [appname]`

Name

Description

appname

The name of the app for which to configure cloud server resources. If omitted, the command needs to be run in the application's root directory, or specify the application's directory with the \-d or \--directory option.

\--org <orgid>

The ID of the organization to which the application belongs. This parameter only is required if the target application has the same name as an application in another organization to which you belong.

\--autoscaleup <true|false>

Boolean (default is false). Enables or disables automatically scaling up the number of cloud servers based on the maxqueuedrequests setting.

\--autoscaledown <true|false>

Boolean (default is false). Enables or disables automatically scaling down the number of cloud servers based on the maxqueuedrequests setting.

\--maxqueuedrequests <var>

Specifies the maximum number of queued requests for autoscaling to occur. The number should be based on the response time of your application; the longer the response time is, the smaller this value should be. AMPLIFY Runtime Services will increase the number of containers if the queue is too high for at least one minute. The default value is 50.

\--maxsize <n>

Sets the maximum number of cloud servers to use.

\--minsize <n>

Sets the minimum number of cloud servers to use.

\--maxconn <n>

Set the maximum per-server number of concurrent connections for the app.

\--maxconnws <n>

Set the maximum per-server number of concurrent web socket connections for the app.

\--autoshutdown <n>

Automatically deactivate non-development container after n seconds (value needs to be higher than 3600 or set to 0). If the value is not set or set to 0, the app will not deactivate if its type isn't development. Regardless, development containers will still be deactivated after seven days of inactivity.

\--set <var>

Sets an environment variable.

To set more than one variable, use comma-separated key-value pairs. For example:

`acs config --set` `"extra_hosts=54.219.6.230 www.163.com;54.219.6.230 www.123.com"`

To access the variable in the application, prefix the variable with the process.env namespace.

\--unset <var>

Unsets the specified environment variable.

\--env \[appname\]

Lists set environment variables.

\-h, \--help

Displays help information about the command.

### crt

Manages custom SSL certificates for accessing your application via HTTPS.

`acs crt [options] [appname]`

Name

Description

appname

The name of the app to associate with the SSL certificate. If omitted, the command needs to be run from the application's root directory, or specify the application's directory with the \-d option.

\--add <cert>

Add a certificate for the app. The certificate should be a PEM file containing a signed certificate, intermediate certificates, and a private key (passphrase eliminated).

\--remove \[appname\]

Removes the SSL certificate of the associated application, if one exists.

\--org <orgid>

The ID of the organization the application belongs to. This parameter only is required if the target application has the same name as an application in another organization you belong to.

\-h, \--help

Displays help information about the command.

### domain

Binds a domain to a published application, so that the application can be accessed using a custom domain as an alias for the application's cloud.appcelerator.com URL.

`acs domain [ options ] [ appname ]`

Name

Description

appname

The name of the app for which to set the domain. If omitted, the command needs to be run in the application's root directory, or specify the application's directory with the \-d option.

\--set <domain>

Set domain binding for the application to the specified domain name. A domain record must exist for the specified domain name, pointing to the alias for the application's cloud.appcelerator.com URL. Do not specify the protocol, that is, do not add \`http://\` or \`https://\`, when setting this parameter. You may bind up to five domain names to the application.

\--remove \[domain\]

Remove domain binding from the application. If the application has more than one domain, you will be prompted to select the domain to remove, or you can optionally specify the domain to remove.

\--org <orgid>

The ID of the organization to which the application belongs. This parameter only is required if the target application has the same name as an application in another organization you belong to.

\--path <path>

Specifies a URL path for routing. Use this parameter when setting more than one application to the same domain name. Set the domain first.

\--check

Check the current domain setting.

\-h, \--help

Displays help information about the command.

### download

Download the app source file with a specified app name and version. If no app name is provided, specify the app directory with either dir or \-d. The currently deployed app version will be downloaded if no app version option provided.

`acs download [options] [appname]`

Name

Description

appname

The name of the app to download. If omitted, the command needs to be run in the application's root directory, or specify the application's directory with the \-d option.

\--ver <version>

The app version to download. If not specified, the currently deployed version will be downloaded.

\--path <local\_path>

The existing local path to which to store the app source file.

\--org <orgid>

The ID of the organization the application belongs to. This parameter only is required if the target application has the same name as an application in another organization you belong to.

\-h, \--help

Displays help information about the command.

### inspect

Use the inspect command to gather detailed information for published services.

`acs inspect [options] [appname|ID]`

Name

Description

appname

The name of the published app for which to gather detailed information.

ID

The ID of the published app for which to gather detailed information.

\-o, \--org <orgid>

The ID of the organization the application belongs to. This parameter only is required if the target application has the same name as an application in another organization you belong to.

\-h, --help

Displays help information about the command.

### list

Shows a list of applications owned by the current user. By default, data is listed for all applications. You can specify an application name to only show details for that application. The information returned by this command also includes error messages, if any, related to the application's deployment and execution.

`acs list [options] [appname]`

Name

Description

appname

Name of the app for which to list information.

\--mine

Only list apps created by the current user.

\--org <orgID>

Lists applications of the specified organization ID.

\--show\_all

Show all servers in the result if there are more than ten servers; otherwise, only servers whose status is not deployed will be shown.

\-h, --help

Show help information for this command.

### logcat

Retrieves and displays a published application's runtime logs continuously from AMPLIFY Runtime Services. It lets you see in real-time what's happening with an application running in the cloud. By default, runtime logs are retrieved every five seconds, and you can configure this interval with the \--interval parameter. The interval cannot be smaller than five seconds.

`acs logcat [ options ] [ appname ]`

Name

Description

appname

Name of the app for which to log information.

\--interval <interval>

Interval for retrieving application logs, in seconds. Default: 5s.

\--build\_log

Displays the application's retrieved log. It does not work with the \--server\_id or \--show\_serverid options.

\--show\_serverid \[appname\]

Show server ID in logs.

\--server\_id <server\_id>

The ID of the server to retrieve logs from. An application may be deployed to multiple servers in the cloud.

\--org <orgid>

The ID of the organization the application belongs to. This parameter is required if the target application has the same name as an application in another organization you belong to.

\-h, \--help

Show help information for this command.

### login

Command for logging in to AMPLIFY Runtime Services using your AMPLIFY Appcelerator Services account credentials.

`acs login [options] [username],[password]`

Name

Description

username

Your AMPLIFY Appcelerator Services account username. If not specified, you are prompted for the username.

password

Your AMPLIFY Appcelerator Services account password. If not specified, you are prompted for the password.

\--host <hostname>

The ACS host to which to log in. If not specified, the command attempts to log in to the host specified by the ~/.acs configuration file, or admin.cloudapp.appcelerator.com if not specified by the ~/.acs file.

\--login\_registry

Login to the private Docker registry.

\-h, \--help

Show help information for this command.

### loglist

Lists the application's log messages within a specific period. By default, a maximum of 100 log messages is returned at a time.

`acs loglist [options] [appname]`

Name

Description

appname

The name of the app for which to retrieve and show runtime logs. If omitted, you must run the command in the application's root directory, or specify the application's directory with the \-d option.

\--server\_id <serverid>

The ID of the server to retrieve logs from. An application may be deployed to multiple servers in the cloud.

\--build\_log

Displays the application build log. It does not work with the \--server\_id or \--show\_serverid options.

\--show\_serverid \[appname\]

Show server ID in logs.

\--start\_date <start\_date>

Starting date for retrieving logs.

\--end\_date <end\_date>

Ending date for retrieving logs.

\--per\_page <per\_page>

Number of log messages per page. Default: 100.

\--more \[appname\]

Display the next page of log messages.

\--org <orgid>

The ID of the organization the application belongs to. This parameter only is required if the target application has the same name as an application in another organization you belong to.

\-h, --help

Show help information for this command.

Dates are specified as YYYY-MM-DD or "YYYY-MM-DD HH:MM". Note that if the time is included, the date string must be quoted. If the specified date range contains more than the specified maximum number of logs, the most recent messages will be returned.

### logout

Logout from AMPLIFY Runtime Services.

`acs logout`

Name

Description

\-h, --help

Show help information for this command.

### new

Starting with AMPLIFY Runtime Services (Arrow Cloud) 1.6.0, acs new creates a new app, and acs new --image creates a new app with a Dockerfile.

`acs` `new` `[options] <name>`

Name

Description

name

Name of the app to create.

\--type <type>

Create a new app of the specified type. Available options are free and image.

\--force

Force to use existing local app directory (add an existing project to the cloud).

\--org <orgid>

Create an app for the specified organization.

\--env <envid>

Create an app for the specified environment.

\-h, --help

Show help information for this command.

### ps

Lists the service tasks for the specified app.

`acs ps [options] <appname>`

Name

Description

appname

The name of the app for which to list service tasks.

\--org <orgid>

The ID of the organization to which the application belongs. This parameter only is required if the target application has the same name as an application in another organization you belong to

\-h, --help

Show help information for this command.

### publish

Publishes and runs an application on the AMPLIFY Runtime Services. This command also lists all currently published versions and the currently deployed version.

Note that if an application is not listening on port 80, use acs config --set PORT=customport to publish work. Also, note that publishing an application now supports publishing Docker images directly.

`acs publish [options] [npm_username],[npm_password],[appname]`

Name

Description

appname

The name of the app to publish. If omitted, you must run the command in the application's root directory, or specify the application's directory with the \-d option.

npm\_username
npm\_password

NPM repository credentials if you are using dependencies from a private NPM repository.

\--force \[appname\]

Required when publishing a version of an application that's already been published.

\--list\_versions \[appname\]

List all published versions of the application and the version deployed currently, if any.

\--set\_active\_version <version>

Set the currently deployed and active version of the application to version.

\--org <orgid>

The ID of the organization the application belongs to. You only need to use this parameter if you have published an application with the same name to multiple organizations.

\--async

Publish an app without waiting for fully deployed onto the cloud.

\--image <name\[:tag\]>

The name of the docker image will use the latesttag if a tag is not specified. Only the image type needs to specify this option.

\--app\_version <version>

The version of the app to be published. Only the image type needs to specify this option.

\--delete\_oldest

Delete the oldest version if published versions reached the max number of versions (10).

\-h, \--help

Show help information for this command.

For a newly installed on-premise cluster, if the Domain Name System (DNS) is not configured for the Mobile Backend Services endpoint, use acs config --set "extra\_hosts=<ip> api.<domain> <appname>" before or after publish for your app to reference to the Mobile Backend Services endpoint that is not in the database. This applies to all endpoints that don't exist in the DNS yet and extra\_hosts can take a list of entries, such as

acs config --set "extra\_hosts=54.219.6.230 www.163.com;54.219.6.230 www.123.com" <appname>

For appc publish, you can include it in appc.json:

"environment": {"extra\_hosts":"54.212.208.81 api.cloudapp-1.appctest.com"},

### remove

Removes an application. If the application has been published, the command unpublishes the application first, then removes it. The local application directory is not deleted by default. Use the \--force option to delete it.

`acs remove [options] [appname]`

Name

Description

appname

The name of the app to remove. If omitted, you must run the command in the application's root directory, or specify the application's directory with the \-d option.

\--force

Remove the local application directory. The application must be specified using -d option, which specifies the target application directory or the command is running in the application's root directory.

\--org <orgid>

The ID of the organization the application belongs to. This parameter is required if the target application has the same name as an application in another organization you belong to.

\-h, \--help

Show help information for this command.

### restart

Released with Appcelerator CLI 6.0.0, this command allows you to restart an AMPLIFY Runtime Services application without having to use acs publish --force.

This command will restart all servers associated with your app.

`acs restart [options] [appname]`

Name

Description

appname

The name of the app to restart. If omitted, you must run the command in the application's root directory, or specify the application's directory with the \-d option.

\--org <orgid>

Organization ID of the app if there are multiple apps with the same name in different organizations.

\-h --help

Show help information for this command.

### restore

Restores the specified app.

`restore [options] [appkey]`

Name

Description

appkey

The key to the app to restore.

\-h, --help

Show help information for this command.

### server

The server command configures the server container size of the application. If your application is already published after changing the container size, you will need to republish the application.

`acs server [options] [appname]`

Name

Description

appname

The name of the app for which to configure cloud server resources. If omitted, the command needs to be run in the application's root directory, or specify the application's directory with the \-d or \--directory option.

\--set <size>

Sets the server size. Values can be one of the following: \`Dev\`, \`Small\`, \`Medium\`, \`Large\`, or \`XLarge\`. See [API Builder Project](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/) for specifics on these sizes.

The minimum recommended container size for Arrow Apps is "Medium". Though you may be able to deploy to a "Dev" or "Small" container for better memory usage and performance, it is highly recommended that you use medium or bigger size containers.

\--org <orgid>

The ID of the organization the application belongs to. This parameter only is required if the target application has the same name as an application in another organization you belong to.

\-h, \--help

Show help information for this command.

### transfer-domain

Transfer a domain name from an app to another.

`acs transfer-domain [options] <domain_name>`

Name

Description

domain\_name

The name of the domain to transfer from one app to another app.

\--from <source app>

The app that currently owns the domain name.

\--to <target app>

The app to receive the domain name.

\-h, \--help

Show help information for this command.

### unpublish

By default, unpublishes the currently deployed and active application, shutting the application down and deleting it from the AMPLIFY Runtime Services cloud. You can also unpublish a specific version with the \--ver option, regardless of whether it is deployed or not. The local application directory is not removed after an unpublish operation, so you can republish the application again with the publish command.

`acs unpublish [options] [appname]`

Name

Description

appname

Name of the app to be unpublished. If omitted, the command needs to be run in the application's root directory, or the application's directory must be specified with the \-d or \--dir option.

\--ver <version>

Un-publishes the version of the application specified by _version_. If not specified, the currently deployed version is unpublished.

\--org <orgid>

The ID of the organization to which the application belongs. This parameter is required if the target application has the same name as an application in another organization to which you belong.

\-h, \--help

Show help information for this command.

### usage

Check server system resource usage within a specific period. The server in cloud logs CPU/memory usage periodically. By default, a maximum of 100 log entries will be returned at a time.

`acs usage [options] [appname]`

Name

Description

appname

The name of the app to retrieve and show system resource usage. If omitted, the command needs to be run in the application's root directory, or specify the application's directory with the \-d option.

\--server\_id <serverid>

The id of the server from which the logs are retrieved. An app may be deployed to multiple servers in the cloud.

\--show\_serverid \[appname\]

Show server ID in logs.

\--start\_date <start\_date>

Starting date for retrieving usage logs.

\--end\_date <end\_date>

Ending date for retrieving usage logs.

\--per\_page <per\_page>

The number of usage logs per page. Default: 100

\--more \[appname\]

Display the next page of log messages.

\-\-org <orgid>

The ID of the organization to which the application belongs. This parameter is required if the target application has the same name as an application in another organization to which you belong.

\-h, --help

Show help information for this command.

### whoami

Shows the currently logged-in user and organizations to which you belong.

`acs whoami [options]`

Name

Description

\--output <value>

Sets the output format. Set to either **report** for human-readable format or **json** for JSON output. Defaults to **report**.

\-h, \--help

Show help information for this command.

## acs-stack commands

### crt

Upload or remove a certificate.

`acs-stack crt [options] <add-or-rm>,[certificateFile]`

Name

Description

certificateFile

The name of the certificate file to add or remove.

add

Add the specified certificate file.

rm

Remove the specified certificate file.

\-c, --cert <cert>

Specify the certificate.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, \--help

Show help information for this command.

### deploy

Deploy a new stack.

`acs-stack deploy [options] <stack-name>`

Name

Description

stack-name

Name of the stack to deploy.

\-c, --compose <compose-file>

Specify the compose file for the stack.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### inspect

Inspect a service.

`acs-stack inspect [options] <stack-name>,[service-name|ID]`

Name

Description

stack-name

Specify the name of the stack to inspect.

service-name

Specify the name of the service to inspect.

ID

Specify the ID of the service to inspect.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### log

Get logs for a stack service.

`acs-stack log [options] <stack-name>,<service-name>`

Name

Description

stack-name

Specify the name of the stack from which to get logs.

service-name

Specify the name of the service from which to get logs.

\--server <server-id>

Specify service ID for checking service logs.

\--start <start-time>

Specify the start time for checking service logs.

\--end <end-time>

Specify the end time for checking service logs.

\--more

Get more service logs.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### logcat

Get continuous logs for a stack service.

`acs-stack logcat [options] <stack-name>,<service-name>`

Name

Description

stack-name

Specify the name of the stack from which to get continuous logs.

service-name

Specify the name of the service from which to get continuous logs.

\--server <server-id>

Specify the service ID for checking service logs.

\--interval <interval>

Specify a longer interval in seconds for periodically checking service logs. Min: 5

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### ls

List stacks.

`acs-stack ls [options] [stack-name]`

Name

Description

stack-name

Specify the name of the stack for which to list stacks.

\-m, --mine

Show stacks only created by the user.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### ps

Check service tasks.

`acs-stack ps [options] <stack-name>,[service-name|ID]`

Name

Description

stack-name

Specify the name of the stack for which to check service tasks.

service-name

Specify the name of the service for which to check service tasks.

ID

Specify the ID of the service to for which check service tasks.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### rm

Remove a stack.

`acs-stack rm [options] <stack-name>`

Name

Description

stack-name

Specify the name of the stack to remove.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### rollback

Rollback a service.

`acs-stack rollback [options] <stack-name>,<service-name>`

Name

Description

stack-name

Specify the name of the stack in which to roll back a service.

service-name

Specify the name of the service to rollback.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### scale

Scale a service.

`acs-stack scale [options] <stack-name>,<service-name>,<relicas>`

Name

Description

stack-name

Specify the name of the stack in which to scale a service.

service-name

Specify the name of the service to scale.

relicas

Specify the name of the relics to rollback.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### services

Check the services of a stack.

`acs-stack services [options] <stack-name>`

Name

Description

stack-name

Specify the name of the stack in which to check services.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.

### update

Update a service.

`acs-stack update [options] <stack-name>,<service-name>`

Name

Description

stack-name

Specify the name of the stack in which to update a service.

service-name

Specify the name of the service to update.

\--envadd <name>=<val>

Add an environment variable.

\--envrm <name>

Remove an environment variable.

\--image <image-tag>

Specify a service image tag.

\--force

Force an update even if no changes require it.

\-o, --org <orgid>

Specify the organization for the involved stack.

\-h, --help

Show help information for this command.
