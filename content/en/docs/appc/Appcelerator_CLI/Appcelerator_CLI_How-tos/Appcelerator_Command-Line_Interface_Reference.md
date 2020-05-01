{"title":"Appcelerator Command-Line Interface Reference","weight":"20"}

* [appc commands](#appc-commands)

    * [Global options](#global-options)

    * [Access](#access)

    * [Access commands](#access-commands)

        * [access get](#access-get)

    * [access set](#access-set)

    * [Alloy](#alloy)

        * [Alloy options](#alloy-options)

        * [alloy new](#alloy-new)

        * [alloy compile](#alloy-compile)

        * [alloy extract-i18n](#alloy-extract-i18n)

        * [alloy generate](#alloy-generate)

        * [alloy copy](#alloy-copy)

        * [alloy move](#alloy-move)

        * [alloy remove](#alloy-remove)

    * [Appc Daemon](#appc-daemon)

        * [Daemon options](#daemon-options)

        * [appcd config](#appcd-config)

        * [appcd dump](#appcd-dump)

        * [appcd exec](#appcd-exec)

        * [appcd logcat](#appcd-logcat)

        * [appcd restart](#appcd-restart)

        * [appcd start](#appcd-start)

        * [appcd status](#appcd-status)

        * [appcd stop](#appcd-stop)

        * [appcd help](#appcd-help)

    * [Cloud/ACS](#cloud/acs)

    * [Cloud/ACS commands](#cloud/acs-commands)

        * [cloud/acs options](#cloud/acs-options)

        * [cloud/acs new](#cloud/acs-new)

        * [cloud/acs domain](#cloud/acs-domain)

        * [cloud/acs list](#cloud/acs-list)

        * [cloud/acs logcat](#cloud/acs-logcat)

        * [cloud/acs loglist](#cloud/acs-loglist)

        * [cloud/acs accesslog](#cloud/acs-accesslog)

        * [cloud/acs usage](#cloud/acs-usage)

        * [cloud/acs crt](#cloud/acs-crt)

        * [cloud/acs login](#cloud/acs-login)

        * [cloud/acs logout](#cloud/acs-logout)

        * [cloud/acs publish](#cloud/acs-publish)

        * [cloud/acs unpublish](#cloud/acs-unpublish)

        * [cloud/acs remove](#cloud/acs-remove)

        * [cloud/acs config](#cloud/acs-config)

        * [cloud/acs whoami](#cloud/acs-whoami)

        * [cloud/acs server](#cloud/acs-server)

        * [cloud/acs download](#cloud/acs-download)

        * [cloud/acs transfer-domain](#cloud/acs-transfer-domain)

        * [cloud/acs restart](#cloud/acs-restart)

    * [Config](#config)

        * [Config examples](#config-examples)

        * [config get](#config-get)

        * [config list](#config-list)

        * [config set](#config-set)

    * [Generate](#generate)

        * [Generate options](#generate-options)

    * [Help](#help)

    * [Info](#info)

    * [Install](#install)

        * [Install options](#install-options)

        * [Install examples](#install-examples)

    * [Login](#login)

        * [Login options](#login-options)

    * [Logout](#logout)

        * [Logout options](#logout-options)

    * [New](#new)

        * [New options](#new-options)

        * [New examples](#new-examples)

    * [Org](#org)

    * [Org commands](#org-commands)

        * [org add](#org-add)

        * [org list](#org-list)

        * [org rm | remove](#org-rm-|-remove)

    * [Org examples](#org-examples)

    * [Owner](#owner)

    * [Owner commands](#owner-commands)

        * [owner add](#owner-add)

        * [owner list](#owner-list)

        * [owner rm | remove](#owner-rm-|-remove)

    * [Owner examples](#owner-examples)

    * [Platform](#platform)

    * [Publish](#publish)

        * [Publish options](#publish-options)

    * [Remove](#remove)

        * [Remove options](#remove-options)

        * [Generic build options and flags](#generic-build-options-and-flags)

        * [Android build options](#android-build-options)

        * [iOS build options and flags](#ios-build-options-and-flags)

        * [Windows build options](#windows-build-options)

    * [Search](#search)

        * [Search options](#search-options)

    * [Setup](#setup)

    * [Switch](#switch)

    * [Titanium | ti](#titanium-|-ti)

    * [Unpublish](#unpublish)

        * [Unpublish options](#unpublish-options)

    * [Use](#use)

        * [Use options](#use-options)

    * [User](#user)

        * [User examples](#user-examples)

    * [User commands](#user-commands)

        * [user add](#user-add)

        * [user rm | remove](#user-rm-|-remove)

    * [Whoami](#whoami)

        * [Whoami options](#whoami-options)

The Appcelerator Command-Line Interface (CLI) is a Node.js-based command-line tool for managing, building, and deploying Appcelerator projects, including Alloy, Titanium and Arrow projects. The Appcelerator CLI provides a unified mechanism for using the other CLI components.

This article provides in-depth information about the CLI commands and options. For information about some common tasks, see [Appcelerator CLI Tasks](/docs/appc/Appcelerator_CLI/Appcelerator_CLI_How-tos/Appcelerator_CLI_Tasks/).

## appc commands

If you don't specify all of the required options, appc prompts you for the missing options.

### Global options

| Option | Description |
| --- | --- |
| \-h, --help | Output usage information |
| \--dashboard <dashboard> | Dashboard URL used for logins |
| \-l, --log-level <LOG\_LEVEL> | Sets the log output level. Specify either: trace, debug, info, warn or error. |
| \-o, --output <format> | Format output (only "json" is supported) |
| \-v, --version | Output the version of the CLI (if \-o "json" is used, the version of npm will also be output) |
| \-q, --quiet | Reduce the amount of text output to the console |
| \--no-banner | Disable banner |
| \--no-colors | Disable colors |
| \--no-services | Disable services |
| \--no-progress, --no-progress-bars | Disable progress bars |
| \--no-prompt | Disable prompt |
| \--prompt-port <promptPort> | Port to use socket-based prompting |
| \--prompt-type <PROMPT\_TYPE> | Prompt type. Specify either cli, socket or socket-bundle. Default is cli. |
| \--username <USERNAME> | Username for login |
| \--password <USER\_PASSWORD> | Password for login |
| \-e, --env <ENVIRONMENT> | Environment to run the command. Specify either production, preproduction or development. |
| \-O, --org-id <orgId> | Organization id for login |
| \-P, --plugin-paths <pluginPaths> | Comma-separated search paths for plugins |
| \-r, --registry <REGISTRY> | Registry server URL to use |
| \-s, --server <SECURITY\_SERVER> | Security server URL used for logins |
| \-v, --vpc-env <vpcEnv> | vpc environment for login |

### Access

Manage a component's access rights.

### Access commands

#### access get

Retrieves the component's access rights.

```bash
appc access get <MODULE_NAME> <options>
```

Example to get a module's access rights: $ appc access get connector/com.foo@1.0.0

### access set

Sets the component's access rights.

```bash
appc access set <MODULE_NAME> <ACCESS_RIGHTS> <options>
```

Access rights can be either:

* public: everyone can see the component.

* private (default): only the publisher can see the component.

* org: Only certain organizations can see the component. Use the appc org command to add or remove organizations.

* user: Only certain users can see the component. Use the appc user command to add or remove users.

* user\_or\_org: Only certain users or organizations can see the component. Use the appc user or appc org command to add or remove users or organizations, respectively.

Example to set a module's access rights: $ appc access set connector/com.foo@1.0.0 private

### Alloy

Run an Alloy CLI command. See the [Alloy Command-Line Interface Reference](/docs/appc/Alloy_Framework/Alloy_How-tos/Alloy_Reference_Guides/Alloy_Command-Line_Interface_Reference/) for more information.

```bash
appc alloy [command] [args] [options]
```

#### Alloy options

<table class="confluenceTable"><thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" "><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-h, --help</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Output usage information</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--dashboard &lt;dashboard&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Dashboard url to use for logins</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-l, --log-level &lt;LOG_LEVEL&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Sets the log output level. Specify either: <tt class=" ">trace</tt>, <tt class=" ">debug</tt>, <tt class=" ">info</tt>, <tt class=" ">warn</tt> or <tt class=" ">error</tt>.</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-o, --output &lt;format&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Format output (only "json" is supported)</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-v, --version</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Output the version of the cli (if -o "json", the version of npm will also be output)</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-a, --app &lt;app&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Test app folder for running "alloy test"</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-A, --apply</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Applies command changes [extract-i18n]</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-b, --noBanner</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Disable the banner</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-c, --config &lt;config&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Pass in compiler configuration</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-f, --force</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Force the command to execute</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-l, --logLevel &lt;logLevel&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Log level (default: 3 [DEBUG])</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-n, --no-colors</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Turn off colors</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-o, --outputPath &lt;outputPath&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Output path for generated code</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-p, --project-dir &lt;project-dir&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Titanium project directory</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-q, --platform &lt;platform&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Target mobile platform [android,ios]</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-s, --spec &lt;spec&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Test spec to use with "alloy test"</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-w, --all</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Require flag for generate styles</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-x, --column &lt;column&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Column for source map query (default: 1)</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-y, --line &lt;line&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Line for source map query (default: 1)</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-z, --source &lt;source&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Source original file for source map query</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--widgetname &lt;name&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Widget name, used with generate command</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--testapp &lt;name&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Test app name to import, used with new command</p></td></tr></tbody></table>

#### alloy new

Create a new alloy project.

```bash
appc alloy new [dir] [options]
```

{{% alert title="⚠️ Warning" color="primary" %}}As of CLI 7.1.0, A custom template directory can be added via this commands:

```bash
appc alloy new . </path/to/template>
```

or

```bash
appc new --template </path/to/template>
```{{% /alert %}}

#### alloy compile

Compile into titanium source code.

```bash
appc alloy compile [dir] [options]
```

#### alloy extract-i18n

Extracts i18n strings from the source code (js and tss files).

```bash
appc alloy extract-i18n [language] [options]
```

#### alloy generate

Generate a new alloy type such as a controller.

```bash
appc alloy generate [type] [name] [options]
```

#### alloy copy

Copy the controller, view, and style files from <source> to <destination>.

```bash
appc alloy copy [source] [destination] [options]
```

#### alloy move

Move the controller, view, and style files from <source> to <destination>.

```bash
appc alloy copy [source] [destination] [options]
```

#### alloy remove

Remove the controller, view, and style files at <source>.

```bash
appc alloy copy [source] [options]
```

### Appc Daemon

The Appcelerator Daemon is a server that hosts services which power the tooling for Axway products such as Titanium SDK.

```bash
appc appcd COMMAND [ARGS] [OPTIONS]
```

#### Daemon options

<table class="confluenceTable"><thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" "><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-h, --help</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Display help</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-v, --version</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Outputs the appcd version</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--config=&lt;json&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Serialized JSON string to mix into the appcd config</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--config-file=&lt;file&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Path to a appcd JS config file</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--no-colors</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Disables colors</p></td></tr></tbody></table>

#### appcd config

Get and set config options.

```bash
appc appcd config [options]
```

#### appcd dump

Dumps the config, status, health, and debug logs to a file.

```bash
appc appcd dump [options]
```

#### appcd exec

Connects to the Appc Daemon and executes the request.

```bash
appc appcd exec [options]
```

#### appcd logcat

Streams Appc Daemon debug log output.

```bash
appc appcd logcat [options]
```

#### appcd restart

Stops the Appc Daemon if running, then starts it.

```bash
appc appcd restart [options]
```

#### appcd start

Starts the Appc Daemon if it's not already running.

```bash
appc appcd start [options]
```

#### appcd status

Displays the Appc Daemon status.

```bash
appc appcd status [options]
```

#### appcd stop

Stops the Appc Daemon if running.

```bash
appc appcd stop [options]
```

#### appcd help

Displays the help screen.

```bash
appc appcd help [options]
```

### Cloud/ACS

Manages Arrow Cloud applications by running an Arrow Cloud CLI command. See the [Arrow Cloud Command-Line Interface Reference](/docs/appc/AMPLIFY_Runtime_Services/AMPLIFY_Runtime_Services_Guide/AMPLIFY_Runtime_Services_Command-Line_Interface_Reference/) for more information.

```bash
appc cloud|acs [COMMAND] [COMMON OPTIONS] [COMMAND OPTIONS]
```

### Cloud/ACS commands

#### cloud/acs options

<table class="confluenceTable"><thead class=" "></thead><tfoot class=" "></tfoot><tbody class=" "><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-h, --help</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Output usage information</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--dashboard &lt;dashboard&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Dashboard url to use for logins</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-l, --log-level &lt;level&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Change log level</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-o, --output &lt;format&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Format output (only "json" is supported)</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-v, --version</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Output the version number</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-q, --quiet</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Reduce the amount of text output to the console</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--no-banner</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Turn off banner</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-n, --no-colors</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Turn off colors</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--no-services</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Disable services</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--no-progress, --no-progress-bars</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Disable progress bars</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--no-prompt</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Disable prompt</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--prompt-port &lt;promptPort&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Port to use socket-based prompting</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--prompt-type &lt;promptType&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Prompt type ["cli","socket","socket-bundle"], defaults to "cli"</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--username &lt;username&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Username for login</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--password &lt;password&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Password for login</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-e, --env &lt;environment&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Environment such as production, preproduction, development, etc</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-O, --org-id &lt;orgId&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Organization id for logins</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-P, --plugin-paths &lt;pluginPaths&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Comma-separated search paths for plugins</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-r, --registry &lt;registry&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Registry server url to use</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--vpc-env &lt;vpcEnv&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>VPC environment for logins</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">-d, --dir &lt;dir&gt;</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Directory to load app from</p></td></tr><tr><td class="confluenceTd" rowspan="1" colspan="1"><p><tt class=" ">--dates</tt></p></td><td class="confluenceTd" rowspan="1" colspan="1"><p>Turn on dates in logging</p></td></tr></tbody></table>

#### cloud/acs new

Create a new cloud/acs app.

```bash
appc cloud/acs new [options] <name>
```

#### cloud/acs domain

Set or remove domain of an existing app. If no appname provided it can run in app dir or with -d to specify an app dir.

```bash
appc cloud/acs domain [options] [appname]
```

#### cloud/acs list

Show the status of all apps or the app specified by appname.

```bash
appc cloud/acs list [options] [appname]
```

#### cloud/acs logcat

Tail the log entries output from your app. If no appname provided it can run in app dir or with -d to specify an app dir. 'logcat -h' for more options.

```bash
appc cloud/acs logcat [options] [appname]
```

#### cloud/acs loglist

List the log entries during the specified start datetime and end datetime. If no appname provided it can run in app dir or with -d to specify an app dir. 'loglist -h' for more options.

```bash
appc cloud/acs loglist [options] [appname]
```

#### cloud/acs accesslog

List the user access logs during the specified start datetime and end datetime. If no appname provided it can run in app dir or with -d to specify an app dir. 'accesslog -h' for more options.

```bash
appc cloud/acs accesslog [options] [appname]
```

#### cloud/acs usage

List the system resource usage logs during the specified start datetime and end datetime. If no appname provided it can run in app dir or with -d to specify an app dir. 'usage -h' for more options.

```bash
appc cloud/acs usage [options] [appname]
```

#### cloud/acs crt

Manage the custom SSL certificates for accessing apps via https. SSL certificates are used for servers in cloud based on certificate names (SubjectAltName or CN). If no appname provided it can run in app dir or with -d to specify an app dir. 'crt -h' for more options. This feature is available to enterprise user only.

```bash
appc cloud/acs crt [options] [appname]
```

#### cloud/acs login

Login to the ACS cloud.

```bash
appc cloud/acs login [options] [username] [password]
```

#### cloud/acs logout

Logout of the ACS cloud

```bash
appc cloud/acs logout
```

#### cloud/acs publish

Publish an app to the ACS cloud. run in app dir or with -d to specify an app dir.

```bash
appc cloud/acs publish [options] [npm_username] [npm_password]
```

{{% alert title="⚠️ Warning" color="primary" %}}If acs cli complains that npm is not found even though npm is in the path, ensure that the directory containing npm is in the NODE\_PATH (for example, NODE\_PATH=/usr/lib/node\_modules).{{% /alert %}}

#### cloud/acs unpublish

Un-publish an app from the ACS cloud. If no appname provided it can run in app dir or with -d to specify an app dir.

```bash
appc cloud/acs unpublish [options] [appname]
```

#### cloud/acs remove

Remove an app from both ACS cloud side and local side. If no appname provided it can run in app dir or with -d to specify an app dir. To remove local dir at the same time -d should be used. In addition, --force must be used to indicate to remove local dir.

```bash
appc cloud/acs remove [options] [appname]
```

#### cloud/acs config

Config how many app servers in cloud to use.

```bash
appc cloud/acs config [options] [appname]
```

#### cloud/acs whoami

Display current login user.

```bash
appc cloud/acs whoami [options]
```

#### cloud/acs server

Set the server size for an app. If no appname provided it can run in app dir or with -d to specify an app dir. 'server -h' for more options.

```bash
appc cloud/acs server [options] [appname]
```

#### cloud/acs download

Download the app source file with specified app name and version. If no appname provided it can run in app dir or with -d to specify an app dir, and the currently deployed app version will be downloaded if no app version option provided. 'download -h' for more options.

```bash
appc cloud/acs download [options] [appname]
```

#### cloud/acs transfer-domain

Transfer a domain name from an app to another. 'transfer-domain -h' for more options.

```bash
appc cloud/acs transfer-domain [options] <domain_name>
```

#### cloud/acs restart

Restart an app running in the API Runtime cloud. If no appname provided it can run in app dir or with -d to specify an app dir.

```bash
appc aloud/acs restart [options] [appname]
```

### Config

Get, set, or list configuration settings.

```bash
appc config <get,set,list> [<key>][<value>]
```

#### Config examples

Display the entire config:

```bash
$ appc config list
```

Get a configuration key's value:

```bash
$ appc config get username
```

Set a configuration key's value to a string:

```bash
$ appc config set defaultEnvironment preproduction
```

Set a configuration key's value to an object:

```bash
$ appc config set devEnvironment '{"registry":"http://localhost:8082"}'
```

Set a deep configuration key's value:

```bash
$ appc config set devEnvironment.registry http://localhost:8082
```

Config commands

#### config get

Retrieves a configuration setting.

```bash
appc config get <KEY_NAME>
```

#### config list

Lists configuration settings.

```bash
appc config list
```

#### config set

Sets a configuration setting.

```bash
appc config set <KEY_NAME> <VALUE>
```

### Generate

Generate an Appcelerator component.

```bash
appc generate [options]
```

#### Generate options

| Option | Description |
| --- | --- |
| \-D, --description <DESCRIPTION> | Brief description of your project. |
| \-P, --plugin-paths <PLUGIN\_PATHS> | Comma-separated search paths for plugins. |
| \-t, --type <TYPES> | Comma-separated list of component types to generate. |

### Help

Displays the help screen.

```bash
appc help [<COMMAND>]
```

### Info

**Since Release 5.0.0.** Gets the current system information.

```bash
appc info [options]
```

### Install

Installs Appcelerator component. If no component is specified, the command will install the dependencies specified in the project's package.json file.

```bash
appc install [<componentNames>] [options]
```

#### Install options

| Option | Description |
| --- | --- |
| \-h, --help | output usage information |
| \-t, --type <type> | component type |
| \-g, --global | Install the component globally for all projects. Saves it in the global cache. |
| \-f, --force | Force install |
| \--skip-npm | Skip install NPM dependencies. Only install Appcelerator components. |
| \-P, --plugin-paths <PLUGIN\_PATHS> | Comma-separated search paths for plugins. |

#### Install examples

Install component dependencies for project (requires package.json):

```bash
$ appc install
```

Install a component locally:

```bash
$ appc install connector/appc.arrowdb
```

Install a component globally:

```bash
$ appc install connector/appc.arrowdb -g
```

Install a titanium module

```bash
$ appc install -t module hyperloop
```

### Login

Logs into the AMPLIFY Appcelerator Services.

```bash
appc login [options]
```

#### Login options

| Option | Description |
| --- | --- |
| \-H, --host <HOST\_SERVER> | Host for login. |
| \-t, --token <TOKEN> | Login using a generated token. |

### Logout

Logout from the AMPLIFY Appcelerator Services.

```bash
appc logout [options]
```

#### Logout options

| Option | Description |
| --- | --- |
| \-D, --deauthorize | Delete device authorization on logout. |

### New

Create a new app and/or server project.

```bash
appc new [options]
```

#### New options

| Option | Description |
| --- | --- |
| \-f, --force | Overwrite any existing projects. |
| \--id <PROJECT\_ID> | ID for your project. |
| \-n, --name <PROEJCT\_NAME> | Name of the project. |
| \--no-services | Skip registering for AMPLIFY Appcelerator Services for Titanium projects. |
| \-p, --platforms <PLATFORMS> | Platforms for Titanium projects. |
| \-P, --plugin-paths <PLUGIN\_PATHS> | Comma-separated search paths for plugins. |
| \--project-dir <PROJECT\_DIRECTORY> | Directory containing the project. |
| \-S, --subtype <SUBTYPE> | Project subtype, such as sample or new. |
| \-t, --type <TYPES> | Project type such as \`app\`, \`api\`, \`timodule\` or \`applewatch\`. |

#### New examples

Create new project via interactive prompting:

Create a new titanium project

Create a new api project

### Org

Manager registry organizations for a component. Only applicable if the component access rights are set to either org or user\_or\_org.

```bash
appc org <add, remove, list> [<orgID>] [<component>]
```

### Org commands

**NOTE:** executing **add** or **rm** without an **orgId** will prompt you with a list of available orgs.

#### org add

Add an organization to a component.

```bash
appc org add <ORGANIZATION_ID> [<COMPONENT>]
```

#### org list

Lists organizations for a component.

```bash
appc org list [<COMPONENT>]
```

#### org rm | remove

Remove an organization from a component.

```bash
appc org rm <ORGANIZATION_ID> [<COMPONENT>]
```

### Org examples

List orgs for a component:

```bash
$ appc org list connector/my.connector
```

A dd an org to a component:

```bash
$ appc org add 12345 connector/my.connector
```

Remove an org from a component:

```bash
$ appc org remove 12345 connector/my.connector
```

### Owner

Manager registry owners for a component. Owners are specified by their AMPLIFY Appcelerator Services username or email.

```bash
appc owner <add, remove, list> [<owner>] [<component>]
```

### Owner commands

#### owner add

Adds an owner to a component.

```bash
appc owner add <USERNAME> [<COMPONENT>]
```

#### owner list

Lists owners of a component.

```bash
appc owner list [<COMPONENT>]
```

#### owner rm | remove

Removes an owner from a component.

```bash
appc owner rm <USERNAME> [<COMPONENT>]
```

### Owner examples

Lists owners for a component:

```bash
$ appc owner list
```

Removes an owner from a component:

```bash
$ appc owner remove user@domain.org
```

Add an owner to a component

```bash
$ appc owner add newowner@email.com
```

### Platform

Runs a specified API against AMPLIFY Appcelerator Services.

```bash
appc platform <api> [<args...>] [options]
```

### Publish

Publish a component to the registry. You should run this command from inside the project's directory.

```bash
appc publish [options]
```

#### Publish options

| Option | Description |
| --- | --- |
| \-f, --force | Overwrite any existing projects. |
| \-P, --plugin-paths <PLUGIN\_PATHS> | Comma-separated search paths for plugins. |
| \--image <name\[:tag\]> | Name of the docker image |
| \--app-version <version> | Version of the app to be published. Only use with '--image' option |
| \--prerelease | Assign as a pre-release build rather than a latest build |

### Remove

Remove installed Appcelerator CLI

```bash
appc remove [version]
```

#### Remove options

| Option | Description |
| --- | --- |
| \-a, --all | Remove all installed but non-active versions |
| \-f, --force | Force the removal to proceed |

Run a project–either build and run a Titanium application, or build and locally run an Arrow application.

```bash
appc run [options]
```

The following options only apply to Titanium applications:

#### Generic build options and flags

| Option | Description |
| --- | --- |
| \-b, --build-only | Only perform the build; when specified, does not install or run the app.  <br />  <br />When building a Windows project using appc run -p windows -T wp-device --wp-sdk ## --build-only, you can now use SDK values (e.g. 10.0.10240.0, 10.0.10586.0, etc.). |
| \-f, --force | Force a clean rebuild. |
| \--skip-js-minify | Bypasses JavaScript minification. Simulator builds are never minified. Only supported for Android and iOS. |
| \--log-level <level> | Minimum logging level. Supported options are **trace**, **debug**, **info**, **warn**, and **error**. |
| \-p, --platforms <platform> | Target build platform: Supported values are **android**, **ios**, and **windows**. (**iphone** and **ipad** are currently accepted as synonyms for **ios**.) |
| \-d, --project-dir <directory> | Directory containing the project, otherwise the current working directory is assumed. |
| \-s, --sdk <version> | Titanium SDK version to build with. If not specified, uses the configured default SDK. |

#### Android build options

| Option | Description |
| --- | --- |
| \-A, --android-sdk <path> | Path to the Android SDK. |
| \-C, --device-id <name> | Name of the device or emulator to install the application to. When --target is "device", then you can specify "all" to install the app to all connected devices. |
| \-D, --deploy-type <type> | Controls several settings such as optimization, encryption, and analytics. Type can be **development**, **test**, or **production**.<br /><br />When --target is "emulator", the deploy type defaults to **development**, but can be set to **test**.<br /><br />When --target is "device", the deploy type defaults to **test**, but can be set to **development**.<br /><br />When --target is "dist-playstore", the deploy type is **production** and cannot be overwritten.<br /><br />Note that **test** will minify and encrypt your JavaScript source code. Any JavaScript syntax errors, even files you are not using, will result in a build failure. |
| \-K, --keystore <path> | Location of the keystore file. |
| \--key-password <keypass> | Password of the keystore private key. Defaults to value specified with --store-password. |
| \--liveview | Starts a [LiveView](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Titanium_Development/LiveView/) session to let you quickly preview changes to your application's UI. **Requires Appcelerator Studio.** |
| \-L, --alias <alias> | Alias for the keystore. |
| \--no-launch | Disables launching the app after installing. |
| \-O, --output-dir <dir> | Output directory (used when target is **dist-playstore**). |
| \-P, --store-password <password> | Password for the keystore. |
| \--sigalg <algorithm> | The digital signature algorithm to sign the .apk with. Possible algorithms are **MD5withRSA**, **SHA1withRSA**, and **SHA256withRSA**. |
| \-T, --target <value> | Target to build for. Target can be **emulator**, **device**, or **dist-playstore**. |

#### iOS build options and flags

| Option | Description |
| --- | --- |
| \-C, --device-id <name> | Name of the device or emulator to install the application to. When --target is "device", then you can specify "all" to install the app to all connected devices. |
| \-D, --deploy-type <type> | Controls several settings such as optimization, encryption, and analytics. Type can be **development**, **test**, or **production**.<br /><br />When --target is "simulator", the deploy type defaults to **development**, but can be set to **test**.<br /><br />When --target is "device", the deploy type defaults to **test**, but can be set to **development**.<br /><br />When --target is "dist-appstore" or "dist-adhoc", the deploy type is **production** and cannot be overwritten.<br /><br />Note that **test** will minify and encrypt your JavaScript source code. Any JavaScript syntax errors, even files you are not using, will result in a build failure. |
| \--force-copy | Forces files to be copied instead of symlinked for simulator builds only. |
| \--force-copy-all | Identical to the --force-copy flag except this will also copy the 32.5 MB libTiCore.a file. **Removed since 8.0.0 and moving to the native JavaScriptCore library.** |
| \--launch-watch-app | Launch both the watch app and main app; only used when target is **simulator**. |
| \--launch-watch-app-only | Launch only the watch app; only used when target is **simulator**. |
| \--sim-focus | Focus the iOS simulator (default is true). To not focus the simulator, use --no-sim-focus. |
| \-V, --developer-name <name> | iOS Developer Certificate to use; required when target is **device**. |
| \-F, --device-family <value> | Device family to build for (**iphone**, **ipad**, or **universal**). Default is **universal**, however if --target is set to "ipad", then the value defaults to **ipad**. |
| \-I, --ios-version <value> | iOS SDK version to build for. Default: latest installed iOS SDK. |
| \-K, --keychain <value> | Path to the distribution keychain to use instead of the system default; only used when target is **device**, **dist-appstore**, or **dist-adhoc**. |
| \--launch-bundle-id <id> | After installing the app in the iOS Simulator, launch a different app instead of the app that was just built. Useful if you need to launch a test runner that in turn launches your app. |
| \-O, --output-dir <dir> | Output directory. Only used when target is **dist-adhoc**. |
| \-P, --pp-uuid <uuid> | Provisioning profile uuid; required when target is **device**, **dist-appstore**, or **dist-adhoc**. |
| \-R, --distribution-name <name> | iOS Distribution Certificate to use; required when target is **dist-appstore** or **dist-adhoc**. |
| \--sim-focus | Focus the iOS Simulator after launching. Defaults to **true**. |
| \-T, --target <value> | Target to build for: **simulator**, **device**, **dist-appstore**, or **dist-adhoc**. |
| \--watch-app-name <name> | Name of the watch app to launch; only used when target is **simulator**. |
| \-W, --watch-device-id <udid> | Watch simulator UDID to launch when building an app with a watch app; only used when target is **simulator**. |
| \-Y, --sim-type <type> | iOS Simulator type: **iphone** or **ipad**; only used when target is **simulator**. |

#### Windows build options

{{% alert title="❗️ Warning" color="danger" %}}As of Titanium 9.0.0, building Windows apps is no longer supported.{{% /alert %}}{{% alert title="❗️ Warning" color="danger" %}}Support for Windows 8.1 and Windows Phone SDKs has been deprecated as of SDK 6.3.0.GA and has be removed in SDK 7.0.0.GA.{{% /alert %}}

| Options | Description |
| --- | --- |
| \-C, --device-id <value> | UDID of the Windows Phone 8 device or emulator to build for. Only used when the target is **wp-emulator** or **wp-device**.<br /><br />Note: An app can only be installed to a single device at a time. |
| \-D, --deploy-type <type> | Type of deployment (**test**, **development** or **production**). Only used when the target is **wp-emulator**, **wp-device** or **ws-local**. |
| \-G, --wp-publisher-guid <GUID> | Windows Phone Publisher ID. Only used when the target is **wp-emulator**, **wp-device** or **dist-**phonestore****. |
| \-I, --win-publisher-id <ID> | Windows Publisher ID. Required to build the application. |
| \--wp-product-guid <GUID> | **Deprecated as of 6.1.0**. Windows 8 product ID, used for upgrading Win 8 apps to Win 8.1. Deprecated and will be removed in future version, use --win-product-guid instead. |
| \-H, --win-product-guid <GUID> | **Since Release 6.1.0**. Windows 10 product ID, used for upgrading Windows 8.1 apps to Windows 10. |
| \-O, --output-dir <dir> | Output directory. Only used when target is **dist-phonestore** or **dist-winstore**. |
| \--ws-cert <file> | **Deprecated as of Release 6.1.0**. Location of the Windows Store certificate file. Only used when target is **ws-local** or **dist-winstore**. Deprecated and will be removed in future version, use --win-cert instead. |
| \-R, --win-cert <file> | **Since Release 6.1.0**. Location of the Windows Store certificate file. Only used when target is **ws-local** or **dist-winstore**. |
| \--wp-sdk <version> | **Deprecated as of Release 6.1.0**. Windows Phone SDK version. Deprecated and will be removed in future version, use --win-sdk instead. |
| \-S, --win-sdk <version> | **Since Release 6.1.0**. Windows SDK version. When you run CLI on Windows 10, you can specify **10.0** to indicate building for Windows 10 _Universal Windows Platform_ (_UWP_) app. You can target more specific SDK version, such as **10.0.15063.0**. |
| \-V, --vs-target <version> | Visual Studio target to build for.<br /><br />* **12.0** to use Visual Studio 2013<br />    <br />* **14.0** to use Visual Studio 2015<br />    <br />* **Visual Studio Community 2017** to use Visual Studio Community 2017<br />    <br />* **Visual Studio Professional 2017** to use Visual Studio Professional 2017<br />    <br />* **Visual Studio Enterprise 2017** to use Visual Studio Enterprise 2017 |
| \-T, --target <value> | Target to build for:<br /><br />* **wp-emulator** to run a Windows Phone app on the emulator<br />    <br />* **wp-device** to run a Window Phone app on a device connected to your host machine<br />    <br />* **dist-**phonestore**** to pakcage a Windows Phone app<br />    <br />* **ws-local** to run a Windows Store app on your local machine<br />    <br />* **dist-winstore** to package a Windows Store app |
| \--skipInstallDependencies | **Since Release 6.1.0.** Skip installing dependency packages. If you had trouble with app deployment on device, try this option. |

### Search

Search for components in the registry.

```bash
appc search <QUERY_TERM> [options]
```

#### Search options

| Option | Description |
| --- | --- |
| \-f, --filter <FILTER> | Overwrite any existing projects. |

### Setup

Runs the setup wizard and checks your environment.

```bash
appc setup [options]
```

### Switch

**Since Release 5.0.0.** Switch organizations without logging in or out of the CLI.

```bash
appc switch <org> [options]
```

### Titanium | ti

Execute titanium commands. See the [Titanium Command-Line Interface Reference](/docs/appc/Titanium_SDK/Titanium_SDK_Guide/Titanium_Command-Line_Interface_Reference/) for more information.

```bash
appc ti <command> [options]
```

```bash
appc titanium <command> [options]
```

### Unpublish

Unpublish a project or component. The component name is only required if the project is run outside the project directory.

```bash
appc unpublish [options] [component]
```

#### Unpublish options

| Option | Description |
| --- | --- |
| \-d, --project-dir <projectDir> | Directory containing the project. |
| \-f, --force | Force unpublish. |

### Use

Selects the version of the CLI to use. Running the command with no options lists the available versions.

```bash
appc use [<add, remove, list>] [<user>] [<component>]
```

#### Use options

| Option | Description |
| --- | --- |
| \-d, --project-dir <projectDir> | Directory containing the project. |
| \-f, --force | Force unpublish. |

### User

Manage registry users for a component. Only applicable if the component access rights are set to either user or user\_or\_org.

```bash
appc user <add,remove,list>[ <user>][ <component>]
```

#### User examples

Remove a user:

```bash
$ appc user remove user@domain.org
```

Add a user:

```bash
$ appc user add newowner@email.com
```

### User commands

#### user add

Adds a user to a component.

```bash
appc user add <USERNAME> [<COMPONENT>]
```

#### user rm | remove

Removes a user from a component.

```bash
appc user rm <USERNAME> [<COMPONENT>]
```

### Whoami

Displays information about the currently logged-in user.

```bash
appc whoami [options]
```

#### Whoami options

| Option | Description |
| --- | --- |
| \-f, --full | Provides information about all the organizations, apps, etc. the user is a part of. |
| \-l, --log-level <level> | Change log level |
| \-o, --output <OUTPUT\_FORMAT> | Output format. Currently only json is supported. |
