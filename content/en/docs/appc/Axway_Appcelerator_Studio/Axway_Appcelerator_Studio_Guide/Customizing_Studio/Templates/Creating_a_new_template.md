{"title":"Creating a new template","weight":"20"}

* [Overview](#Overview)

* [Creating a new file template](#Creatinganewfiletemplate)

* [Creating a new project template](#Creatinganewprojecttemplate)

  * [Project types](#Projecttypes)

  * [Local content](#Localcontent)

  * [Remote content](#Remotecontent)

  * [Template variables](#Templatevariables)


## Overview

Users can create new templates or modify existing templates to allow easy creation of default content.

We assume you've [created a new Ruble](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Customizing_Studio/Rubles/Creating_a_new_Ruble/) as a placeholder for the following content.

## Creating a new file template

New file templates are templates that show up after a user has entered a file name and has clicked the **Next** button:

![Screen_shot_2011-04-05_at_8.56.37_AM](/Images/appc/download/attachments/30083254/Screen_shot_2011-04-05_at_8.56.37_AM.png)

1. Open the existing bundle.rb file

2. Add the following content to the bottom of the file:

  `template` `"Sample File Template"`  `do` `|t|`

  `t.filetype =` `"*.txt"`

  `t.location =` `"templates/sample.txt"`

  `end`

3. Replace the "sample" and "txt" values with values appropriate to your filetype.

4. Create a templates folder underneath the _rublename_.ruble folder.

5. Drop-in file sample.txt (or the specific file you have created).

6. Save and close bundle.rb.


If you now go to **File > New > File...** and create a file name of the appropriate extension above, you should see your template in the list.

## Creating a new project template

New project templates are templates that show up after a user has entered a project name and has clicked the **Next** button:

![Screen_shot_2011-04-05_at_9.02.07_AM](/Images/appc/download/attachments/30083254/Screen_shot_2011-04-05_at_9.02.07_AM.png)

You can create project templates that reference a local .zip file or retrieve content from the web.

### Project types

Project templates can be added to existing project wizards by the specification of the "type" element:

Type

Project

all

All project types

ruby

Ruby projects

php

PHP projects

web

Web projects

python

Python projects

titanium\_desktop

Titanium Desktop projects

titanium\_mobile

Titanium Mobile projects

### Local content

If your content is hosted locally, you can reference a .zip file containing the files in question.

1. Create a templates directory in the bundle and add a project\_templates.rb file in the templates directory.

2. Add the following content to the project\_templates.rb file:

  `require` `'ruble'`

  `project_template` `"Sample Project Template"`  `do` `|t|`

  `t.type = :web`

  `t.location =` `"templates/sample_project.zip"`

  `t.description =` `"A sample project template"`

  `t.icon =` `"template.png"`  `// Ideally a ruble-relative path to a 48x48px icon. Could also be a URL to a remote file`

  `t.tags = [``'Titanium Classic'``]`

  `end`

3. Replace the template name, "web", and "sample\_project.zip" values with values appropriate to your project.

4. Drop the file sample\_project.zip in the templates folder.

5. Save and close project\_templates.rb.


**File > New > Project...** and create a project of the appropriate type above; you should see your template in the list.

### Remote content

Note that this does not yet work for Titanium projects. See bug [http://jira.appcelerator.org/browse/TISTUD-640](http://jira.appcelerator.org/browse/TISTUD-640) for status on that feature.

If you instead have a project template hosted on a Git repo, you can reference that as well:

1. Create a templates directory in the bundle and add a project\_templates.rb file in the templates directory.

2. Add the following content to the project\_templates.rb file:

  `require` `'ruble'`

  `project_template` `"Sample Remote Project Template"`  `do` `|t|`

  `t.type = :web`

  `t.location =` `"git://github.com/repo.git"`

  `t.description =` `"Remote template. Requires network access."`

  `t.icon =` `"template.png"`  `// Ideally a ruble-relative path to a 48x48px icon. Could also be a URL to a remote file`

  `t.tags = [``'Titanium Classic'``]`

  `end`

3. Replace the template name, "web", and "location" values with values appropriate to your project.

4. Save and close project\_templates.rb.


**File > New > Project...** and create a project of the appropriate type above; you should see your template in the list.

The [Ruble Specification](/docs/appc/Axway_Appcelerator_Studio/Axway_Appcelerator_Studio_Guide/Customizing_Studio/Rubles/Ruble_Specification/) gives a complete discussion on the new Ruble scripting system in Studio.

### Template variables

It's possible to add template-variables in the project's template files. Those variables will be substituted with the appropriate content as the project is created.

By default, variables are not replaced. If you need to turn this on, use "t.replace\_parameters = true" in the project template definition to enable substitution

The following variables are supported:

TM\_NEW\_FILE\_BASENAME

The file name, without the file extension.

TM\_NEW\_FILE

The absolute path to the current file.

TM\_NEW\_FILE\_DIRECTORY

The directory path for the current file.

TM\_PROJECTNAME

The name of the created project.

TIME

The current time (in words).

YEAR

The current year.

Variables should be inserted inside a ${} blocks into your code. For example:

`Project name is ${TM_PROJECTNAME}.`
