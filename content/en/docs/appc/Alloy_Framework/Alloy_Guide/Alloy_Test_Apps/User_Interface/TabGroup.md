{"title":"TabGroup","weight":"190"}

Demonstrates basic use of a TabbedGroup control to display a tabbed interface.

Example App Source Location

You can find this example app in the Alloy repository under [samples/apps/ui/tabgroup](https://github.com/appcelerator/alloy/tree/master/samples/apps/ui/tabgroup). Check the [instructions](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Test_Apps/) how to run these sample projects.

A [TabGroup](#!/api/Titanium.UI.TabGroup) contains one or more [Tab](#!/api/Titanium.UI.TabGroup) objects, each of which has an associated tab control that is used to bring it into focus.

![screenshot](/Images/appc/download/attachments/41845777/screenshot.png)

app/views/index.xml

`<``Alloy``>`

`<``TabGroup``>`

`<!-- Explicit Window declaration -->`

`<``Tab`  `id``=``"tab1"``>`

`<``Window`  `id``=``"win1"``>`

`<``Label``>Label 1</``Label``>`

`<``Label``>Label 2</``Label``>`

`<``Label`  `platform``=``"ios"``>Label 3</``Label``>`

`<``Label``>Label 4</``Label``>`

`<``Label``>Label 5</``Label``>`

`</``Window``>`

`</``Tab``>`

`<!-- Tab included via <``Require``> tag -->`

`<``Require`  `src``=``"tabView"``/>`

`</``TabGroup``>`

`</``Alloy``>`

app/views/tabView.xml

`<``Alloy``>`

`<``Tab`  `title``=``"required"``>`

`<``Window`  `title``=``"required"``>`

`<``Label``>This is a required tab</``Label``>`

`</``Window``>`

`</``Tab``>`

`</``Alloy``>`

## See also

* [Titanium.UI.TabGroup](#!/api/Titanium.UI.TabGroup) API reference
