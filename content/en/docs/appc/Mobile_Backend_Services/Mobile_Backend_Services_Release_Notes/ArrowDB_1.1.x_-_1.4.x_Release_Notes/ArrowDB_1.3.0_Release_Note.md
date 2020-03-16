{"title":"ArrowDB 1.3.0 - 17 September 2015","weight":"20"}

## Behavior changes

* **Search APIs**: All search APIs are deprecated. For text searches, use a [$text query operator](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Search_and_Query_APIs/) with the query method. Existing datasources created before ArrowDB 1.3.0 can continue to use the search API. New datasources created since ArrowDB 1.3.0 cannot use the search API. Affected APIs include [Events.search](/arrowdb/latest/#!/api/Events-method-search), [Friends.search](/arrowdb/latest/#!/api/Friends-method-search), [Places.search](/arrowdb/latest/#!/api/Places-method-search) and [Users.search](/arrowdb/latest/#!/api/Users-method-search).

## New features

* **Subscribe or Unsubscribe to Multiple Push Channels**: Comma-separate a list of channel names to subscribe or unsubscribe to multiple push channels with the [PushNotifications](/arrowdb/latest/#!/api/PushNotifications) APIs.

* **Text Query Operator**: To perform a full-text search on ArrowDB objects, use the $text query operator with the where parameter of query methods. For details, see the [Search and Query guide](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Search_and_Query_APIs/).
