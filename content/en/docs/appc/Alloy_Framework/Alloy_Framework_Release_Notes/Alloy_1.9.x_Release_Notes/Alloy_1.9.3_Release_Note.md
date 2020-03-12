{"title":"Alloy 1.9.3 - 8 October 2016","weight":"30"} 

# Alloy 1.9.3 - 8 October 2016

Alloy 1.9.3 is a patch release that includes new features, improvements, and bug fixes.

As of this release, the previous Alloy patch release is no longer supported. Note: major and minor releases continue to be supported according to their nominal lifetime. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## New features

*   [ALOY-1493](https://jira.appcelerator.org/browse/ALOY-1493) - \[Alloy\] Alloy sql adapter db\_file to be function
    
    *   The db\_file not accepts function
        
    *   Example:
        
        exports.definition = {  config: {  columns: {},  adapter: {  type: "sql",  collection\_name: "mytable",  db\_file: function() {  var myFile = Titanium.Filesystem.getFile(Titanium.Filesystem.applicationDataDirectory, 'file1.sql');  return myFile.exists() ? myFile.nativePath : Titanium.Filesystem.applicationDataDirectory + 'file2.sql';  },  db\_name: "projectsDB",  idAttribute: "UserID",  remoteBackup: false  }  }};
        

## Improvements

*   [ALOY-1519](https://jira.appcelerator.org/browse/ALOY-1519) - Alloy: Support iOS 10 <RefreshControl> tag in Ti.UI.ScrollView
    
    *   Added support for iOS 10's <RefreshControl> element in Ti.UI.ScrollView
        

## Fixed issues

*   [ALOY-1520](https://jira.appcelerator.org/browse/ALOY-1520) - Replace Ti.Ui.iPhone with Ti.Ui.iOS in Alloy