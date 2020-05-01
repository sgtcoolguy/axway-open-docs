{"title":"Titanium Angular Getting Started Guide","weight":"10"}

* [Creating Angular projects](#creating-angular-projects)

* [Running Angular projects](#running-angular-projects)

* [Appendix and tips](#appendix-and-tips)

    * [Selecting a code editor](#selecting-a-code-editor)

## Creating Angular projects

With the latest nightly builds of Titanium SDK installed you have the option to create projects using the new Angular project template. Open your terminal and run the following command to create a new project that uses the Angular template:

*Create a new Angular project*

```bash
appc new -t app --ng
```

With the \--ng option, you instruct the Appc CLI to use the Angular template when creating the new project. You can use all other available options to customize the creation of your new project (see the [Command-Line Interface Reference](/docs/appc/Appcelerator_CLI/Appcelerator_CLI_How-tos/Appcelerator_Command-Line_Interface_Reference/#LineInterfaceReference-New)).

## Running Angular projects

To build and run your Angular based project, use the following command as usual (from your project root directory):

*Build and run Angular project*

```bash
appc run -p [android|ios]
```

There are no extra steps you need to do to build and run an Angular enabled project. Compilation of the TypeScript source and bundling is automatically done during Titaniums build steps.

*Titanium Angular debug output*

You might notice a lot of additional debug information during the build and while the app is running. Since Titanium Angular is still under active development we make extensive use of logging. The number of messages should decline in later Preview versions. A lot of it is already limited to debug and trace log levels (which you may enable by appending \-l debug or \-l trace to the appc run command).

## Appendix and tips

### Selecting a code editor

You can develop a Titanium Angular project in any code editor you like. Edit your app's source files and run the above command to build and run your Angular project and you are good to go. However, we recommend you to use an editor which makes use of TypeScripts additional type information. For example, take a look at [Visual Studio Code](https://code.visualstudio.com/) which is a fast and extendible editor with excellent TypeScript support backed by Microsoft.

Another good alternative is [Atom](https://atom.io/) with the [appcelerator-titanium](https://atom.io/packages/appcelerator-titanium) and [TypeScript](https://atom.io/packages/atom-typescript) packages.
