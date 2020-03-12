{"title":"API Builder Tools 2.0.0 Release Note","weight":"30"} 

# API Builder Tools 2.0.0 Release Note

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## API Builder Tools 2.0.0 - 14 April 2017

API Builder Tools 2.0.0 is a major release that includes several new features, bug fixes, and a few known issues.

As of this release, Arrow Builder Tools 5.3.1 will not be supported one calendar year from 2.0.0's release date. See [Axway Appcelerator Deprecation Policy](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Deprecation_Policy/) and [Nominal Lifetimes](/docs/appc/AMPLIFY_Appcelerator_Services_Overview/Axway_Appcelerator_Product_Lifecycle/#NominalLifetimes) documents for details.

## New features

*   With the previous release, the following items were listed as a "tech preview". With this GA release, they have been officially implemented:
    
    *   Refresh of UI with latest Axway brand styling
        
    *   Improved UX for model lifecycle management
        
    *   Enhanced Model builder for creation and composition of new models
        
    *   Model builder workflow has been streamlined to allow the creation of base models and composition from existing models
        
    *   Improved configuration management across deployment environments
        
    *   Streamlined filtering of API logs, advanced filters, and pagination on Logs View
        
    *   Intuitive look and feel for API Test & Docs view
        
    *   Internationalization-ready UI
        
*   This release allows developers to create Swagger-based API endpoints using orchestrations ([Flows](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/Artifacts/Flows/))
    
*   If configured, API Builder transactional logs can be accessed via Embedded Analytics dashboards
    
*   Enhanced DevOps experience through the addition of three publishing options (including the use of Docker file and Docker images)
    

## Fixed issues

*   Previously, Arrow included a bundled version of ReactJS for the web route react engine. ReactJS web route engine is no longer bundled with Arrow. It is available from [https://www.npmjs.com/package/arrow-react-engine](https://www.npmjs.com/package/arrow-react-engine).
    
*   Previously, Arrow used to allow users to access the admin interfaces from machines other than their development machine. Arrow now defaults to only allow connections from localhost only, however it is possible to add to the whitelisted hostnames, IPs or IP ranges.
    
*   Previously, when started by appc run Arrow would watch for changes and restart when it detected a change to certain folders. This feature has been removed and the Arrow app will now only be restarted when making changes from the UI or when the arrow app crashes
    
*   Previously, models which used the composite connector could not reference "object" and "array" fields which existed on a joined model. The Composite connector now looks at the "name" property on a field definition to mean that the field should come from a field of a specific name on the joined model, rather than returning model as an object field or all matching models as an array field.
    
*   Previously, when using composite models, the "multiple" property was documented but didn't have any function. All fields which were a type of array, and joined from another model would perform a "join as an array" and pull in all instances of the joined model. Now that this is fixed, the "multiple" property in the join metadata can be used to specify that a field of type array can contain multiple matches of a single field in a joined model.
    

## Known issues

*   With this release, the model builder workflow doesn't allow extending base models but the same can be accomplished via orchestrations
    
*   The Data Editor feature has been removed from the new UI. If you need to access this feature, it is still available via the old UI (as before).
    
*   npm can warn about a missing connectors package.json file
    
    *   Newer versions of npm (e.g. 4.4.1) can emit a warning, npm WARN enoent ENOENT: no such file or directory, open '/home/<project>/node\_modules/connectors/package.json' when npm is invoked.
        
    *   API Builder maintains a list of installed connectors in node\_modules. This keeps installed modules together, even though npm does not maintain the installed connectors. This results in a node\_modules/connectors directory that does not have a package.json file. npm warns that the file is missing. The warning can be ignored.
        
*   Inline schema are not currently supported
    
    *   Swagger API generated by Arrow is stripped out the inline schema