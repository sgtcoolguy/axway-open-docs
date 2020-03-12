{"title":"Studio Components","weight":"40"} 

*   [General Guidelines](#GeneralGuidelines)
    
*   [Editors](#Editors)
    
*   [Previewing/Servers](#Previewing/Servers)
    
*   [Scripting](#Scripting)
    
*   [Miscellaneous](#Miscellaneous)
    
*   [Titanium](#Titanium)
    

This document lists the various components (and the related scopes) inside Studio.

## General Guidelines

There are a few guidelines to observe when creating a new scope or using them in practice.

.\* for components indicate that there is a per-editor/language component associated, i.e. editor.js, scripting.rubles.js.

*   If it has a view in studio, it is a root-level scope (i.e. validation, terminal)
    
*   Multi-word components have words separated by hyphens (i.e. content-assist)
    
*   Per-language components are created on a as-needed basis in JIRA. Thus, there may not yet be a editor.navigation.js in JIRA. Thus, you can assign items to editor.navigation. When we get enough sub-issues, we can then break it apart.
    

## Editors

Scope

Description

[call-hierarchy.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="call-hierarchy")

Call Hierarchy

[colorization.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="colorization")

Syntax colorization

[editor](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="editor")

Cross-language editor functionality (infrastructure)

[editor.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="editor")

auto-indentation, pair matching, double/triple clicks, pair highlighting, branding/icons, templates, browsing perspective

[editor.content-assist](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="content-assist")

Cross-language editor content assist functionality (infrastructure)

[editor.content-assist.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="content-assist")

Core/Global, User-defined, Libraries/references, Hippie Completion

[editor.documentation.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="documentation")

Language-specific version of JavaDocs

[editor.folding.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="folding")

language folding

[editor.hover.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="hover")

Item Documentation, Value Visualizers (i.e. color preview of RGB CSS value), Debugging hovers, Source of referenced item

[editor.navigation.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="navigation")

Go To Declaration, Find References, Open Type, Editor hyperlink

[editor.occurences.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="editor")

text-based, semantic mark occurences

[formatting.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="formatting")

language formatting

[outline.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="outline")

Outline, Quick Outline

[problems.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="problems")

Problem description from validation

[problems.parsing.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="problems")

Parse Errors

[problems.spelling.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="problems")

Spell Checking

[problems.style.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="problems")

Style/Usage Validation

[problems.quick-fixes.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="problems")

Quick Fixes

[tasks.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="tasks")

Task Markers (TODO, FIXME, XXX)

[type-hierarchy.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="type-hierarchy")

Type Hierarchy

## Previewing/Servers

Scope

Description

[preview](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="preview")

[Previewing](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Web_Development/Previewing/) core infrastructure

[preview.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="preview")

Language/editor-specific previewing issues

## Scripting

Scope

Description

[scripting](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="scripting")

The core java and jruby support that implements the ruble framework

[scripting.rubles](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="scripting")

Scripting extensions to Studio

[scripting.rubles.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="scripting")

Ruble snippets and commands for particular languages

## Miscellaneous

Scope

Description

[app-explorer](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="app-explorer")

The App Explorer view

[build](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="build")

Anything having to do with hudson or configuring the build server

[debugging](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="debugging")

The core debugger functionality

[debugging.js](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="debugging")

Support for debugging JavaScript on various devices

[debugging.php](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="debugging")

Support for debugging PHP applications

[debugging.ruby](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="debugging")

Support for debugging Ruby applications

[deployment](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="deployment")

The deployment and packaging system. Synchronization, upload, etc.

[deployment.ftp](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="deployment")

FTP support

[deployment.ftps](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="deployment")

FTPS support

[deployment.sftp](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="deployment")

SFTP support

[file.wizard](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="file")

The infrastructure for creating new files

[file.wizard.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="file")

Language/editor file creation wizards

[installer](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="installer")

Anything having to do with the installation process

[project-explorer](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="project-explorer")

The project explorer view

[project.wizard](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="project")

The infrastructure for creating new projects

[project.wizard.\*](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="project")

Language/editor project creation wizards

[source-control.git](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="source-control.git")

Git support

[source-control.svn](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="source-control.svn")

SVN support

[terminal](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="terminal")

The terminal window

[theme](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="theme")

Theming support inside Studio

[update](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="update")

Anything having to do with updating Titanium Studio

## Titanium

Scope

Description

[analytics](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="analytics")

Cloud analytics

[debugging.android](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="debugging")

Debugging on Android

[debugging.ios](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="debugging")

Debugging on iOS

[platform.android](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="android")

Android platform support

[platform.ios](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="ios")

iOS platform support

[platform.mobileweb](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="mobileweb")

html5 output platform support

[sdk](http://jira.appcelerator.org/secure/IssueNavigator!executeAdvanced.jspa?jqlQuery=component="sdk")

Updating and installation of the Titanium SDKs inside Titanium Studio