{"title":"AMPLIFY CLI","weight":"120"}

* [Extensions](#extensions)

* [Requirements](#requirements)

* [Installation](#installation)

* [Next steps](#next-steps)

The AMPLIFY Command Line Interface (ACLI) is a unified command line interface provides a single entry-point for multiple external CLI's and the Axway AMPLIFY platform. External CLI's are registered with the ACLI (via a config file) and are responsible for all application logic.

With the ACLI, you can:

* Install and manage additional Axway command line programs

* Authenticate against the Axway platform

* Configure your local AMPLIFY development settings

* Automate AMPLIFY CLI commands from other scripting languages

* Apply authentication credentials per command

![AMPLIFY_CLI](/Images/appc/download/attachments/58726425/AMPLIFY_CLI.png)

## Extensions

ACLI, aside from many other features, provides a main entry point for invoking other local CLI programs. These other CLIs are called extensions. Extension CLIs can be a npm package, a single Node.js file, or a native executable.

With the exception of [cli-kit](https://github.com/cb1kenobi/cli-kit) enabled CLIs, all extension CLIs are run as subprocesses and the AMPLIFY CLI banner is suppressed. The only indication an extension CLI has that it's being run by the AMPLIFY CLI is the AMPLIFY\_CLI environment variable containing the AMPLIFY CLI's version.

cli-kit enabled CLIs are directly loaded via require() and the exported CLI structure is merged with the parent CLI command context tree. This promotes efficient reuse parser state and provides a seamless user experience.

If an extension is a npm package, the AMPLIFY CLI will automatically invoke it using the Node.js executable. Specifying the extension as node /path/to/script.js will treat the extension as a native executable.

## Requirements

| Component | Version |
| --- | --- |
| [Node.js](https://nodejs.org/en/) | 8.10.0 or later |
| [npm](https://www.npmjs.com/) | 6.6.0 or later |

## Installation

To install AMPLIFY CLI (ACLI), execute this command: \[sudo\] npm i -g @axway/amplify-cli

If you get error message, see [AMPLIFY CLI Error Messages During Installation](/docs/appc/AMPLIFY_CLI/AMPLIFY_CLI_Error_Messages_During_Installation/) for details and troubleshooting

## Next steps

You can learn more about ACLI by reading the following documents:

* [AMPLIFY CLI Quick Start](/docs/appc/AMPLIFY_CLI/AMPLIFY_CLI_Quick_Start/)

* [AMPLIFY CLI Commands](/docs/appc/AMPLIFY_CLI/AMPLIFY_CLI_Commands/)

* [AMPLIFY CLI Error Messages During Installation](/docs/appc/AMPLIFY_CLI/AMPLIFY_CLI_Error_Messages_During_Installation/)

Last Modified: Jul 23, 2019 10:54
