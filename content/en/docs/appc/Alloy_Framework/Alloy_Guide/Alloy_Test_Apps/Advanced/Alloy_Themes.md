{"title":"Alloy Themes","weight":"10"}

This document demonstrates how to use Alloy themes to easily style your entire application UI for different platforms.

{{% alert title="💡 Hint" color="info" %}}*App folder location*

[_alloy_/test/apps/**advanced/themes**](https://github.com/appcelerator/alloy/tree/master/samples/apps/advanced/themes/){{% /alert %}}![Example](/Images/appc/download/attachments/41845677/Example.png)

The themes/ folder contains of three folders named "blue", "dark", and "green" that each contain **assets/** and **styles/** folders. These folders contain, respectively, image files and other theme assets, and TSS files that define the theme's custom styles.

*app/themes folder*

```
├── themes
│   ├── blue
│   │   ├── assets
│   │   │   └── button_blue.png
│   │   └── styles
│   │       └── index.tss
│   ├── dark
│   │   ├── assets
│   │   │   └── button_dark.png
│   │   └── styles
│   │       └── index.tss
│   └── green
│       ├── assets
│       │   └── button_green.png
│       └── styles
│           ├── index.tss
│           └── ios
├── assets
├── styles
│   ├── app.tss
└── views
    ├── dialog.xml
    └── index.xml
```

To use a theme, add it to your Alloy project's **config.json** file with "theme" as the key and the name of the theme folder as the value, as shown below. Before compilation, the content of the appropriate theme's assets folder are copied into the project's assets folder, replacing any files of the same name. Custom theme styles are merged with those defined in the application's app/styles folder. Theme styles take precedence over application styles during this merge process.

*app/config.json*

```json
{
  "global": {
    "theme": "blue"
  },
  "os:ios": {
    "theme": "green"
  },
  "os:android": {
    "theme": "dark"
  },
  "sourcemap": false,
  "adapters": []
}
```

## See also

* [Project Configuration File](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Test_Apps/Basics/Project_Configuration_File/)

* [Style Priorities](/docs/appc/Alloy_Framework/Alloy_Guide/Alloy_Views/Alloy_Styles_and_Themes/#style-priorities)
