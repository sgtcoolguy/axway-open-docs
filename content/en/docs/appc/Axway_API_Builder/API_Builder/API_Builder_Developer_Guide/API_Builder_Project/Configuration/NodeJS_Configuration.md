{"title":"NodeJS Configuration","weight":"20"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

* [Dependencies](#Dependencies)

* [Engines](#Engines)

* [Health check](#Healthcheck)

* [Main](#Main)

* [Name](#Name)

* [npmAuthentication](#npmAuthentication)

* [npmRegistry](#npmRegistry)

* [Scripts](#Scripts)

  * [Preinstall and post-install](#Preinstallandpost-install)

  * [Start](#Start)

* [Version](#Version)


An API Builder application contains a file called package.json located in the root directory of the project. AMPLIFY Runtime Services uses the package.json file to configure settings and install dependencies for the application.

Important fields for API Builder applications are defined below.

## Dependencies

The application can import any third-party modules that are supported by standard Node.js applications. Before publishing the app to the cloud, make sure all dependencies are listed in the dependencies field in the application's package.json file. For example, to add support for MongoDB 1.2.0 or greater:

`{`

`"dependencies"``:{` `"mongodb"``:` `">1.2.0"` `}`

`}`

## Engines

You can specify which version of Node.js to run your application on. Use the engines field in the package.json file to specify engine versions. To specify the Node.js version, set the node key in the engines dictionary to the specific version of Node.js to use. For example, to specify to use version 0.10.22:

`{`

`"engines"` `: {` `"node"``:` `"0.10.22"` `}`

`}`

You may specify any version of Node.js. Node.js 0.8.26, 0.10.22 and 0.12.4 are built in, but other versions will be downloaded from [https://nodejs.org/](https://nodejs.org/) when the application is built prior to running npm install. If you do not specify a Node.js version, the application will use 0.12.4 by default.

Deprecated Behavior

Prior to AMPLIFY Runtime Services 1.2.0, if this field is undefined when you publish your application, the application will use 0.10.22 by default.

If this field is undefined when you republish your application and the latest supported Node.js version changed on the AMPLIFY Runtime Services servers, you will receive an error message when trying to publish your application. You must set the Node.js version to republish your application.

## Health check

Starting with AMPLIFY Runtime Services 1.2.0, you may define a health-check endpoint called arrowPing.json that returns a 200 HTTP code. To let AMPLIFY Runtime Services know you defined the health-check endpoint, set the healthCheck field to true. For an example, see [API Builder Project](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/).

`{`

`healthCheck:` `true`

`}`

By default, the health check starts after a two minute wait period. If your application normally takes longer than two minutes to start up, you should set the start\_period environment variable to an appropriate startup time (in minutes) to avoid having the docker swarm restart your application before it is online.

## Main

AMPLIFY Runtime Services uses the main field in the package.json file to determine the application's main entry point. Set this field to a JavaScript file. AMPLIFY Runtime Services loads and runs this file first.

By default, the main field is set to the app.js file located in the project's root folder:

`{`

`"main"``:` `"app.js"`

`}`

You can load a module by leaving this field blank and specifying the scripts field.

## Name

Use the name field to specify the name of the application. An app's name must be unique across all apps of a user or organization. It will be used to ID the app when publishing/unpublishing to the cloud or setting up the app through CLI commands.

By default, this field is set to the name of the project when it was created.

`{`

`"name"``:` `"MyArrowApp"`

`}`

## npmAuthentication

To enable authenticated package installs from a private npm registry specified by [npmRegistry](#undefined), add the npmAuthentication field in your application's package.json file and set it to true:

`{`

`"npmAuthentication"``:` `true`

`}`

When enabled, you must provide login credentials for the npm registry when calling appc acs publish . You can provide the credentials on the command line when calling the publish command:

`$ appc cloud publish myuser mypwd`

If acs cli complains that npm is not found even though npm is in the path, ensure that the directory containing npm is in the NODE\_PATH (for example, NODE\_PATH=/usr/lib/node\_modules).

If no credentials are provided on the command line, the Appcelerator CLI will attempt to read the credentials from ~/.npmrc. If no ~/.npmrc file is found, or it does not contain any credentials, you are prompted for the npm username and password:

`$ appc cloud publish`

`npm username: admin`

`npm password: ***********`

`Preparing application` `for` `publish...` `done`

If you use a private npm registry hosted by Nodejitsu, you must first synchronize your public npm user account with the private npm, otherwise you will get an "unauthorized" error. To do this, enter the following npm commands:

`$ npm config` `set` `strict-ssl` `true`

`$ npm config` `set` `ca` `""`

`$ npm config` `set` `registry https:``//``<your-subdomain>.registry.nodejitsu.com`

`$ npm login`

See [https://www.nodejitsu.com/documentation/npm/cli/](https://www.nodejitsu.com/documentation/npm/cli/) for more information.

## npmRegistry

If you want to use a different npm registry besides the official public npm registry to install dependencies, add the npmRegistry field to the package.json file and set the value to the registry URL you want to use. For example, the entry below uses a European npm mirror:

`{`

`"npmRegistry"` `:` `"http://registry.npmjs.eu/"`

`}`

To require authentication for npm installs, add the npmAuthentication field to your package.json file.

## Scripts

### Preinstall and post-install

Specifies a path to a script to execute before or after the application is built. You can use the script to install custom binaries in the project folder.

`{`

`scripts: {`

`preinstall:` `'scripts/pre.sh'``,`

`postinstall:` `'scripts/post.sh'`

`}`

`}`

Prior to AMPLIFY Runtime Services 1.3.0, you could also use the script to install custom binaries outside the project directory.

Do not name the script install.sh, located in the root folder of the project. The name is reserved to specify a script to install binaries to the container.

### Start

If your application's package.json file does not specify a main field, Appcelerator Cloud will now look at the scripts.start field in the package.json file to determine the main module to launch. Appcelerator Cloud will execute the start script using npm start.

For example, to launch the foo module:

`{`

`"scripts"``: {` `"start"``:` `"foo"` `}`

`}`

## Version

The version of the application. Used to version the application.

By default, this field is set to 1.0.0:

`{`

`"version"``:` `"1.0.0"`

`}`
