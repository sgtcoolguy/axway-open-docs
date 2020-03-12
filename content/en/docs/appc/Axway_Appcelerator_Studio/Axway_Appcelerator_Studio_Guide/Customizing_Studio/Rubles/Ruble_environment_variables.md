{"title":"Ruble environment variables","weight":"120"} 

# Ruble environment variables

*   [Overview](#Overview)
    
*   [Referencing an environment variable](#Referencinganenvironmentvariable)
    
*   [Setting an environment variable](#Settinganenvironmentvariable)
    
*   [TextMate Environment Variables](#TextMateEnvironmentVariables)
    
    *   [Current Editor](#CurrentEditor)
        

## Overview

Rubles can reference environment variables during execution, and developers can contribute new environment variables as well.

## Referencing an environment variable

Environment variables are available through a hash. There are two methods of accessing them, depending on how they are used in the Ruby code:

*   In statements: filepath.sub(ENV\['TM\_PROJECT\_DIRECTORY'\], '') : File.basename(filepath)
    
*   Inside strings: rspec\_merb\_gem = (Dir\["#{ENV\['TM\_PROJECT\_DIRECTORY'\]}/gems/gems/rspec\*"\].first || ''))
    

Note the usage of #ENV\['keyname'\] inside strings.

## Setting an environment variable

You can also set variables into the same hash:

*   In Ruby code: ENV\['TM\_DATE'\] = Time.now.strftime("%Y-%m-%d")
    
*   Example:
    
    `template` `"XXX Template"`  `do` `|t|`
    
    `t.filetype =` `"*.xxx"`
    
    `t.invoke` `do` `|context|`
    
    `ENV[``'TM_DATE'``] = Time.now.strftime(``"%Y-%m-%d"``)`
    
    `raw_contents = IO.read(``"#{File.dirname(ENV['TM_BUNDLE_SUPPORT'])}/templates/yyy.xxx"``)`
    
    `raw_contents.gsub(/\$\{([Creating a` `new` `template^}]*)\}/) {|match| ENV[match[``2``..-``2``]] }`
    
    `end`
    
    `end`
    

## TextMate Environment Variables

### Current Editor

Variable

Description

TM\_BUNDLE\_PATH

Absolute path to the root of the ruble directory

TM\_BUNDLE\_SUPPORT

Absolute path to the lib sub-dir of the ruble

TM\_CARET\_LINE\_NUMBER

Line number where the caret is in the active editor (1-based)

TM\_CARET\_LINE\_TEXT

Text of the line where the caret is in the active editor

TM\_CARET\_OFFSET

Offset of the caret in the active editor, from beginning of the file (0-based)

TM\_COLUMN\_NUMBER

caret\_column + 1

TM\_COMMENT\_END

end characters used when wrapping comment, i.e. '\*/' - may not exist for pair because there's only start characters (i.e. // or #)

TM\_COMMENT\_START

start characters used when wrapping comment, i.e. '// ', '# ', '/\*'

TM\_CURRENT\_LINE

Text of the current line in the active editor

TM\_DIRECTORY

Absolute path of the parent directory of the file in the active editor

TM\_EMAIL

email address of current user

TM\_FILENAME

Just the filename (basename) of the file in the active editor

TM\_FILEPATH

Absolute path of the file in the active editor

TM\_FULLNAME

Full name of current user

TM\_INPUT\_START\_COLUMN

Offset inside the line, from beginning of line (1-based)

TM\_INPUT\_START\_LINE

TM\_SELECTION\_START\_LINE\_NUMBER

TM\_INPUT\_START\_LINE\_INDEX

Offset inside the line, from beginning of line (0-based)

TM\_LINE\_INDEX

Offset inside the line, from beginning of line (0-based)

TM\_LINE\_NUMBER

line number where selection begins in active editor (lines are 1-based)

TM\_NEW\_FILE

Absolute path to new file

TM\_NEW\_FILE\_BASENAME

Basename of the new file

TM\_NEW\_FILE\_DIRECTORY

Directory containing the new file

TM\_RUBY

Override pointer to ruby executable to use

TM\_SELECTED\_FILE

Absolute path of the file in the active editor

TM\_SELECTED\_TEXT

actual text selected in the active editor

TM\_SELECTION\_END\_LINE\_NUMBER

line number where selection ends in active editor (lines are 1-based)

TM\_SELECTION\_LENGTH

length of selected text in active editor

TM\_SELECTION\_OFFSET

offset of beginning of selection inside active editor (from beginning of file, 0-based)

TM\_SELECTION\_START\_LINE\_NUMBER

line number where selection begins in active editor (lines are 1-based)

TM\_SOFT\_TABS

"YES" = use spaces for tabs, "NO" = use tab character

TM\_TAB\_SIZE

number of spaces to represent a tab/indent level, typically 4, 2 for ruby code

USER

shortname for current user, i.e 'cwilliams'