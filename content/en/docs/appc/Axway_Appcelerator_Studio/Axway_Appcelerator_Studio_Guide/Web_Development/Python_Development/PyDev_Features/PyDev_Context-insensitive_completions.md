{"title":"PyDev Context-insensitive completions","weight":"50"} 

The 'context-insensitive' code completion brings up completions with tokens found it the pythonpath and automatically imports the module that contains that token when selected.

It is shown only when the completion is requested for the globals and 3 characteres are already typed.

You need to request the completions to show with **Ctrl+Space.**

![complnoctx](/Images/appc/pydev.org/images/completion/complnoctx.png)

**Image:** All the tokens that start with 'xml' in the pythonpath

![complnoctx2](/Images/appc/pydev.org/images/completion/complnoctx2.png)

**Image:** Result of selecting the 'XMLFilterBase' token