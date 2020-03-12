{"title":"ArrowDB 1.1.13 - 11 June 2015","weight":"40"}

## New features

* Added the ability to batch create custom objects using the [objects/:classname/batch\_create.json method](/arrowdb/latest/#!/api/CustomObjects-method-batch_create).


## Bug fixes

* Fixed an issue where relational fields were not expanded in responses from Message APIs.

* Fixed an issue where using the coordinates, order, skip and limit fields together did not return the correct results.

* Fixed an issue where a device could subscribe multiple times to push notifications with the same device token.
