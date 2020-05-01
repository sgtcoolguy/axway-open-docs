{"title":"PyLint can be used with PyDev","weight":"180"}

{{% alert title="⚠️ Warning" color="primary" %}}[PyLint](http://www.logilab.org/projects/pylint) is **disabled by default**, so, if you want to activate it, you should go to the pylint preferences page, **specify its location** (it MUST be installed in the site-packages) and activate it (after activating it, you can clean your project on the project menu so that the files are checked with pylint, or you can do it on deltas as you go and change your files).{{% /alert %}}

![pylint_prefs](/Images/appc/pydev.org/images/pylint/pylint_prefs.png)
Well, moving on: The integration is done so that it is integrated with the eclipse builder. That means that whenever you change a file, it automatically passes pylint (if auto-build is on – check the menu Project > Build Automatically. If it is not, you can request a build when you want with Ctrl+B, so that the deltas are analyzed).

This, however, has a drawback: PyLint can be slow at sometimes, and if you work in big projects, it can be kind of slow (anyway, you can stop the builder process at any time if you want) - you should expect that it takes some secs. For each file, it analyzes, so, if you are working with about 700 files - like I am - it can take a long time - more than 40 minutes to get all the info on the project...

For these cases, I have provided an option on the maximum delta to use PyLint on. So, if you have all of the sudden 100 changed files because of a CVS update, PyLint will not be run unless the limit you specify allows it.

Oh, if you don't see the problems with your problems view, don't forget to enable it in the problems view filter.

![pylint](/Images/appc/pydev.org/images/pylint/pylint.png)
