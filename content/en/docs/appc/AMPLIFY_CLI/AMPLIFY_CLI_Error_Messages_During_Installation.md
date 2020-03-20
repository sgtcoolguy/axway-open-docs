{"title":"AMPLIFY CLI Error Messages During Installation","weight":"30"}

At some point, you may experience error message during installation of one or more modules. This document aims to assist in those problems.

* [Permission denied to mkdir](#permission-denied-to-mkdir)

* [Install failure with npm install](#install-failure-with-npm-install)

* [Keytar failed to install](#keytar-failed-to-install)

## Permission denied to mkdir

If you are using ACLI 1.1.0 and earlier, then you may encounter this issue. Later versions shouldn't have this problem.

If you installed ACLI and did not have any issues with permissions, you may see the "Secure token store is not available" error message when any amplify auth login commands are issued.

If you get an error message about permission being denied to create a directory (see below), you'll need to add the \--unsafe-perm=true flag to the above command.

```
gyp ERR! stack Error: EACCES: permission denied, mkdir '/Users/<user>/<install dir>/node_modules/keytar/build'
...
```

or

```
prebuild-install WARN install EACCES: permission denied, access '/Users/<user>/.npm'
gyp ERR! configure error
gyp ERR! stack Error: EACCES: permission denied, mkdir '/usr/local/lib/node_modules/@axway/amplify-cli/node_modules/keytar/build'
...
```

## Install failure with npm install

If you encounter the following error message (this is not an error on npm's side but rather ACLI's package manager),

```bash
An error occurred when running "npm install"
Error: Subprocess exited with code 243
    at ChildProcess.child.on.code (/Users/<user>/.npm-global/lib/node_modules/@axway/amplify-cli/node_modules/appcd-subprocess/dist/subprocess.js:63:17)
    at ChildProcess.emit (events.js:182:13)
    at maybeClose (internal/child_process.js:962:16)
    at Socket.stream.socket.on (internal/child_process.js:381:11)
    at Socket.emit (events.js:182:13)
    at Pipe._handle.close (net.js:606:12)
```

Confirm that the package you're trying to install didn't fail to install.

1. Open a terminal in ~/.axway/packages.

2. Look through this directory for any empty directories.

3. Remove any empty directories.

4. Try installing the package again.

## Keytar failed to install

If you are using ACLI 1.1.0 and earlier, then you may encounter this issue. Later versions shouldn't have this problem.

If you encounter this error when trying, amplify auth login -u <user> -p <password>

```bash
Secure token store is not available.
Please reinstall the AMPLIFY CLI by running:
npm i -g --unsafe-perm @axway/amplify-cli
```

It's likely that keytar failed to install during the installation of ACLI. To fix this issue,

1. Uninstall ACLI: npm uninstall amplify -g

2. Re-install ACLI using the \--unsafe-perm flag: \[sudo\] npm i -g --unsafe-perm @axway/amplify-cli

3. Try logging in again.

If you do not wish to install keytar, you can disable secure store and fallback to the file-based store by executing this command: amplify config set auth.tokenStoreType file.
