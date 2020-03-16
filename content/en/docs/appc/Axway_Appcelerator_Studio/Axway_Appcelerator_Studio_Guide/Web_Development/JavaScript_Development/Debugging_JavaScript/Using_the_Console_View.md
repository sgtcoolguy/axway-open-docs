{"title":"Using the Console View","weight":"120"}

* [Introduction](#introduction)

* [Instructions](#instructions)

    * [Adding a new log message to the Console View](#adding-a-new-log-message-to-the-console-view)

    * [Adding other log messages](#adding-other-log-messages)

* [Related Topics](#related-topics)

## Introduction

Use the Console View (shown below) to find out the value of a variable or object at a given time. The value will be written out to the Console.

![ConsoleView](/Images/appc/download/attachments/30083112/ConsoleView.png)

## Instructions

This section describes how to do common logging tasks.

### Adding a new log message to the Console View

You will need to have the debugger set up to run to use the Console View. See [Running the debugger](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/JavaScript_Development/Debugging_JavaScript/Running_the_debugger/) for help.

To add a new log message to the Console View:

1. Open your file in the appropriate HTML or JavaScript Editor.

2. Navigate to the function or place in your code where you want to add the log message.

3. Add the following line of code to your code:

    `aptana.log(``''``logMessage``''``);`

    _logMessage_ should be the message that you want to be printed out to the Console View. (e.g.

    `aptana.log(``"Now is "` `+ tDate);`

4. Click the **Debug** button ![IconDebug1](/Images/appc/download/attachments/30083112/IconDebug1.png) to run/debug your code in your browser.

The log entry that you added will print out to the Console View as it is executed.
Click the **Terminate** button ![IconTerminate](/Images/appc/download/attachments/30083112/IconTerminate.png) to stop the execution of your code.

### Adding other log messages

**window.dump()**

In addition to the aptana.log, you can also use the **window.dump()** command to print out to the console. The **window.dump()** command is compatible with many currently popular JavaScript toolkits.

**aptana.trace()**

Use the **aptana.trace()** command to generate a stack trace in the Console.

## Related Topics

* [About the Debug perspective](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/JavaScript_Development/Debugging_JavaScript/About_the_Debug_perspective/)

* [Installing the JavaScript debugger](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/JavaScript_Development/Debugging_JavaScript/Installing_the_JavaScript_debugger/)

* [Running the debugger](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/JavaScript_Development/Debugging_JavaScript/Running_the_debugger/)

* [Stepping into and over functions](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/JavaScript_Development/Debugging_JavaScript/Stepping_into_and_over_functions/)

* [Adding a breakpoint](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/JavaScript_Development/Debugging_JavaScript/Adding_a_breakpoint/)
