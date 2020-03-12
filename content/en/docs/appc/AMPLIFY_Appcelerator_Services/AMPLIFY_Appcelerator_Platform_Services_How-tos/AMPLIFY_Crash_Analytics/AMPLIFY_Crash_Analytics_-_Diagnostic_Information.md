{"title":"AMPLIFY Crash Analytics - Diagnostic Information","weight":"10"}

Developers can use the AMPLIFY Crash Analytics (ACA) [API](https://docs.appcelerator.com/platform/latest/#!/api/Modules.ACA) to capture additional information that might be useful to diagnose a crash. For example, device information can be obtained using Titanium APIs and set as additional data that will be sent with the crash event. The device information can be set either using the setMetadata method or as a breadcrumb.

The following code sample demonstrates how to gather device information and attach it to the crash event:

* device orientation

* device model

* network info

* device available and total memory

* location


`aca.setMetadata(``'device'``, {`

`orientation: Ti.Gesture.portrait ?` `'portrait'` `:` `'landscape'``,`

`model: Ti.Platform.model,`

`network_type: Ti.Network.networkTypeName,`

`available_memory: Ti.Platform.availableMemory,`

`total_memory: Ti.Platform.totalMemory,`

`location: Ti.Geolocation.lastGeolocation`

`});`

These data points can then be accessed through Query Builder by accessing the data.meta.device.<property>:

obtaining device model

`data.meta.device.model`

![Screen_Shot_2019-09-24_at_2.40.18_PM](/Images/appc/download/attachments/60148830/Screen_Shot_2019-09-24_at_2.40.18_PM.png)
