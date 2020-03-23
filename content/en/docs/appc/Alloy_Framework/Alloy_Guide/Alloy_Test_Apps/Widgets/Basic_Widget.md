{"title":"Basic Widget","weight":"10"}

Demonstrates how to create and use a basic widget.

{{% alert title="💡 Hint" color="info" %}}*App Folder Location*

alloy/test/apps/**widgets/basic**{{% /alert %}}![widget-basic](/Images/appc/download/attachments/41845783/widget-basic.png)

Widgets have their own views/, controllers/, models/, styles/ and assets/ folders. These folders are organized in the same way as the top-level app/ directory in the Alloy project. By convention, widgets resides in the app/widgets folder. The sample application includes a widget named **com.foo.widget** in the app/widgets/ folder, as shown below.

*App and widget folder structure*

```
app
├──assets
├──config.json
├──controllers
│   └──index.js
├──styles
│   ├──app.tss
│   └──index.tss
├──views
│   └──index.xml
└──widgets
    └──com.foo.widget
        ├──assets
        │   └── back.jpg
        ├──controllers
        │   └── widget.js
        ├──styles
        │   └── widget.tss
        ├──views
        │   ├──image.xml
        │   └──widget.xml
        └──widget.json
```

The Alloy app's configuration file (config.json) must declare the widget as a dependency:

*app/config.json*

```json
{
    "dependencies": {
        "com.foo.widget":"1.0"
    },
    "sourcemap": false,
    "adapters": []
}
```

By convention, a widget's default view is located at **_widget\_folder_/views/widget.xml**, and it's controller and style files are are **_widget\_folder_/controllers/widget.js** and **_widget\_folder_/styles/widget.tss**. To include a widget in the main application, insert a **<Widget/>** element and set its **src** attribute to the name of the widget folder ("com.foo.widget" in this case). By default, the widget.xml view is included; you can specify a different widget view XML file by specifying its **name** attribute.

```xml
<Alloy>
    <Window>
        <Widget src="com.foo.widget" name="image"/>
        <Widget src="com.foo.widget" id="w"/>
    </Window>
</Alloy>
```
