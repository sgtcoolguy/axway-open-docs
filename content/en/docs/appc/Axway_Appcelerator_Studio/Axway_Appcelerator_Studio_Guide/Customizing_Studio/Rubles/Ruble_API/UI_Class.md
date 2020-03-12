{"title":"UI Class","weight":"100"}

The UI class contains methods for interacting with the user interface inside Studio.

## Usage

Examples of how you might interact with methods of the UI class.

### Singleton:

`require` `'ruble/ui'`

`Ruble::UI.alert(:info,` `'Title'``,` `'Message'``) # opens an info dialog box with title`

## UI Methods

The UI class has the following singleton methods:

Method

Description

alert(style, title, message, \*buttons)

Opens a dialog box. Style can be one of :warning, :error or :info buttons is an array of string labels for the buttons the of which user can choose. The first entry is the default button (what will be chosen if user hits Enter). The return value is the label of the chosen button.

menu(options = \[\])

Pop up a menu on screen.
Options may be an Array of Strings, or an Array of Hashes:

1. If it's an Array of Hashes, it's expected that each Hash will contain:

2. 'display' => String - entry to show in menu

3. 'image' = > String - image to show alongside the entry

4. 'insert' => String - a snippet to insert when the entry is chosen

5. 'tool\_tip' => String - tooltip to display for menu entry


simple\_notification(options = {})

Opens an info dialog box with an "OK" button. Pass in :title, :summary in options hash to set those values on the opened dialog. like calling alert(:info, options\[:title\], options\[:summary\], "OK").

request\_item(:title => '', :prompt => '', :button1 => '', :button2 => '')

request\_color(hex\_string = nil)

Show the system color picker and return a hex-format color (#RRGGBB) string with the chosen color.
If the input string is a recognizable hex string, the default color (in the opened color picker) will be set to it.

request\_confirmation(options = {}

Post a confirmation alert. Returns true if the first button is chosen, false otherwise.
Possible options:

* :button1 => String - label of the default button

* :button2 => String - label of the secondary button

* :title => String - Title of the dialog

* :prompt => String - message in the dialog


request\_string(options)

Opens a dialog box with a text field input. Returns the user input as a string if they choose "OK".
Possible Options:

* :title => String - title of the dialog.

* :prompt => String - message added to dialog

* :button1 => String - label of the confirm button, defaults to "OK"

* :button2 => String - label of the cancel button. defaults to "Cancel".


request\_secure\_string(options = {})

Opens a password dialog. See request\_string.

tool\_tip(content, options = {})

Show Tooltip using the current cursor location. Content is shown as bold text at the top of the tooltip.
Possible options:

* :balloon => true - pop up a balloon style tooltip

* :icon => :error, :info, or :warning. add an image icon in upper left of tooltip. Only used with balloon tooltips.

* :message => String, an optional explanatory string that is shown below content.


request\_file(options = {})

Show a standard open file dialog. Returns the full path of the file/dir as a string.
Possible Options:

* :only\_directories => true - limit to directory selection. If not present or false, it will be limited to only file selection

* :default => String - message added to dialog if selecting directories

* :title => String - title of dialog

* :directory => String - opening directory path for dialog


request\_files(options = {})

Show a standard open file dialog, allowing multiple selections. See request\_file.
