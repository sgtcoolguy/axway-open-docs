{"title":"TASKS","weight":"230"} 

## My tasks are not being updated!

The most common problem for tasks not being updated is that your files are not under your PYTHONPATH (that's right, the only analyzed files are the ones that are under your project PYTHONPATH – check how to configure it under the [PyDev Getting Started](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/Python_Development/PyDev_Getting_Started/))

## Where can I configure which comments should appear as tasks?

The TODO's can be configured in the tasks preferences page, so, fell free to use as many task tags (separated by spaces) as you want...

![tasks](/Images/appc/pydev.org/images/tasks/tasks.png)

## Where can I see the available tasks?

The tasks should appear in the tasks view, so, you can check it.

![tasks2](/Images/appc/pydev.org/images/tasks/tasks2.png)

## My project is correctly configured, why are my tasks still not appearing?

The tasks are based on the builder, so, if you don't use the autobuild, you have to make the manual build (Ctrl+B) once in a while to get the tasks updated (in fact, the auto-build affects lots of things, such as code-completion, code analysis, etc, so, you're reccommended to keep it on)  
![tasks3](/Images/appc/pydev.org/images/tasks/tasks3.png)