{"title":"Custom Objects and Fields","weight":"30"}

This document provides information about custom objects and fields, how to create custom objects, adding and removing custom fields, and supported data types.

* [Custom objects and custom fields](#custom-objects-and-custom-fields)

* [Creating custom objects](#creating-custom-objects)

* [Adding custom fields to predefined objects](#adding-custom-fields-to-predefined-objects)

* [Supported data types](#supported-data-types)

* [Indexing size limit for custom objects and fields](#indexing-size-limit-for-custom-objects-and-fields)

* [Geographic coordinates in custom fields](#geographic-coordinates-in-custom-fields)

    * [Remove a field](#remove-a-field)

    * [Querying custom fields](#querying-custom-fields)

* [Availability](#availability)

* [iOS](#ios)

## Custom objects and custom fields

Mobile Backend Services (MBS) provides many types of commonly used predefined objects such as [Users](/arrowdb/latest/#!/api/Users) and [Photos](/arrowdb/latest/#!/api/Photos). However, you may want to create custom data types or store custom fields on predefined MBS objects. Custom Objects and Custom Data Fields provide your application with this ability.

## Creating custom objects

If you would like to create custom objects with a custom object type, please refer to [CustomObjects](/arrowdb/latest/#!/api/CustomObjects) to get a list of API calls that can be used to create and access custom objects.

## Adding custom fields to predefined objects

If you would like to store additional custom data into any predefined MBS objects, you can pass in JSON encoded custom\_fields. Any number of custom fields can be specified for an instance of a predefined object.

For example, if you are using the Users API and want to store the age and favorite color of each user, include JSON encoding of custom\_fields.

`custom_fields='{`

`"age"``: 23,`

`"favorite_color"``:` `"blue"`

`}'`

For example, to associate the above custom fields to users:

`$ curl -b cookies.txt -c cookies.txt -X POST --data-urlencode` `"email=john.smith@company.com"` `--data-urlencode`

`"role=teacher"` `--data-urlencode` `"first_name=John"` `--data-urlencode` `"last_name=Smith"` `--data-urlencode`

`"password=pass"` `--data-urlencode` `"password_confirmation=pass"` `--data-urlencode 'custom_fields={``"age"``:23,`

`"favorite_color"``:``"blue"``}' https:``//api.cloud.appcelerator.com/v1/users/create.json?key=<YOUR APP APP KEY>`

`{`

`"meta"``: {`

`"status"``:` `"ok"``,`

`"code"``: 200,`

`"method_name"``:` `"createUser"``,`

`"session_id"``:` `"xdqCplQqcXBq8WW1ir9nzq5U4nE"`

`},`

`"response"``: {`

`"users"``: [`

`{`

`"id"``:` `"4ec5907bd9ca72020c000005"``,`

`"first_name"``:` `"John"``,`

`"last_name"``:` `"Smith"``,`

`"created_at"``:` `"2011-11-17T22:53:48+0000"``,`

`"updated_at"``:` `"2011-11-17T22:53:48+0000"``,`

`"external_accounts"``: [`

`],`

`"role"``:` `"teacher"``,`

`"email"``:` `"john.smith@company.com"``,`

`"custom_fields"``: {`

`"age"``: 23,`

`"favorite_color"``:` `"blue"`

`},`

`"stats"``: {`

`"photos"``: {`

`"total_count"``: 0`

`},`

`"storage"``: {`

`"used"``: 0`

`}`

`}`

`}`

`]`

`}`

`}`

Custom Data is returned in the custom\_fields JSON response field in the type that was specified. Attempting to define custom fields using invalid types or an incorrect naming convention will be silently ignored.

## Supported data types

| Type | Example |
| --- | --- |
| Boolean | true or false |
| String | "blue" |
| Number | 23 or 1.234 |
| Date | "2011-11-02 17:07:37 -0700". If a string value matches date format "yyyy-mm-dd hh:mm:ss+zzzz" or "yyyy-mm-dd:hh:mm:ss+zzzz", it will be converted to Date type on the API Builder backend |

You could also store more complex data types, such as Array and Hash. Hash and Array can be embedded into each other. Currently, data stored inside a Hash is not queryable.

| Type | Example |
| --- | --- |
| Hash | {"age":23,"scores":{"math":90, "physics":100}, "my\_favorite\_colors":\["blue","red"\]} |
| Array | \["nissan", "honda"\] or \[2006, 2008\], \[{"age":28}, {"color":"blue"}\] |

## Indexing size limit for custom objects and fields

To support efficient data query operations, MBS indexes the field names and values of each custom object, or custom fields you add to a predefined object. For example, suppose you create a custom object, cars, with the fields make and model. Mobile Backend Services will create two index entries in the MongoDB database, one for each field. The total size of an index entry, including meta-data added by MBS, must be less than **1024 bytes** (1KB).

If a custom field's name or value exceeds this size, then no index entry for that field is created. Consequently, if you run a custom [query](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Search_and_Query_APIs/) against that field, nothing will be returned.

For instance, in the previous example, suppose the string value assigned to the model was greater than 1KB. If you queried the cars collection for objects whose model matched that value, no objects would be returned:

`Cloud.Objects.query({`

`classname:` `'cars'``,`

`where: {`

`make: {`

`$regex:``"^That Really Long Model Name*"`

`}`

`}`

`},` `function` `(e) {`

`if` `(e.success) {`

`console.log(e.cars.length);` `// 0`

`}`

`});`

## Geographic coordinates in custom fields

To enable geographical searches, there is a predefined custom coordinates field for optionally storing geographic coordinates. The coordinates field can store a single location as an array ( \[longitude, latitude\] ) or multiple locations as an array of arrays ( \[\[longitude1,latitude1\], \[longitude2, latitude2\]\] ). So for the above example, to store location information about the user, we might have:

`custom_fields = '{`

`"color"``:` `"blue"``,`

`"age"``: 23,`

`"coordinates"``: [-122.1, 37.1]`

`}'`

### Remove a field

If you wish to remove a custom field during an update, set the field value to null.

`{`

`"age"``:` `null`

`}`

### Querying custom fields

Data stored in custom fields other than Array and Hash can be queried together with predefined fields. Please refer to [Query](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Search_and_Query_APIs/) for more information. If you define a custom field name that is the same as one of the predefined fields, you will be able to store and retrieve it, but you won't be able to query on it since the query action would be performed on the predefined field instead. For example, [Users](/arrowdb/latest/#!/api/Users) have a predefined field called first\_name, if you define a custom field also called first\_name, when you try to query first\_name, it will only query against the predefined first\_name field.

## Availability

The following MBS objects allow you to add one or more extra data fields during create and update actions:

* [Chats.create](/arrowdb/latest/#!/api/Chats-method-create)

* [Checkins.create](/arrowdb/latest/#!/api/Checkins-method-create)

* [PhotoCollections.create](/arrowdb/latest/#!/api/PhotoCollections-method-create) and [update](/arrowdb/latest/#!/api/PhotoCollections-method-update)

* [Events.create](/arrowdb/latest/#!/api/Events-method-create) and [update](/arrowdb/latest/#!/api/Events-method-update)

* [Files.create](/arrowdb/latest/#!/api/Files-method-create) and [update](/arrowdb/latest/#!/api/Files-method-update)

* [Messages.create](/arrowdb/latest/#!/api/Messages-method-create)

* [Photos.create](/arrowdb/latest/#!/api/Photos-method-create) and [update](/arrowdb/latest/#!/api/Photos-method-update)

* [Places.create](/arrowdb/latest/#!/api/Places-method-create) and [update](/arrowdb/latest/#!/api/Places-method-update)

* [Posts.create](/arrowdb/latest/#!/api/Posts-method-create) and [update](/arrowdb/latest/#!/api/Posts-method-update)

* [Reviews.create](/arrowdb/latest/#!/api/Reviews-method-create) and [update](/arrowdb/latest/#!/api/Reviews-method-update)

* [Statuses.create](/arrowdb/latest/#!/api/Statuses-method-create)

* [Users.create](/arrowdb/latest/#!/api/Users-method-create) and [update](/arrowdb/latest/#!/api/Users-method-update)

## iOS

If you are using the [iOS APS SDK](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Mobile_Backend_Services_SDKs/AMPLIFY_Appcelerator_Platform_Services_SDK_for_iOS_Mobile_Backend_Services/) to create an object's custom fields, use an NSDictionary to construct the custom data you want to associate with the object.

The following table lists the data types you can define with the iOS APS SDK:

| Type | Example | iOS Class |
| --- | --- | --- |
| String | "blue" | NString |
| Number | 123 or 1.234 | \[NSNumber numberWithInt:\] or \[NSNumber numberWithDouble:\] |
| Boolean | true or false | \[NSNumber numberWithBool:\] |
| Date | "2011-11-02 17:07:37 -0700" | NSString |
| Hash | {"age": 23, "color": "blue"} | NSDictionary |
| Array | \[123, 234\] or \["mike", "joe"\] | NSArray |
| Geo-coordinates | \[lng, lat\], e.g. \[122.33, 37.48\] | NSArray with two NSNumber elements |

For example, if you want to create a user with custom fields, such as eye\_color, enrolled\_at, etc., you can put all the custom fields in an NSDictionary.

`NSMutableDictionary *customFields = [NSMutableDictionary dictionary];`

`[customFields setObject:@``"brown"` `forKey:@``"eye_color"``];` `// set a string`

`[customFields setObject:@``"2011-11-02 17:07:37 -0700"` `forKey:@``"enrolled_at"``];` `// set a date`

`[customFields setObject:[NSNumber numberWithInt:23] forKey:@``"age"``];` `// set a number`

`[customFields setObject:[NSNumber numberWithBool:``true``] forKey:@``"student"``];` `// set a boolean`

`[customFields setObject:[NSArray arrayWithObjects:@``"hiking"``, @``"reading"``, nil] forKey:@``"hobby"``];` `// set an array`

`[customFields setObject:[NSDictionary dictionaryWithObjectsAndKeys:@``"cookies"``, @``"favorite"``, nil]`

`forKey:@``"others"``];`

`NSMutableDictionary *params = [NSMutableDictionary dictionary];`

`[params setObject:@``"john@usc.com"` `forKey:@``"email"``];`

`[params setObject:@``"John"` `forKey:@``"first_name"``];`

`[params setObject:@``"Woo"` `forKey:@``"last_name"``];`

`[params setObject:@``"pass"` `forKey:@``"password"``];`

`[params setObject:@``"pass"` `forKey:@``"password_confirmation"``];`

`[params setObject:customFields forKey:@``"custom_fields"``];` `// add custom fields`

`[APSUsers create:params withBlock:^(APSResponse *e){`

`if` `(e.success) {`

`NSArray *users = [e.response valueForKey:@``"users"``];`

`if` `([users count] == 1) {`

`NSDictionary *user = users[0];`

`NSLog(@``"Successfully registered user %@"``, [user valueForKey:@``"email"``]);`

`NSLog(@``"custom fields are %@"``, [user valueForKey:@``"custom_fields"``]);`

`}`

`}` `else` `{`

`[[[UIAlertView alloc] initWithTitle:@``"Error"` `message:e.errorMessage delegate:nil`

`cancelButtonTitle:@``"OK"` `otherButtonTitles:nil] show];`

`}`

If you would like to use your custom data type, you need to provide a class method to JSON to encode the data of your object.

`@interface MyObject : NSObject`

`@property NSString *color;`

`@property NSNumber *mileage;`

`@end`

`@implementation MyObject`

`/*!`

`Converts the object to an encodable JSON object.`

`@return Object encodable as JSON, such as a NSDictionary or NSArray.`

`*/`

`- (id)toJSON`

`{`

`return` `[NSDictionary dictionaryWithObjectsAndKeys:self.color, @``"color"``, self.mileage, @``"mileage"``, nil];`

`}`

`@end`

`MyObject *object = [[MyObject alloc] init];`

`object.color = @``"green"``;`

`object.mileage = [NSNumber numberWithDouble:23.3];`

`NSMutableDictionary *customFields = [NSMutableDictionary dictionary];`

`[customFields setObject:[object toJSON] forKey:@``"MyObject"``];`
