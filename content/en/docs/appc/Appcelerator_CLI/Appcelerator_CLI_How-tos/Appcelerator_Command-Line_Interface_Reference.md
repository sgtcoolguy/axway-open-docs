{"title":"Appcelerator Command-Line Interface Reference","weight":"20"}

* [appc commands](#appccommands)

  * [Global options](#Globaloptions)

  * [Access](#Access)

  * [Access commands](#Accesscommands)

    * [access get](#accessget)

  * [access set](#accessset)

  * [Alloy](#Alloy)

    * [Alloy options](#Alloyoptions)

    * [alloy new](#alloynew)

    * [alloy compile](#alloycompile)

    * [alloy extract-i18n](#alloyextract-i18n)

    * [alloy generate](#alloygenerate)

    * [alloy copy](#alloycopy)

    * [alloy move](#alloymove)

    * [alloy remove](#alloyremove)

  * [Appc Daemon](#AppcDaemon)

    * [Daemon options](#Daemonoptions)

    * [appcd config](#appcdconfig)

    * [appcd dump](#appcddump)

    * [appcd exec](#appcdexec)

    * [appcd logcat](#appcdlogcat)

    * [appcd restart](#appcdrestart)

    * [appcd start](#appcdstart)

    * [appcd status](#appcdstatus)

    * [appcd stop](#appcdstop)

    * [appcd help](#appcdhelp)

  * [Cloud/ACS](#Cloud/ACS)

  * [Cloud/ACS commands](#Cloud/ACScommands)

    * [cloud/acs options](#cloud/acsoptions)

    * [cloud/acs new](#cloud/acsnew)

    * [cloud/acs domain](#cloud/acsdomain)

    * [cloud/acs list](#cloud/acslist)

    * [cloud/acs logcat](#cloud/acslogcat)

    * [cloud/acs loglist](#cloud/acsloglist)

    * [cloud/acs accesslog](#cloud/acsaccesslog)

    * [cloud/acs usage](#cloud/acsusage)

    * [cloud/acs crt](#cloud/acscrt)

    * [cloud/acs login](#cloud/acslogin)

    * [cloud/acs logout](#cloud/acslogout)

    * [cloud/acs publish](#cloud/acspublish)

    * [cloud/acs unpublish](#cloud/acsunpublish)

    * [cloud/acs remove](#cloud/acsremove)

    * [cloud/acs config](#cloud/acsconfig)

    * [cloud/acs whoami](#cloud/acswhoami)

    * [cloud/acs server](#cloud/acsserver)

    * [cloud/acs download](#cloud/acsdownload)

    * [cloud/acs transfer-domain](#cloud/acstransfer-domain)

    * [cloud/acs restart](#cloud/acsrestart)

  * [Config](#Config)

    * [Config examples](#Configexamples)

    * [config get](#configget)

    * [config list](#configlist)

    * [config set](#configset)

  * [Generate](#Generate)

    * [Generate options](#Generateoptions)

  * [Help](#Help)

  * [Info](#Info)

  * [Install](#Install)

    * [Install options](#Installoptions)

    * [Install examples](#Installexamples)

  * [Login](#Login)

    * [Login options](#Loginoptions)

  * [Logout](#Logout)

    * [Logout options](#Logoutoptions)

  * [New](#New)

    * [New options](#Newoptions)

    * [New examples](#Newexamples)

  * [Org](#Org)

  * [Org commands](#Orgcommands)

    * [org add](#orgadd)

    * [org list](#orglist)

    * [org rm | remove](#orgrm|remove)

  * [Org examples](#Orgexamples)

  * [Owner](#Owner)

  * [Owner commands](#Ownercommands)

    * [owner add](#owneradd)

    * [owner list](#ownerlist)

    * [owner rm | remove](#ownerrm|remove)

  * [Owner examples](#Ownerexamples)

  * [Platform](#Platform)

  * [Publish](#Publish)

    * [Publish options](#Publishoptions)

  * [Remove](#Remove)

    * [Remove options](#Removeoptions)

    * [Generic build options and flags](#Genericbuildoptionsandflags)

    * [Android build options](#Androidbuildoptions)

    * [iOS build options and flags](#iOSbuildoptionsandflags)

    * [Windows build options](#Windowsbuildoptions)

  * [Search](#Search)

    * [Search options](#Searchoptions)

  * [Setup](#Setup)

  * [Switch](#Switch)

  * [Titanium | ti](#Titanium|ti)

  * [Unpublish](#Unpublish)

    * [Unpublish options](#Unpublishoptions)

  * [Use](#Use)

    * [Use options](#Useoptions)

  * [User](#User)

    * [User examples](#Userexamples)

  * [User commands](#Usercommands)

    * [user add](#useradd)

    * [user rm | remove](#userrm|remove)

  * [Whoami](#Whoami)

    * [Whoami options](#Whoamioptions)


The Appcelerator Command-Line Interface (CLI) is a Node.js-based command-line tool for managing, building, and deploying Appcelerator projects, including Alloy, Titanium and Arrow projects. The Appcelerator CLI provides a unified mechanism for using the other CLI components.

This article provides in-depth information about the CLI commands and options. For information about some common tasks, see [Appcelerator CLI Tasks](/docs/appc/Appcelerator_CLI/Appcelerator_CLI_How-tos/Appcelerator_CLI_Tasks/).

## appc commands

If you don't specify all of the required options, appc prompts you for the missing options.

### Global options

Option

Description

\-h, --help

Output usage information

\--dashboard <dashboard>

Dashboard URL used for logins

\-l, --log-level <LOG\_LEVEL>

Sets the log output level. Specify either: trace, debug, info, warn or error.

\-o, --output <format>

Format output (only "json" is supported)

\-v, --version

Output the version of the CLI (if \-o "json" is used, the version of npm will also be output)

\-q, --quiet

Reduce the amount of text output to the console

\--no-banner

Disable banner

\--no-colors

Disable colors

\--no-services

Disable services

\--no-progress, --no-progress-bars

Disable progress bars

\--no-prompt

Disable prompt

\--prompt-port <promptPort>

Port to use socket-based prompting

\--prompt-type <PROMPT\_TYPE>

Prompt type. Specify either cli, socket or socket-bundle. Default is cli.

\--username <USERNAME>

Username for login

\--password <USER\_PASSWORD>

Password for login

\-e, --env <ENVIRONMENT>

Environment to run the command. Specify either production, preproduction or development.

\-O, --org-id <orgId>

Organization id for login

\-P, --plugin-paths <pluginPaths>

Comma-separated search paths for plugins

\-r, --registry <REGISTRY>

Registry server URL to use

\-s, --server <SECURITY\_SERVER>

Security server URL used for logins

\-v, --vpc-env <vpcEnv>

vpc environment for login

### Access

Manage a component's access rights.

### Access commands

#### access get

Retrieves the component's access rights.

`appc access get <MODULE_NAME> <options>`

Example to get a module's access rights: $ appc access get connector/com.foo@1.0.0

### access set

Sets the component's access rights.

`appc access` `set` `<MODULE_NAME> <ACCESS_RIGHTS> <options>`

Access rights can be either:

* public: everyone can see the component.

* private (default): only the publisher can see the component.

* org: Only certain organizations can see the component. Use the appc org command to add or remove organizations.

* user: Only certain users can see the component. Use the appc user command to add or remove users.

* user\_or\_org: Only certain users or organizations can see the component. Use the appc user or appc org command to add or remove users or organizations, respectively.


Example to set a module's access rights: $ appc access set connector/com.foo@1.0.0 private

### Alloy

Run an Alloy CLI command. See the [Alloy Command-Line Interface Reference](/docs/appc/Alloy_Framework/Alloy_How-tos/Alloy_Reference_Guides/Alloy_Command-Line_Interface_Reference/) for more information.

`appc alloy [``command``] [args] [options]`

#### Alloy options

\-h, --help

Output usage information

\--dashboard <dashboard>

Dashboard url to use for logins

\-l, --log-level <LOG\_LEVEL>

Sets the log output level. Specify either: trace, debug, info, warn or error.

\-o, --output <format>

Format output (only "json" is supported)

\-v, --version

Output the version of the cli (if -o "json", the version of npm will also be output)

\-a, --app <app>

Test app folder for running "alloy test"

\-A, --apply

Applies command changes \[extract-i18n\]

\-b, --noBanner

Disable the banner

\-c, --config <config>

Pass in compiler configuration

\-f, --force

Force the command to execute

\-l, --logLevel <logLevel>

Log level (default: 3 \[DEBUG\])

\-n, --no-colors

Turn off colors

\-o, --outputPath <outputPath>

Output path for generated code

\-p, --project-dir <project-dir>

Titanium project directory

\-q, --platform <platform>

Target mobile platform \[android,ios\]

\-s, --spec <spec>

Test spec to use with "alloy test"

\-w, --all

Require flag for generate styles

\-x, --column <column>

Column for source map query (default: 1)

\-y, --line <line>

Line for source map query (default: 1)

\-z, --source <source>

Source original file for source map query

\--widgetname <name>

Widget name, used with generate command

\--testapp <name>

Test app name to import, used with new command

#### alloy new

Create a new alloy project.

`appc alloy new [``dir``] [options]`

As of CLI 7.1.0, A custom template directory can be added via this commands:

`appc alloy` `new` `. </path/to/template>`

or

`appc` `new` `--template </path/to/template>`

#### alloy compile

Compile into titanium source code.

`appc alloy compile [``dir``] [options]`

#### alloy extract-i18n

Extracts i18n strings from the source code (js and tss files).

`appc alloy extract-i18n [language] [options]`

#### alloy generate

Generate a new alloy type such as a controller.

`appc alloy generate [``type``] [name] [options]`

#### alloy copy

Copy the controller, view, and style files from <source> to <destination>.

`appc alloy copy [``source``] [destination] [options]`

#### alloy move

Move the controller, view, and style files from <source> to <destination>.

`appc alloy copy [``source``] [destination] [options]`

#### alloy remove

Remove the controller, view, and style files at <source>.

`appc alloy copy [``source``] [options]`

### Appc Daemon

The Appcelerator Daemon is a server that hosts services which power the tooling for Axway products such as Titanium SDK.

`appc appcd COMMAND [ARGS] [OPTIONS]`

#### Daemon options

\-h, --help

Display help

\-v, --version

Outputs the appcd version

\--config=<json>

Serialized JSON string to mix into the appcd config

\--config-file=<file>

Path to a appcd JS config file

\--no-colors

Disables colors

#### appcd config

Get and set config options.

`appc appcd config [options]`

#### appcd dump

Dumps the config, status, health, and debug logs to a file.

`appc appcd dump [options]`

#### appcd exec

Connects to the Appc Daemon and executes the request.

`appc appcd` `exec` `[options]`

#### appcd logcat

Streams Appc Daemon debug log output.

`appc appcd logcat [options]`

#### appcd restart

Stops the Appc Daemon if running, then starts it.

`appc appcd restart [options]`

#### appcd start

Starts the Appc Daemon if it's not already running.

`appc appcd start [options]`

#### appcd status

Displays the Appc Daemon status.

`appc appcd status [options]`

#### appcd stop

Stops the Appc Daemon if running.

`appc appcd stop [options]`

#### appcd help

Displays the help screen.

`appc appcd help [options]`

### Cloud/ACS

Manages Arrow Cloud applications by running an Arrow Cloud CLI command. See the [Arrow Cloud Command-Line Interface Reference](/docs/appc/AMPLIFY_Runtime_Services/AMPLIFY_Runtime_Services_Guide/AMPLIFY_Runtime_Services_Command-Line_Interface_Reference/) for more information.

`appc cloud|acs [COMMAND] [COMMON OPTIONS] [COMMAND OPTIONS]`

### Cloud/ACS commands

#### cloud/acs options

\-h, --help

Output usage information

\--dashboard <dashboard>

Dashboard url to use for logins

\-l, --log-level <level>

Change log level

\-o, --output <format>

Format output (only "json" is supported)

\-v, --version

Output the version number

\-q, --quiet

Reduce the amount of text output to the console

\--no-banner

Turn off banner

\-n, --no-colors

Turn off colors

\--no-services

Disable services

\--no-progress, --no-progress-bars

Disable progress bars

\--no-prompt

Disable prompt

\--prompt-port <promptPort>

Port to use socket-based prompting

\--prompt-type <promptType>

Prompt type \["cli","socket","socket-bundle"\], defaults to "cli"

\--username <username>

Username for login

\--password <password>

Password for login

\-e, --env <environment>

Environment such as production, preproduction, development, etc

\-O, --org-id <orgId>

Organization id for logins

\-P, --plugin-paths <pluginPaths>

Comma-separated search paths for plugins

\-r, --registry <registry>

Registry server url to use

\--vpc-env <vpcEnv>

VPC environment for logins

\-d, --dir <dir>

Directory to load app from

\--dates

Turn on dates in logging

#### cloud/acs new

Create a new cloud/acs app.

`appc cloud``/acs` `new [options] <name>`

#### cloud/acs domain

Set or remove domain of an existing app. If no appname provided it can run in app dir or with -d to specify an app dir.

`appc cloud``/acs` `domain [options] [appname]`

#### cloud/acs list

Show the status of all apps or the app specified by appname.

`appc cloud``/acs` `list [options] [appname]`

#### cloud/acs logcat

Tail the log entries output from your app. If no appname provided it can run in app dir or with -d to specify an app dir. 'logcat -h' for more options.

`appc cloud``/acs` `logcat [options] [appname]`

#### cloud/acs loglist

List the log entries during the specified start datetime and end datetime. If no appname provided it can run in app dir or with -d to specify an app dir. 'loglist -h' for more options.

`appc cloud``/acs` `loglist [options] [appname]`

#### cloud/acs accesslog

List the user access logs during the specified start datetime and end datetime. If no appname provided it can run in app dir or with -d to specify an app dir. 'accesslog -h' for more options.

`appc cloud``/acs` `accesslog [options] [appname]`

#### cloud/acs usage

List the system resource usage logs during the specified start datetime and end datetime. If no appname provided it can run in app dir or with -d to specify an app dir. 'usage -h' for more options.

`appc cloud``/acs` `usage [options] [appname]`

#### cloud/acs crt

Manage the custom SSL certificates for accessing apps via https. SSL certificates are used for servers in cloud based on certificate names (SubjectAltName or CN). If no appname provided it can run in app dir or with -d to specify an app dir. 'crt -h' for more options. This feature is available to enterprise user only.

`appc cloud``/acs` `crt [options] [appname]`

#### cloud/acs login

Login to the ACS cloud.

`appc cloud``/acs` `login [options] [username] [password]`

#### cloud/acs logout

Logout of the ACS cloud

`appc cloud``/acs`  `logout`

#### cloud/acs publish

Publish an app to the ACS cloud. run in app dir or with -d to specify an app dir.

`appc cloud``/acs` `publish [options] [npm_username] [npm_password]`

If acs cli complains that npm is not found even though npm is in the path, ensure that the directory containing npm is in the NODE\_PATH (for example, NODE\_PATH=/usr/lib/node\_modules).

#### cloud/acs unpublish

Un-publish an app from the ACS cloud. If no appname provided it can run in app dir or with -d to specify an app dir.

`appc cloud``/acs` `unpublish [options] [appname]`

#### cloud/acs remove

Remove an app from both ACS cloud side and local side. If no appname provided it can run in app dir or with -d to specify an app dir. To remove local dir at the same time -d should be used. In addition, --force must be used to indicate to remove local dir.

`appc cloud``/acs` `remove [options] [appname]`

#### cloud/acs config

Config how many app servers in cloud to use.

`appc cloud``/acs` `config [options] [appname]`

#### cloud/acs whoami

Display current login user.

`appc cloud``/acs`  `whoami` `[options]`

#### cloud/acs server

Set the server size for an app. If no appname provided it can run in app dir or with -d to specify an app dir. 'server -h' for more options.

`appc cloud``/acs` `server [options] [appname]`

#### cloud/acs download

Download the app source file with specified app name and version. If no appname provided it can run in app dir or with -d to specify an app dir, and the currently deployed app version will be downloaded if no app version option provided. 'download -h' for more options.

`appc cloud``/acs` `download [options] [appname]`

#### cloud/acs transfer-domain

Transfer a domain name from an app to another. 'transfer-domain -h' for more options.

`appc cloud``/acs` `transfer-domain [options] <domain_name>`

#### cloud/acs restart

Restart an app running in the API Runtime cloud. If no appname provided it can run in app dir or with -d to specify an app dir.

`appc aloud``/acs` `restart [options] [appname]`

### Config

Get, set, or list configuration settings.

`appc config <get,``set``,list> [<key>][<value>]`

#### Config examples

Display the entire config:

` $ appc config list`

Get a configuration key's value:

`$ appc config get username`

Set a configuration key's value to a string:

`$ appc config` `set` `defaultEnvironment preproduction`

Set a configuration key's value to an object:

`$ appc config` `set` `devEnvironment` `'{"registry":"http://localhost:8082"}'`

Set a deep configuration key's value:

`$ appc config` `set` `devEnvironment.registry http:``//localhost``:8082`

Config commands

#### config get

Retrieves a configuration setting.

`appc config get <KEY_NAME>`

#### config list

Lists configuration settings.

`appc config list`

#### config set

Sets a configuration setting.

`appc config` `set` `<KEY_NAME> <VALUE>`

### Generate

Generate an Appcelerator component.

`appc generate [options]`

#### Generate options

Option

Description

\-D, --description <DESCRIPTION>

Brief description of your project.

\-P, --plugin-paths <PLUGIN\_PATHS>

Comma-separated search paths for plugins.

\-t, --type <TYPES>

Comma-separated list of component types to generate.

### Help

Displays the help screen.

`appc help [<COMMAND>]`

### Info

**Since Release 5.0.0.** Gets the current system information.

`appc info [options]`

### Install

Installs Appcelerator component. If no component is specified, the command will install the dependencies specified in the project's package.json file.

`appc` `install` `[<componentNames>] [options]`

#### Install options

Option

Description

\-h, --help

output usage information

\-t, --type <type>

component type

\-g, --global

Install the component globally for all projects. Saves it in the global cache.

\-f, --force

Force install

\--skip-npm

Skip install NPM dependencies. Only install Appcelerator components.

\-P, --plugin-paths <PLUGIN\_PATHS>

Comma-separated search paths for plugins.

#### Install examples

Install component dependencies for project (requires package.json):

`$ appc` `install`

Install a component locally:

`$ appc` `install` `connector``/appc``.arrowdb`

Install a component globally:

`$ appc` `install` `connector``/appc``.arrowdb -g`

Install a titanium module

`$ appc` `install` `-t module hyperloop`

### Login

Logs into the AMPLIFY Appcelerator Services.

`appc login [options]`

#### Login options

Option

Description

\-H, --host <HOST\_SERVER>

Host for login.

\-t, --token <TOKEN>

Login using a generated token.

### Logout

Logout from the AMPLIFY Appcelerator Services.

`appc` `logout` `[options]`

#### Logout options

Option

Description

\-D, --deauthorize

Delete device authorization on logout.

### New

Create a new app and/or server project.

`appc new [options]`

#### New options

Option

Description

\-f, --force

Overwrite any existing projects.

\--id <PROJECT\_ID>

ID for your project.

\-n, --name <PROEJCT\_NAME>

Name of the project.

\--no-services

Skip registering for AMPLIFY Appcelerator Services for Titanium projects.

\-p, --platforms <PLATFORMS>

Platforms for Titanium projects.

\-P, --plugin-paths <PLUGIN\_PATHS>

Comma-separated search paths for plugins.

\--project-dir <PROJECT\_DIRECTORY>

Directory containing the project.

\-S, --subtype <SUBTYPE>

Project subtype, such as sample or new.

\-t, --type <TYPES>

Project type such as \`app\`, \`api\`, \`timodule\` or \`applewatch\`.

#### New examples

Create new project via interactive prompting:

Create a new titanium project

Create a new api project

### Org

Manager registry organizations for a component. Only applicable if the component access rights are set to either org or user\_or\_org.

`appc org <add, remove, list> [<orgID>] [<component>]`

### Org commands

**NOTE:** executing **add** or **rm** without an **orgId** will prompt you with a list of available orgs.

#### org add

Add an organization to a component.

`appc org add <ORGANIZATION_ID> [<COMPONENT>]`

#### org list

Lists organizations for a component.

`appc org list [<COMPONENT>]`

#### org rm | remove

Remove an organization from a component.

`appc org` `rm` `<ORGANIZATION_ID> [<COMPONENT>]`

### Org examples

List orgs for a component:

`$ appc org list connector``/my``.connector`

A dd an org to a component:

`$ appc org add 12345 connector``/my``.connector`

Remove an org from a component:

`$ appc org remove 12345 connector``/my``.connector`

### Owner

Manager registry owners for a component. Owners are specified by their AMPLIFY Appcelerator Services username or email.

`appc owner <add, remove, list> [<owner>] [<component>]`

### Owner commands

#### owner add

Adds an owner to a component.

`appc owner add <USERNAME> [<COMPONENT>]`

#### owner list

Lists owners of a component.

`appc owner list [<COMPONENT>]`

#### owner rm | remove

Removes an owner from a component.

`appc owner` `rm` `<USERNAME> [<COMPONENT>]`

### Owner examples

Lists owners for a component:

`$ appc owner list`

Removes an owner from a component:

`$ appc owner remove user@domain.org`

Add an owner to a component

`$ appc owner add newowner@email.com`

### Platform

Runs a specified API against AMPLIFY Appcelerator Services.

`appc platform <api> [<args...>] [options]`

### Publish

Publish a component to the registry. You should run this command from inside the project's directory.

`appc publish [options]`

#### Publish options

Option

Description

\-f, --force

Overwrite any existing projects.

\-P, --plugin-paths <PLUGIN\_PATHS>

Comma-separated search paths for plugins.

\--image <name\[:tag\]>

Name of the docker image

\--app-version <version>

Version of the app to be published. Only use with '--image' option

\--prerelease

Assign as a pre-release build rather than a latest build

### Remove

Remove installed Appcelerator CLI

`appc remove [version]`

#### Remove options

Option

Description

\-a, --all

Remove all installed but non-active versions

\-f, --force

Force the removal to proceed

Run a project–either build and run a Titanium application, or build and locally run an Arrow application.

`appc run [options]`

The following options only apply to Titanium applications:

#### Generic build options and flags

Option

Description

\-b, --build-only

Only perform the build; when specified, does not install or run the app.

When building a Windows project using appc run -p windows -T wp-device --wp-sdk ## --build-only, you can now use SDK values (e.g. 10.0.10240.0, 10.0.10586.0, etc.).

\-f, --force

Force a clean rebuild.

\--skip-js-minify

Bypasses JavaScript minification. Simulator builds are never minified. Only supported for Android and iOS.

\--log-level <level>

Minimum logging level. Supported options are **trace**, **debug**, **info**, **warn**, and **error**.

\-p, --platforms <platform>

Target build platform: Supported values are **android**, **ios**, and **windows**. (**iphone** and **ipad** are currently accepted as synonyms for **ios**.)

\-d, --project-dir <directory>

Directory containing the project, otherwise the current working directory is assumed.

\-s, --sdk <version>

Titanium SDK version to build with. If not specified, uses the configured default SDK.

#### Android build options

Option

Description

\-A, --android-sdk <path>

Path to the Android SDK.

\-C, --device-id <name>

Name of the device or emulator to install the application to. When --target is "device", then you can specify "all" to install the app to all connected devices.

\-D, --deploy-type <type>

Controls several settings such as optimization, encryption, and analytics. Type can be **development**, **test**, or **production**.

When --target is "emulator", the deploy type defaults to **development**, but can be set to **test**.

When --target is "device", the deploy type defaults to **test**, but can be set to **development**.

When --target is "dist-playstore", the deploy type is **production** and cannot be overwritten.

Note that **test** will minify and encrypt your JavaScript source code. Any JavaScript syntax errors, even files you are not using, will result in a build failure.

\-K, --keystore <path>

Location of the keystore file.

\--key-password <keypass>

Password of the keystore private key. Defaults to value specified with --store-password.

\--liveview

Starts a [LiveView](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Titanium_Development/LiveView/) session to let you quickly preview changes to your application's UI. **Requires Appcelerator Studio.**

\-L, --alias <alias>

Alias for the keystore.

\--no-launch

Disables launching the app after installing.

\-O, --output-dir <dir>

Output directory (used when target is **dist-playstore**).

\-P, --store-password <password>

Password for the keystore.

\--sigalg <algorithm>

The digital signature algorithm to sign the .apk with. Possible algorithms are **MD5withRSA**, **SHA1withRSA**, and **SHA256withRSA**.

\-T, --target <value>

Target to build for. Target can be **emulator**, **device**, or **dist-playstore**.

#### iOS build options and flags

Option

Description

\-C, --device-id <name>

Name of the device or emulator to install the application to. When --target is "device", then you can specify "all" to install the app to all connected devices.

\-D, --deploy-type <type>

Controls several settings such as optimization, encryption, and analytics. Type can be **development**, **test**, or **production**.

When --target is "simulator", the deploy type defaults to **development**, but can be set to **test**.

When --target is "device", the deploy type defaults to **test**, but can be set to **development**.

When --target is "dist-appstore" or "dist-adhoc", the deploy type is **production** and cannot be overwritten.

Note that **test** will minify and encrypt your JavaScript source code. Any JavaScript syntax errors, even files you are not using, will result in a build failure.

\--force-copy

Forces files to be copied instead of symlinked for simulator builds only.

\--force-copy-all

Identical to the --force-copy flag except this will also copy the 32.5 MB libTiCore.a file. **Removed since 8.0.0 and moving to the native JavaScriptCore library.**

\--launch-watch-app

Launch both the watch app and main app; only used when target is **simulator**.

\--launch-watch-app-only

Launch only the watch app; only used when target is **simulator**.

\--sim-focus

Focus the iOS simulator (default is true). To not focus the simulator, use --no-sim-focus.

\-V, --developer-name <name>

iOS Developer Certificate to use; required when target is **device**.

\-F, --device-family <value>

Device family to build for (**iphone**, **ipad**, or **universal**). Default is **universal**, however if --target is set to "ipad", then the value defaults to **ipad**.

\-I, --ios-version <value>

iOS SDK version to build for. Default: latest installed iOS SDK.

\-K, --keychain <value>

Path to the distribution keychain to use instead of the system default; only used when target is **device**, **dist-appstore**, or **dist-adhoc**.

\--launch-bundle-id <id>

After installing the app in the iOS Simulator, launch a different app instead of the app that was just built. Useful if you need to launch a test runner that in turn launches your app.

\-O, --output-dir <dir>

Output directory. Only used when target is **dist-adhoc**.

\-P, --pp-uuid <uuid>

Provisioning profile uuid; required when target is **device**, **dist-appstore**, or **dist-adhoc**.

\-R, --distribution-name <name>

iOS Distribution Certificate to use; required when target is **dist-appstore** or **dist-adhoc**.

\--sim-focus

Focus the iOS Simulator after launching. Defaults to **true**.

\-T, --target <value>

Target to build for: **simulator**, **device**, **dist-appstore**, or **dist-adhoc**.

\--watch-app-name <name>

Name of the watch app to launch; only used when target is **simulator**.

\-W, --watch-device-id <udid>

Watch simulator UDID to launch when building an app with a watch app; only used when target is **simulator**.

\-Y, --sim-type <type>

iOS Simulator type: **iphone** or **ipad**; only used when target is **simulator**.

#### Windows build options

As of Titanium 9.0.0, building Windows apps is no longer supported.

Support for Windows 8.1 and Windows Phone SDKs has been deprecated as of SDK 6.3.0.GA and has be removed in SDK 7.0.0.GA.

Options

Description

\-C, --device-id <value>

UDID of the Windows Phone 8 device or emulator to build for. Only used when the target is **wp-emulator** or **wp-device**.

Note: An app can only be installed to a single device at a time.

\-D, --deploy-type <type>

Type of deployment (**test**, **development** or **production**). Only used when the target is **wp-emulator**, **wp-device** or **ws-local**.

\-G, --wp-publisher-guid <GUID>

Windows Phone Publisher ID. Only used when the target is **wp-emulator**, **wp-device** or **dist-**phonestore****.

\-I, --win-publisher-id <ID>

Windows Publisher ID. Required to build the application.

\--wp-product-guid <GUID>

**Deprecated as of 6.1.0**. Windows 8 product ID, used for upgrading Win 8 apps to Win 8.1. Deprecated and will be removed in future version, use --win-product-guid instead.

\-H, --win-product-guid <GUID>

**Since Release 6.1.0**. Windows 10 product ID, used for upgrading Windows 8.1 apps to Windows 10.

\-O, --output-dir <dir>

Output directory. Only used when target is **dist-phonestore** or **dist-winstore**.

\--ws-cert <file>

**Deprecated as of Release 6.1.0**. Location of the Windows Store certificate file. Only used when target is **ws-local** or **dist-winstore**. Deprecated and will be removed in future version, use --win-cert instead.

\-R, --win-cert <file>

**Since Release 6.1.0**. Location of the Windows Store certificate file. Only used when target is **ws-local** or **dist-winstore**.

\--wp-sdk <version>

**Deprecated as of Release 6.1.0**. Windows Phone SDK version. Deprecated and will be removed in future version, use --win-sdk instead.

\-S, --win-sdk <version>

**Since Release 6.1.0**. Windows SDK version. When you run CLI on Windows 10, you can specify **10.0** to indicate building for Windows 10 _Universal Windows Platform_ (_UWP_) app. You can target more specific SDK version, such as **10.0.15063.0**.

\-V, --vs-target <version>

Visual Studio target to build for.

* **12.0** to use Visual Studio 2013

* **14.0** to use Visual Studio 2015

* **Visual Studio Community 2017** to use Visual Studio Community 2017

* **Visual Studio Professional 2017** to use Visual Studio Professional 2017

* **Visual Studio Enterprise 2017** to use Visual Studio Enterprise 2017


\-T, --target <value>

Target to build for:

* **wp-emulator** to run a Windows Phone app on the emulator

* **wp-device** to run a Window Phone app on a device connected to your host machine

* **dist-**phonestore**** to pakcage a Windows Phone app

* **ws-local** to run a Windows Store app on your local machine

* **dist-winstore** to package a Windows Store app


\--skipInstallDependencies

**Since Release 6.1.0.** Skip installing dependency packages. If you had trouble with app deployment on device, try this option.

### Search

Search for components in the registry.

`appc search <QUERY_TERM> [options]`

#### Search options

Option

Description

\-f, --filter <FILTER>

Overwrite any existing projects.

### Setup

Runs the setup wizard and checks your environment.

`appc setup [options]`

### Switch

**Since Release 5.0.0.** Switch organizations without logging in or out of the CLI.

`appc switch <org> [options]`

### Titanium | ti

Execute titanium commands. See the [Titanium Command-Line Interface Reference](/docs/appc/Titanium_SDK/Titanium_SDK_Guide/Titanium_Command-Line_Interface_Reference/) for more information.

`appc ti <``command``> [options]`

`appc titanium <``command``> [options]`

### Unpublish

Unpublish a project or component. The component name is only required if the project is run outside the project directory.

`appc unpublish [options] [component]`

#### Unpublish options

Option

Description

\-d, --project-dir <projectDir>

Directory containing the project.

\-f, --force

Force unpublish.

### Use

Selects the version of the CLI to use. Running the command with no options lists the available versions.

`appc use [<add, remove, list>] [<user>] [<component>]`

#### Use options

Option

Description

\-d, --project-dir <projectDir>

Directory containing the project.

\-f, --force

Force unpublish.

### User

Manage registry users for a component. Only applicable if the component access rights are set to either user or user\_or\_org.

`appc user <add,remove,list>[ <user>][ <component>]`

#### User examples

Remove a user:

`$ appc user remove user@domain.org`

Add a user:

`$ appc user add newowner@email.com`

### User commands

#### user add

Adds a user to a component.

`appc user add <USERNAME> [<COMPONENT>]`

#### user rm | remove

Removes a user from a component.

`appc user` `rm` `<USERNAME> [<COMPONENT>]`

### Whoami

Displays information about the currently logged-in user.

`appc` `whoami` `[options]`

#### Whoami options

Option

Description

\-f, --full

Provides information about all the organizations, apps, etc. the user is a part of.

\-l, --log-level <level>

Change log level

\-o, --output <OUTPUT\_FORMAT>

Output format. Currently only json is supported.
