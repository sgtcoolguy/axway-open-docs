{"title":"Arrow Builder 1.2.62 Release Note","weight":"50"}

{{% alert title="❗️ Warning" color="danger" %}}*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

## Arrow Builder 1.2.62 - 18 September 2015

Arrow Builder 1.2.62 is a patch release, addressing high-priority issues from previous releases.

### New Features

* Create a Swagger Interface as part of the API documentation. For details, see [API Builder APIs](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_APIs/).

* Support clearing local logs in the Admin Console.

### Fixed Issues

* API-1013: Logs in the root directory caused the server to reload

* API-1015: Server should not restart on certain file/directory changes, such as web/public, web/views/ and package.json

* API-1026: Cannot set model fields during a POST in a pre-block on an ArrowDB model

* API-1027: Transaction logs still have too much unnecessary data in them

* API-1030: Server size was not being applied using appc 5.0.0-30

* API-1033: Disable memwatch
