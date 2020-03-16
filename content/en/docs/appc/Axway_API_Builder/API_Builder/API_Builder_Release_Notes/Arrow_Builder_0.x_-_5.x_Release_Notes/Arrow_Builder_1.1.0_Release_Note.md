{"title":"Arrow Builder 1.1.0 Release Note","weight":"80"}

API Builder 3.x is deprecated

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.

## Arrow Builder 1.1.0 - 08 July 2015

Arrow Builder 1.1.0 is a feature release, including new features, improvements and bug fixes.

### Behavior Changes

Connectors no longer automatically generate APIs for their models. To automatically generate the APIs for a connector's model, add the modelAutogen key to the connector's configuration file and set it to true.

### Fixed Issues and Improvements

* API-526: MySQL Connector: If you use sel/unsel in a query, null values are being returned

* API-556: While running locally, if you update a local model's name, then the previous auto-generated API docs do not get deleted

* API-600: Connector models should not generate API's automatically

* API-646: ArrowDB: Show an error when trying to query with $like and a wildcard prefix

* API-690: ArrowDB Connector: if you use the distinct endpoint with a $like query, a stack trace is thrown in the terminal

* API-803: Conflict with auto-generated "/api/user/:id" API endpoint when creating an "/api/user/me" API endpoint

* API-851: Defer batch requests to connectors if applicable

* API-866: Export express so user can access included middleware

* API-876: If you make a PUT API call, you will get a 404 on the first request

* API-879: Fixed request logging

* API-884: Fixed access log capabilities

* API-894: If you create a new model while running locally, the local admin page becomes blank after you refresh

* API-906: Latest arrow is returning 404 for PUT request (update) using arrowdb

### Known Issues

* API-905: Arrow application throws an error when trying to use two different MySQL databases.

* API-917: The styling of the code examples in the Admin console is skewed for both local builds and published Arrow applications.

### API Changes

| Name | Type | Description |
| --- | --- | --- |
| Arrow.express | instance property | Express module instance. |
