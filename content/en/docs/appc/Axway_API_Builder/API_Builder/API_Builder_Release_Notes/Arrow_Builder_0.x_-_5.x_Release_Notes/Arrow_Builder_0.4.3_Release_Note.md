{"title":"Arrow Builder 0.4.3 Release Note","weight":"90"} 

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## Arrow Builder 0.4.3 - 11 June 2015

Arrow Builder 0.4.3 is a patch release, addressing high-priority issues from previous releases.

### New Feature

Add ability to return response results in a specific format by adding the format extension as a suffix to the response. Supported extensions are json, xml, csv, yaml, yml, txt and js. For example, if the API call is the the /api/foo path, to retrieve results as XML, use /api/foo.xml.

### Fixed Issues

*   API-455: Model: Query - Specified order of data is not correctly returned
    
*   API-785: Azure connector causes crash on start-up when wiring up Models
    
*   API-831: Arrow apps in VPCs always use the public ACS environment
    
*   API-832: Arrow apps in VPCs created with a default user named "undefined"