{"title":"Studio Components","weight":"40"}

* [General Guidelines](#general-guidelines)

* [Editors](#editors)

* [Previewing/Servers](#previewing/servers)

* [Scripting](#scripting)

* [Miscellaneous](#miscellaneous)

* [Titanium](#titanium)

This document lists the various components (and the related scopes) inside Studio.

## General Guidelines

There are a few guidelines to observe when creating a new scope or using them in practice.

{{% alert title="⚠️ Warning" color="primary" %}}.\* for components indicate that there is a per-editor/language component associated, i.e. editor.js, scripting.rubles.js.{{% /alert %}}

* If it has a view in studio, it is a root-level scope (i.e. validation, terminal)

* Multi-word components have words separated by hyphens (i.e. content-assist)

* Per-language components are created on a as-needed basis in JIRA. Thus, there may not yet be a editor.navigation.js in JIRA. Thus, you can assign items to editor.navigation. When we get enough sub-issues, we can then break it apart.

## Editors

| Scope | Description |
| --- | --- |
| [call-hierarchy.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Call Hierarchy |
| [colorization.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Syntax colorization |
| [editor](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Cross-language editor functionality (infrastructure) |
| [editor.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | auto-indentation, pair matching, double/triple clicks, pair highlighting, branding/icons, templates, browsing perspective |
| [editor.content-assist](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Cross-language editor content assist functionality (infrastructure) |
| [editor.content-assist.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Core/Global, User-defined, Libraries/references, Hippie Completion |
| [editor.documentation.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Language-specific version of JavaDocs |
| [editor.folding.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | language folding |
| [editor.hover.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Item Documentation, Value Visualizers (i.e. color preview of RGB CSS value), Debugging hovers, Source of referenced item |
| [editor.navigation.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Go To Declaration, Find References, Open Type, Editor hyperlink |
| [editor.occurences.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | text-based, semantic mark occurences |
| [formatting.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | language formatting |
| [outline.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Outline, Quick Outline |
| [problems.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Problem description from validation |
| [problems.parsing.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Parse Errors |
| [problems.spelling.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Spell Checking |
| [problems.style.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Style/Usage Validation |
| [problems.quick-fixes.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Quick Fixes |
| [tasks.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Task Markers (TODO, FIXME, XXX) |
| [type-hierarchy.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Type Hierarchy |

## Previewing/Servers

| Scope | Description |
| --- | --- |
| [preview](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | [Previewing](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/Previewing/) core infrastructure |
| [preview.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Language/editor-specific previewing issues |

## Scripting

| Scope | Description |
| --- | --- |
| [scripting](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | The core java and jruby support that implements the ruble framework |
| [scripting.rubles](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Scripting extensions to Studio |
| [scripting.rubles.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Ruble snippets and commands for particular languages |

## Miscellaneous

| Scope | Description |
| --- | --- |
| [app-explorer](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | The App Explorer view |
| [build](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Anything having to do with hudson or configuring the build server |
| [debugging](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | The core debugger functionality |
| [debugging.js](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Support for debugging JavaScript on various devices |
| [debugging.php](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Support for debugging PHP applications |
| [debugging.ruby](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Support for debugging Ruby applications |
| [deployment](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | The deployment and packaging system. Synchronization, upload, etc. |
| [deployment.ftp](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | FTP support |
| [deployment.ftps](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | FTPS support |
| [deployment.sftp](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | SFTP support |
| [file.wizard](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | The infrastructure for creating new files |
| [file.wizard.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Language/editor file creation wizards |
| [installer](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Anything having to do with the installation process |
| [project-explorer](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | The project explorer view |
| [project.wizard](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | The infrastructure for creating new projects |
| [project.wizard.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Language/editor project creation wizards |
| [source-control.git](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Git support |
| [source-control.svn](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | SVN support |
| [terminal](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | The terminal window |
| [theme](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Theming support inside Studio |
| [update](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Anything having to do with updating Titanium Studio |

## Titanium

| Scope | Description |
| --- | --- |
| [analytics](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Cloud analytics |
| [debugging.android](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Debugging on Android |
| [debugging.ios](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Debugging on iOS |
| [platform.android](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Android platform support |
| [platform.ios](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | iOS platform support |
| [platform.mobileweb](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | html5 output platform support |
| [sdk](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component=) | Updating and installation of the Titanium SDKs inside Titanium Studio |
