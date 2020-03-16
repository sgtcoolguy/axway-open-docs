{"title":"Atomic Increment Operator","weight":"10"}

Mobile Backend Services supports the Mongo $inc atomic increment operator.

## $inc

You can use $inc to increment (or decrement) a [custom field](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Custom_Objects_and_Fields/) by a specified value in a single update operation.

* The operator accepts positive and negative increment amounts

* It can only be applied to a single field per method call.

$inc is specified with the following form, where fieldName is the name of the field to update and value is a positive (or negative) number to increment (or decrement) fieldName by:

`"fieldName"``: {` `"$inc:"` `value}`

The operator must be enclosed in quotes, as shown above. The following methods support the $inc operator:

* [Checkins.update](/arrowdb/latest/#!/api/Checkins-method-update)

* [CustomObjects.update](/arrowdb/latest/#!/api/CustomObjects-method-update)

* [Events.update](/arrowdb/latest/#!/api/Events-method-update)

* [Files.update](/arrowdb/latest/#!/api/Files-method-update)

* [PhotoCollections.update](/arrowdb/latest/#!/api/PhotoCollections-method-update)

* [Photos.update](/arrowdb/latest/#!/api/Photos-method-update)

* [Places.update](/arrowdb/latest/#!/api/Places-method-update)

* [Posts.update](/arrowdb/latest/#!/api/Posts-method-update)

* [Reviews.update](/arrowdb/latest/#!/api/Reviews-method-update)

* [Users.update](/arrowdb/latest/#!/api/Users-method-update)

* [Statuses.update](/arrowdb/latest/#!/api/Statuses-method-update)

### Examples

The following example increments the score custom field by 10 in a [CustomObjects](/arrowdb/latest/#!/api/CustomObjects) update to a custom object called family:

`$ curl -b c.txt -c c.txt -X PUT -F` `"id=511117915554f74313000009"` `-F` `"fields={"``favorite``":"``play xbox 360",`

`"pet"``:``"shark"` `,``"score"``:{``'$inc'``:10}}"`

`"api.cloud.appcelerator.com/v1/objects/family/update.json?key=TENIhpXtjFbkBbztvfZMwnciOjE9aHjd"`

`{`

`"meta"``: {`

`"code"``: 200,`

`"status"``:` `"ok"``,`

`"method_name"``:` `"updateCustomObject"`

`},`

`"response"``: {`

`"family"``: [`

`{`

`"family_name"``:` `"ACS"``,`

`"score"``: 10,`

`"age"``: 40,`

`"cars"``: 1,`

`"favorite"``:` `"play xbox 360"``,`

`"pet"``:` `"shark"``,`

`"id"``:` `"511117915554f74313000009"``,`

`"created_at"``:` `"2013-02-05T14:30:41+0000"``,`

`"updated_at"``:` `"2013-02-05T14:30:41+0000"``,`

`"user"``: {`

`"id"``:` `"511117905554f74313000003"``,`

`"first_name"``:` `"Alice"``,`

`"last_name"``:` `"Gal"``,`

`"created_at"``:` `"2013-02-05T14:30:40+0000"``,`

`"updated_at"``:` `"2013-02-05T14:30:41+0000"``,`

`"external_accounts"``: [`

`],`

`"confirmed_at"``:` `"2013-02-05T14:30:40+0000"``,`

`"username"``:` `"alice"``,`

`"email"``:` `"alice@gal.com"``,`

`"admin"``:` `"false"`

`}`

`}`

`]`

`}`

`}`

The following example decrements the score custom field by 20 in a [Checkins](/arrowdb/latest/#!/api/Checkins) update:

`$ curl -b c.txt -c c.txt -X PUT -F` `"checkin_id=511111945554f742d300000b"` `-F`

`"custom_fields={"``favorite``":"``play xbox 360``", "``pet``":"``shark``" ,"``score``":{'$inc':-20}}"`

`"https://api.cloud.appcelerator.com/v1/checkins/update.json?key=TENIhpXtjFbkBbztvfZMwnciOjE9aHjd"`

`{`

`"meta"``: {`

`"code"``: 200,`

`"status"``:` `"ok"``,`

`"method_name"``:` `"updateCheckin"`

`},`

`"response"``: {`

`"checkins"``: [`

`{`

`"id"``:` `"511111945554f742d300000b"``,`

`"created_at"``:` `"2013-02-05T14:05:08+0000"``,`

`"updated_at"``:` `"2013-02-05T14:05:08+0000"``,`

`"place"``: {`

`"id"``:` `"511111935554f742d3000009"``,`

`"name"``:` `"Maya Restaurant"``,`

`"created_at"``:` `"2013-02-05T14:05:07+0000"``,`

`"updated_at"``:` `"2013-02-05T14:05:07+0000"``,`

`"address"``:` `"303 2nd Street"``,`

`"city"``:` `"San Francisco"``,`

`"state"``:` `"CA"``,`

`"country"``:` `"United States"``,`

`"phone_number"``:` `"(415) 543-2928"``,`

`"latitude"``: 37.784732,`

`"longitude"``: -122.395441,`

`"google_cid"``:` `"7106049823222705125"``,`

`"user"``: {`

`"id"``:` `"511111925554f742d3000003"``,`

`"first_name"``:` `"Alice"``,`

`"last_name"``:` `"Gal"``,`

`"created_at"``:` `"2013-02-05T14:05:06+0000"``,`

`"updated_at"``:` `"2013-02-05T14:05:08+0000"``,`

`"external_accounts"``: [`

`],`

`"confirmed_at"``:` `"2013-02-05T14:05:06+0000"``,`

`"username"``:` `"alice"``,`

`"email"``:` `"alice@gal.com"``,`

`"admin"``:` `"false"`

`}`

`},`

`"user"``: {`

`"id"``:` `"511111925554f742d3000003"``,`

`"first_name"``:` `"Alice"``,`

`"last_name"``:` `"Gal"``,`

`"created_at"``:` `"2013-02-05T14:05:06+0000"``,`

`"updated_at"``:` `"2013-02-05T14:05:08+0000"``,`

`"external_accounts"``: [`

`],`

`"confirmed_at"``:` `"2013-02-05T14:05:06+0000"``,`

`"username"``:` `"alice"``,`

`"email"``:` `"alice@gal.com"``,`

`"admin"``:` `"false"`

`},`

`"custom_fields"``: {`

`"family_name"``:` `"ACS"``,`

`"score"``: 15,`

`"age"``: 40,`

`"cars"``: 1,`

`"favorite"``:` `"play xbox 360"``,`

`"pet"``:` `"shark"`

`}`

`}`

`]`

`}`

`}`

If you apply $inc to multiple fields in one Update call, you will get an error:

`$ curl -b c.txt -c c.txt -X PUT -F` `"checkin_id=511111945554f742d300000b"` `-F`

`"custom_fields={"``favorite``":"``play xbox 360``", "``pet``":"``shark``" ,"``score``":{$inc:10}, "``age``":{$inc:10}}"`

`"http://api.cloud.appcelerator.com/v1/checkins/update.json?key=HSejkGE9ghavAelMJv7bZYNM5HyMhqYq"`

`{`

`"meta"``: {`

`"status"``:` `"fail"``,`

`"code"``: 400,`

`"message"``:` `"$inc operation only support to increase one field once."``,`

`"method_name"``:` `"updateCheckin"`

`}`

`}`
