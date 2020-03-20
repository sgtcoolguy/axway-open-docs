{"title":"Arrow Builder 1.3.13 Release Note","weight":"40"}

*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## Arrow Builder 1.3.13

Arrow Builder 1.3.13 is a minor release that includes new features, improvements, and bug fixes.

### Behavior Changes

* When using the guided connector development, after adding a new capability, the Arrow application will stop running and output instructions on what to do next. Previously, the Arrow application would restart, which could cause a crash.

### New Features and Improvements

* Add ability to set descriptions for auto-generated APIs. For details, see the _Model Properties_ section in the Arrow Admin console.

* Allow Arrow client sessions to end when the browser session ends.

### Fixed Issues

* Fixed an issue where adding \\n to the description moves the content out of the table.

* Fixed an issue where a bizarre stack trace would output after restarting the Arrow project.

* Fixed an issue using the Photo sync images parameter with Arrow. Use the following syntax to pass the parameter:

    ```
    {
      'photo_sizes': {preview: '120x120#'},
      'photo_sync_sizes[]': 'preview'
    }
    ```

* Fixed an issue where the Arrow application now throws a 504 error code if the request takes more than 60 seconds.

* Fixed an issue where the MSSQL connector would throw an error on run.
