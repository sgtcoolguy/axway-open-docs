{"title":"PyDev Context-sensitive completions","weight":"60"} 

## Code Completion

### Requesting Code Completion

Code completion provides context-sensitive completions and is enabled with **Ctrl+Space**. (Note that eclipse has simple emacs-style text-completion with **Alt+/**).

It's important to note that your interpreter must be properly configured for the code-completion to work, and for getting the **builtins**, PyDev spawns a shell, so, having a **firewall can prevent the code-completion from working** if it's blocking the communication from eclipse to that shell.

## Preferences

If you want to configure something, you have to go to **window > preferences > PyDev > Editor > Code Completion**.

![codecompletionpreferences](/Images/appc/pydev.org/images/codecompletion/codecompletionpreferences.png)

## Snapshots

Completing on a variable on the class (also works for locals) that are defined in the same scope we are.

![codecompletionattr1](/Images/appc/pydev.org/images/codecompletion/codecompletionattr1.png)

Getting the builtins.

![codecompletionbuiltins](/Images/appc/pydev.org/images/codecompletion/codecompletionbuiltins.png)

Completing on a class (note that we get the hierarchy even from builtins).

![codecompletionhierarchy1](/Images/appc/pydev.org/images/codecompletion/codecompletionhierarchy1.png)

## Completing for making an import (goes for PYTHONPATH)

![compl2](/Images/appc/pydev.org/images/codecompletion/compl2.png)

## Completing on an import

![compl3](/Images/appc/pydev.org/images/codecompletion/compl3.png)

## Completing for global tokens (handles wild-imports, local imports, local variables, etc.)

![compl4](/Images/appc/pydev.org/images/codecompletion/compl4.png)