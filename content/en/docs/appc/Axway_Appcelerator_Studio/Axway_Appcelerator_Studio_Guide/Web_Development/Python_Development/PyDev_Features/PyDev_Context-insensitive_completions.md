{"title":"PyDev Context-insensitive completions","weight":"50"}

The 'context-insensitive' code completion brings up completions with tokens found it the python path and automatically imports the module that contains that token when selected.

It is shown only when the completion is requested for the globals, and three characters are already typed.

{{% alert title="⚠️ Warning" color="primary" %}}You need to request the completions to show with **Ctrl+Space.**{{% /alert %}}

![complnoctx](/Images/appc/pydev.org/images/completion/complnoctx.png)

**Image:** All the tokens that start with 'xml' in the python path

![complnoctx2](/Images/appc/pydev.org/images/completion/complnoctx2.png)

**Image:** Result of selecting the 'XMLFilterBase' token
