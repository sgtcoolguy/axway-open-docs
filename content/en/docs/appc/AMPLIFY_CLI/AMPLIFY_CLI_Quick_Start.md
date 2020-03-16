{"title":"AMPLIFY CLI Quick Start","weight":"10"}

* [Quick start](#quick-start)

* [Installation](#installation)

* [Finding ACLI's commands](#finding-acli's-commands)

* [Authentication](#authentication)

    * [Logging in](#logging-in)

* [Managing packages](#managing-packages)

    * [Searching for packages](#searching-for-packages)

    * [Installing a package](#installing-a-package)

    * [Using select versions](#using-select-versions)

    * [Updating packages](#updating-packages)

    * [Starting a packageIn some cases, a package has a start option. The command would look something like this: amplify <product> start](#starting-a-packagein-some-cases,-a-package-has-a-start-option.-the-command-would-look-something-like-this:-amplify-<product>-start)

    * [Purging unused versions](#purging-unused-versions)

    * [Uninstalling a package](#uninstalling-a-package)

## Quick start

This document will cover some basic concepts for using AMPLIFY CLI (ACLI).

## Installation

To install AMPLIFY CLI (ACLI), execute this command: \[sudo\] npm i -g @axway/amplify-cli

If you get error message, see [AMPLIFY CLI Error Messages During Installation](/docs/appc/AMPLIFY_CLI/AMPLIFY_CLI_Error_Messages_During_Installation/) for details and troubleshooting

## Finding ACLI's commands

To see a list of ACLI's commands, execute this command: amplify

From there, you can drill down to ACLI's commands and their usage.

## Authentication

### Logging in

amplify auth login

## Managing packages

### Searching for packages

To search for an AMPLIFY package, use this command: amplify pm search

You should see something like this in your terminal:

`NAME | VERSION | TYPE | DESCRIPTION`

`...`

`@axway``/amplify-builder-cli` `| 0.0.9 | amplify-cli-plugin | Manage API Builder Standalone projects`

`appc.arrowdb | 1.1.1 | apib-data-connector | This is an API Builder connector` `for` `ArrowDB.`

`| | | Instructions` `for` `installation from CLI provided`

`| | |` `in` `the Product Website's readme. Start`

`| | | creating API's today` `for`  `free` `with Axway API`

`| | | Builder http:``//platform``.axway.com`

`appcd | 2.0.1 | amplify-cli-plugin | A daemon that powers Appcelerator tooling and`

`| | | makes the impossible possible.`

`...`

### Installing a package

Now that you have some ideas on which packages that can be installed via the ACLI, let's install the Appc Daemon. Execute this command: amplify pm install appcd

### Using select versions

Now let's suppose that you want to use a select version of the Appc Daemon.

1. Execute this command to get a list of the different versions available for a package: amplify pm view <package> versions. For the Appc Daemon, let's execute this command: amplify pm view appcd versions

2. Before using a select version of a package, we need to install it using a command like this: amplify pm install <package>@#.#.#. In this case, we want to install the 1.1.3 version of the Appc Daemon: amplify pm install appcd@1.1.3. Installing a version should automatically set it to an active version. If it doesn't, follow step #3.

3. To active a select version, use this command: amplify pm use <package>@#.#.#. To active the Appc Daemon to version 1.1.3, use this command: amplify pm use appcd@1.1.3

### Updating packages

To update a package, use this command: amplify pm update <package>

Continuing on with our Appc Daemon example, lets try to update it using this command: amplify pm update appcd

### Starting a packageIn some cases, a package has a start option. The command would look something like this: amplify <product> start

In the case of the Appc Daemon, use this command to start it: amplify appcd start

### Purging unused versions

To purge all unused versions of a package, use this command: amplify pm purge <package>

To purge unused versions of Appc Daemon, use this command: amplify pm purge appcd

### Uninstalling a package

To remove a specific package via ACLI, use this command: amplify pm uninstall <package>

To remove the Appc Daemon, use this command: amplify pm uninstall appcd
