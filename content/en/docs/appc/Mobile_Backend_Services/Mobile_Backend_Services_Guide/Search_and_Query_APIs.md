{"title":"Search and Query APIs","weight":"60"}

* [Query API overview](#query-api-overview)

    * [Query API availability](#query-api-availability)

    * [Query parameters](#query-parameters)

        * [count](#count)

        * [page](#page)

        * [per\_page](#per_page)

        * [limit](#limit)

        * [id and \_id](#id-and-_id)

        * [new\_pagination](#new_pagination)

        * [skip](#skip)

        * [where](#where)

            * [Geographic coordinates](#geographic-coordinates)

        * [order](#order)

        * [sel](#sel)

        * [unsel](#unsel)

* [Query pagination](#query-pagination)

    * [Range-based query pagination examples](#range-based-query-pagination-examples)

        * [Query on a custom field with results in ascending order](#query-on-a-custom-field-with-results-in-ascending-order)

        * [Query on a custom field with results in descending order](#query-on-a-custom-field-with-results-in-descending-order)

        * [Query for the next page of results with results in ascending order](#query-for-the-next-page-of-results-with-results-in-ascending-order)

        * [Query for the previous page of results](#query-for-the-previous-page-of-results)

* [Search API overview](#search-api-overview)

    * [Search API parameters](#search-api-parameters)

        * [page](#page)

        * [per\_page](#per_page)

        * [q](#q)

    * [Search API availability](#search-api-availability)

Mobile Backend Services (MBS) provides APIs for querying and searching for MBS objects. The query APIs allow you to perform custom database-style searches, while search APIs perform a full-text search using the MBS search engine.

{{% alert title="⚠️ Warning" color="primary" %}}The search API is deprecated since Release 1.3.0. Applications created before Arrow Cloud Release 1.3.0 can continue to use the deprecated search API, but new applications will need to use the query API with the $text query operator.{{% /alert %}}

## Query API overview

The query API provides an interface for applying database-style query constraints on predefined objects and [custom fields](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Custom_Objects_and_Fields/).

When no query parameters are provided, all objects of the specified type are returned with default pagination. You can control the pagination of queries with the skip and limit parameters, or by using a custom where clause. See [Query Pagination](#query-pagination) for more information.

You can also control the sort order of query results using the order parameter, and specify the fields you want to include (or exclude) from results using the sel and unsel query parameters.

### Query API availability

The following MBS objects provide query methods: [ACLs](/arrowdb/latest/#!/api/ACLs-method-query), [Chats](/arrowdb/latest/#!/api/Chats-method-query), [Checkins](/arrowdb/latest/#!/api/Checkins-method-query), [CustomObjects](/arrowdb/latest/#!/api/CustomObjects-method-query), [Events](/arrowdb/latest/#!/api/Events-method-query), [Files](/arrowdb/latest/#!/api/Files-method-query), [GeoFences](/arrowdb/latest/#!/api/GeoFences-method-query), [KeyValues](/arrowdb/latest/#!/api/KeyValues-method-query), [Likes](/arrowdb/latest/#!/api/Likes-method-query), [Logs](/arrowdb/latest/#!/api/Logs), [Messages](/arrowdb/latest/#!/api/Messages-method-query), [Photos](/arrowdb/latest/#!/api/Photos-method-query), [Places](/arrowdb/latest/#!/api/Places-method-query), [Posts](/arrowdb/latest/#!/api/Posts-method-query),
[PushNotifications](/arrowdb/latest/#!/api/PushNotifications-method-query), [PushSchedules](/arrowdb/latest/#!/api/PushSchedules-method-query), [Reviews](/arrowdb/latest/#!/api/Reviews-method-query), [Statuses](/arrowdb/latest/#!/api/Statuses-method-query), and [Users](/arrowdb/latest/#!/api/Users-method-query).

For security reasons, when querying for [Users](/arrowdb/latest/#!/api/Users), the [email](/arrowdb/latest/#!/api/Emails) field is not returned in the User object unless you have [admin access](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Admin_Access/)[.](/arrowdb/latest/#!/guide/admin_access)

### Query parameters

The following parameters are available for query operations:

#### count

If the query includes count=true, the response's meta-object contains a count field whose value is the total number of objects that matched the query criteria. If the query matches more than 5000 objects, the count field contains the value "5000+". For more information, see [Query Pagination](#query-pagination).

#### page

{{% alert title="⚠️ Warning" color="primary" %}}Starting in Mobile Backend Services (ArrowDB) 1.1.5, page and per\_page are no longer supported in query operations. Applications should instead use **skip** and **limit** query parameters.{{% /alert %}}

#### per\_page

{{% alert title="⚠️ Warning" color="primary" %}}Starting in Mobile Backend Services (ArrowDB) 1.1.5, page and per\_page are no longer supported in query operations. Applications should instead use **skip** and **limit** query parameters.{{% /alert %}}

#### limit

The number of records to fetch. The value must be greater than 0, and no greater than 1000, or an HTTP 400 (Bad Request) error will be returned. The default value of limit is 10.

#### id and \_id

query by id or \_id:

```
~ curl -d 'where={"id":"54517c49dda09594270002da"}' -X GET "localhost:8082/v1/users/query.json?key=l1J36VuGo2eFMJ
~ curl -d 'where={"id":"54517c49dda09594270002da"}' -X GET
"localhost:8082/v1/users/query.json?key=l1J36VuGo2eFMJKELNXdxAq8Z4MQIbYr&pretty_json=true"
{
    "meta": {
        "code": 200,
        "status": "ok",
        "method_name": "queryUsers"
    },
    "response": {
        "users": [{
            "id": "54517c49dda09594270002da",
            "created_at": "2014-10-29T23:46:17+0000",
            "updated_at": "2014-10-29T23:46:17+0000",
            "external_accounts": [],
            "confirmed_at": "2014-10-29T23:46:17+0000",
            "username": "hmm",
            "email": "",
            "admin": "false",
            "stats": {
                "photos": {
                    "total_count": 0
                },
                "storage": {
                    "used": 0
                }
            },
            "custom_fields": {}
        }]
    }
}

~ curl -d 'where={"_id":"54517c49dda09594270002da"}' -X GET
"localhost:8082/v1/users/query.json?key=l1J36VuGo2eFMJKELNXdxAq8Z4MQIbYr&pretty_json=true"
{
    "meta": {
        "code": 200,
        "status": "ok",
        "method_name": "queryUsers"
    },
    "response": {
        "users": [{
            "id": "54517c49dda09594270002da",
            "created_at": "2014-10-29T23:46:17+0000",
            "updated_at": "2014-10-29T23:46:17+0000",
            "external_accounts": [],
            "confirmed_at": "2014-10-29T23:46:17+0000",
            "username": "hmm",
            "email": "",
            "admin": "false",
            "stats": {
                "photos": {
                    "total_count": 0
                },
                "storage": {
                    "used": 0
                }
            },
            "custom_fields": {}
        }]
    }
}
```

Query multiple objects by using $in:

```
~ curl -d 'where={"_id":{"$in":["54517c49dda09594270002da","54517c33dda09594270002d5"]}}' -X GET
"localhost:8082/v1/users/query.json?key=l1J36VuGo2eFMJKELNXdxAq8Z4MQIbYr&pretty_json=true"
{
    "meta": {
        "code": 200,
        "status": "ok",
        "method_name": "queryUsers"
    },
    "response": {
        "users": [{
            "id": "54517c49dda09594270002da",
            "created_at": "2014-10-29T23:46:17+0000",
            "updated_at": "2014-10-29T23:46:17+0000",
            "external_accounts": [],
            "confirmed_at": "2014-10-29T23:46:17+0000",
            "username": "hmm",
            "email": "",
            "admin": "false",
            "stats": {
                "photos": {
                    "total_count": 0
                },
                "storage": {
                    "used": 0
                }
            },
            "custom_fields": {}
        }, {
            "id": "54517c33dda09594270002d5",
            "created_at": "2014-10-29T23:45:55+0000",
            "updated_at": "2014-10-29T23:45:55+0000",
            "external_accounts": [],
            "confirmed_at": "2014-10-29T23:45:55+0000",
            "username": "test",
            "email": "",
            "admin": "false",
            "stats": {
                "photos": {
                    "total_count": 0
                },
                "storage": {
                    "used": 0
                }
            },
            "custom_fields": {}
        }]
    }
}
```

#### new\_pagination

When new\_pagination=true is included in a query, the number of records evaluated in the database is limited to 5000.

By default, MBS puts no limit on the number of records that are evaluated in the database. This means, for example, that if you execute an open-ended query for all MBS objects of some type, and apply a sort and filter on the results, all records in the database are evaluated, sorted, and filtered in memory.

For applications that have relatively small numbers of total records (< 5000), this operation can be completed efficiently with no noticeable impact on your application's performance. However, if a table has a vast number (>= 1 million) records, these kinds of operations are very inefficient, and your users will notice a performance hit.

#### skip

The number of records to skip. The value must be greater than or equal to 0, and no greater than 4999, or an HTTP 400 error will be returned. To skip 5000 records or more, you need to perform a range-based query. See [Query Pagination](#query-pagination) for more information.

#### where

Constrains values for fields. The value should be encoded JSON. Each value in the search query needs to be less than 1024 bytes. If the value is larger than 1024 bytes, the query does not return any results.

Each type of MBS object has a set of predefined fields that can be queried with the where operator. See each object's query method for details.

Also, you can query the [custom fields](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Custom_Objects_and_Fields/) on any object. Note, however, that you can only query simple values, such as Strings, Dates, Numbers, or Booleans. If a custom field takes an array or object as a value, you can't query any of the values stored in the array or object.

For more information, see [Supported Data Types](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Custom_Objects_and_Fields/).

Currently, MBS does not support case insensitive queries. To perform a case-insensitive query on a field, save an additional normalized copy of the original field and perform the query on the normalized field instead.

To perform an exact match on a field, for example, to search for users with first\_name matching "joe", use:

```
where={"first_name": "joe"}
```

You can add more search criteria by adding them together. For example, to search for users with first\_name matching "joe", favorite\_color matching "blue" and age of 28, use the following query:

```
where={"age": 28, "favorite_color": "blue", "first_name" : "joe"}
```

For non-exact matches, where supports these options:

| Operator | Summary |
| --- | --- |
| $lt | Less than |
| $lte | Less than or equal to |
| $gt | Greater than |
| $gte | Greater than or equal to |
| $ne | Not equal to |
| $in | Contained in, allows you to specify an array of possible matches. |
| $nin | Not contained in, it selects objects for which the specified field does not have any value in the specified array. |
| $or | Use boolean or in a query, an array of expressions, any of which can match. |
| $nor | A boolean or expression to do queries, you give $nor a list of expressions, none of which can match the query. |
| $and | Give $and an array of expressions, all of which must match the query. |
| $all | The $all operator is similar to $in, but instead of matching any value in the specified array, all values in the array must be matched. |
| $elemMatch | Give $elemMatch an expression to match against elements in an array. |
| $exists | Check for the existence of a field. |
| $regex | Regex match on a string. Currently, only prefix matches are supported: the regular expression must begin with an anchor (^) followed by a letter or digit. For example, '^a', '^a.\*', and '^a.\*$' are allowed, but not '^.\*a\*'. |
| $text | Perform a text search on the contents of the field. A **$text** expression has the following syntax:  <br />{ "$text": { "$search": <string> }}  <br />Most punctuation marks and spaces are treated as delimiters allowing you to search for multiple keywords, excluding escaped double quotes (\\") and hyphens (-). Escaped double quotes are used for phrase searches, and hyphens are used to negate searches. Sorting does not work with the $text operator, that is, using the order field will not have any effect when using the $text operator. |

##### Geographic coordinates

For querying geographic coordinates, the following operators are supported:

| Operator | Summary |
| --- | --- |
| $nearSphere | Search near geographic coordinates, the format is \[longitude, latitude\] |
| $maxDistance | and used with $nearSphere to limit maximum search distance. All distances use radians. This allows you to easily multiply by the radius of the earth (about 6371 km or 3959 miles) to get the distance in your choice of units. Conversely, divide by the radius of the earth when doing queries |

You can combine any of the above to build a more complex query.

For more information on constructing geographic coordinate queries, see [Geographic Coordinates in Custom Fields](#geographic-coordinates) and [Custom Objects and Fields](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Custom_Objects_and_Fields/) for a general creation of custom objects and field queries.

If you want to find users with age older than 28:

```
where={"age": {"$gt":28}}
```

If you want to find users at age 28 or 38:

```
where = {"age": {"$in":[28,38]}}
```

If you want to find users at age neither 28 nor 38:

```
where = {"age": {"$nin":[28,38]}}
```

If you want to find a user whose email is "john@example.com" and type is User:

```
where={"$and": [ {"email" : "john@example.com"}, { "_type" : "User" } ] }
```

If you want to find users who have options are 2,3:

```
where={"options": {"$all" : [2,3] } }
```

If you want to find users who have location information:

```
where={"location": {"$exists" : true} }
```

If you want to find users who do not have location information:

```
where={"location": {"$exists" : false} }
```

If you have a custom array with your user object, such as a list of scores (scores: \[65, 86, 92'), you can search the elements in the array. For example, if you want to search for scores within a certain range:

```
where={"scores":{ "$elemMatch": { "$gte": 70, "$lt": 90 } }}
```

If you have a custom array of tags, such as tags: \[ 'employee', 'manager' \], you can use the $all operator to return objects that contain all the specified elements:

```
where={"tags":{ "$all": [ 'employee', 'manager' ] }
```

If you have assigned custom coordinates to your user objects, you can search by users' coordinates. For example, if you want to find users named "joe" near longitude -122.1 and latitude 37.1:

```
where={"first_name":"joe", "coordinates":{"$nearSphere":[-122.1, 37.1]}}
```

To find users named "joe" near longitude -122.1 and latitude 37.1 with a maximum distance of 5 miles (convert 5 miles to radians, 5/3959 = 0.00126):

```
where={"first_name":"joe", "coordinates":{"$nearSphere":[-122.1,37.1], "$maxDistance" : 0.00126}}
```

To search for the keywords javascript, ruby, or python, but not php:

```
where={"$text": { "$search": "javascript,ruby,python,-php" }}
```

#### order

Sort results by one or more fields. In general, you can sort based on any predefined field that you can query using the where operator, as well as on custom fields. Any exceptions to this rule are noted in API reference for the individual query methods.

To reverse the sorting order, add order in front of a field. For example, to sort results by first\_name in ascending order then created\_at in descending order:

```
order=first_name,-created_at
```

#### sel

Selects which fields to return from the query. Do not use this parameter if you are using the unsel parameter.

Assign an array of field names to filter to the all field to search all JSON fields, including fields in nested objects. Currently, this is the only supported option.

If you want to display a field from the custom\_field object, pass the field name of the custom\_field object.

If you want to display a field from a nested object, then both the name of the nested object and field need to be specified.

For example, if you want to return the first\_name field only:

```
sel={"all":["first_name"]}
```

#### unsel

Selects which fields not return from the query. Do not use this parameter if you are using the sel parameter.

Assign an array of field names to filter to the all field to search all JSON fields, including fields in nested objects. Currently, this is the only supported option.

If you want to hide a field from the custom\_field object, pass the field name of the custom\_field object.

If you want to hide displaying a field from a nested object, then both the name of the nested object and field need to be specified.

For example, if you want to return all fields except first\_name:

```
unsel={"all":["first_name"]}
```

## Query pagination

Starting with Mobile Backend Services (ArrowDB) 1.1.5, we have made the following changes:

* Skip is limited to 0-4999; as a result, you can not skip beyond 5000 records.

* If the query includes count=true, the query response's meta object contains a count field whose value is the total number of objects that match the query criteria. If the query matches more than 5000 objects, the count field contains the value "5000+". If your query result set includes more than 5000 records, you should perform range-based queries for pagination. This is done by including a where parameter on an object field using the $gt or $lt operators, as discussed below.

For example, the following cURL uses a range-based query for Statuses whose custom field named score is less than 100 and sorts the results in ascending order on the score field:

```
$ curl -d 'where={"score":{"$lt":100}}&order=score' -X GET
"http://<HOST>/v1/statuses/query.json?key=<KEY>&count=true&pretty_json=true"
```

Mobile Backend Services object IDs, represented by the \_id field, are based on object timestamps and machine IDs, which allows for range-based pagination. For example, suppose an application performs a query whose last object returned has an ID of "5418a8815a6919fde8cf1e4d". To get the set of objects created before the object, the application would query for those objects whose \_id field is less than that value:

```
$ curl -X GET -d 'where={"_id":{"$lt":"5418a8815a6919fde8cf1e4d"}}'
"http://<HOST>/v1/statuses/query.json?key=<KEY>&count=true&pretty_json=t&_session_id=<SESSION_ID>"
```

Similarly, if the ID of the first object returned in a query was "5418a87f5a6919fde8cee391" the application would query on objects whose \_id field is greater than that value to retrieve the previous set of data:

```
$ curl -X GET -d 'where={"_id":{"$gt":"5418a87f5a6919fde8cee391"}}'
"http://<HOST>/v1/statuses/query.json?key=<KEY>&count=true&pretty_json=t&_session_id=<SESSION_ID>"
```

To query objects between a range of object IDs, use together $gt and $lt together:

```
curl -X GET -d 'where={"_id":{"$gt":"5418a87f5a6919fde8cee38f", "$lt":"5418a8815a6919fde8cf1e4d"}}'
"http://<HOST>/v1/statuses/query.json?key=<KEY>&count=true&pretty_json=t&_session_id=<SESSION_ID>"
```

For additional examples, see [Range-based Query Pagination Examples](#Range-basedQueryPaginationExamples).

### Range-based query pagination examples

* Query on Custom Field, Results in Ascending Order

* Query on Custom Field, Results in Descending Order

* Query for the Next Page of Results, Results in Ascending Order

* Query for the Previous Page of Results

#### Query on a custom field with results in ascending order

In this example, the query returns Statuses objects whose custom score field is less than 100 and sorts results on the score in ascending order (&order=score). The query matches 100 total records.

```
~ curl -d 'where={"score":{"$lt":100}}&order=score' -X GET
"http://<HOST>:8082/v1/statuses/query.json?key=<KEY>&count=true&pretty_json=true"
{
  "meta": {
    "code": 200,
    "status": "ok",
    "method_name": "queryStatuses",
    "count": 100
  },
  "response": {
    "statuses": [
      {
        "id": "53fe1c25759220e9f675413a",
        "custom_fields": {
          "score": 0.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675413b",
        "message": "status",
        "custom_fields": {
          "score": 1.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675413c",
        "custom_fields": {
          "score": 2.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675413d",
        "custom_fields": {
          "score": 3.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675413e",
        "custom_fields": {
          "score": 4.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675413f",
        "custom_fields": {
          "score": 5.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754140",
        "custom_fields": {
          "score": 6.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754141",
        "custom_fields": {
          "score": 7.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754142",
        "custom_fields": {
          "score": 8.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754143",
        "custom_fields": {
          "score": 9.0
        }, ...
      }
    ]
  }
}
```

#### Query on a custom field with results in descending order

In this example, status objects are queried whose custom score field is less than 100 and sorts results on score in descending order (&order=-score).

```
$ curl -d 'where={"score":{"$lt":100}}&order=-score' -X GET
"http://<HOST>/v1/statuses/query.json?key=<KEY>&count=true&pretty_json=true"
{
  "meta": {
    "code": 200,
    "status": "ok",
    "method_name": "queryStatuses",
    "count": 100
  },
  "response": {
    "statuses": [
      {
        "id": "53fe1c25759220e9f675419d",
        "custom_fields": {
          "score" 99.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675419c",
        "custom_fields": {
          "score" 98.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675419b",
        "custom_fields": {
          "score" 97.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675419a",
        "custom_fields": {
          "score" 96.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754199",
        "custom_fields": {
          "score" 95.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754198",
        "custom_fields": {
          "score" 94.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754197",
        "custom_fields": {
          "score" 93.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754196",
        "custom_fields": {
          "score" 92.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754195",
        "custom_fields": {
          "score" 91.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754194",
        "custom_fields": {
          "score" 90.0
        }, ...
      }
    ]
  }
}
```

#### Query for the next page of results with results in ascending order

In this example, the next page of status objects is queried whose \_id field is less than "53fe1c25759220e9f6754194" and sorted in descending order on the custom score field.

```
$ curl -d 'where={"score":{"$lt":100},"_id":{"$lt":"53fe1c25759220e9f6754194"}}&order=-score' -X GET
"http://<HOST>/v1/statuses/query.json?key=<KEY>&count=true&pretty_json=true"
{
  "meta": {
    "code": 200,
    "status": "ok",
    "method_name": "queryStatuses",
    "count": 90
  },
  "response": {
    "statuses": [
      {
        "id": "53fe1c25759220e9f6754193",
        "custom_fields": {
          "score": 89.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754192",
        "custom_fields": {
          "score": 88.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754191",
        "custom_fields": {
          "score": 87.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f6754190",
        "custom_fields": {
          "score": 86.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675418f",
        "custom_fields": {
          "score": 85.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675418e",
        "custom_fields": {
          "score": 84.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675418d",
        "custom_fields": {
          "score": 83.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675418c",
        "custom_fields": {
          "score": 82.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675418b",
        "custom_fields": {
          "score": 81.0
        }, ...
      },
      {
        "id": "53fe1c25759220e9f675418a",
        "custom_fields": {
          "score": 80.0
        }, ...
      }
    ]
  }
}
```

#### Query for the previous page of results

As explained previously, to get the second (or next) page of results in a query, you query for objects whose \_id field is less (older) than the \_id of the last object returned by the prior query. To get the previous (first) page of results again, you query for those objects whose \_id is greater (newer) than the first object returned in by the prior query.

However, if you query for the third results page, and you want to get the previous (second) results page, you need to restrict the query to those objects whose \_id is greater than the first object returned by the most recent query (third results page), and less than that of the last object returned in the query before that (second results page); or, equivalently, less than or equal to the first object returned in the initial query (first results page). The following demonstrates this.

**First page (page 1)**

The first query request doesn't specify a range.

Request:

```
curl -X GET "<HOST>/v1/users/query.json?key=<KEY>&new_pagination=true&pretty_json=true"
```

Response (abbreviated):

```
{
  "response": {
    "users": [
      {
        "id": "5447f04580e61e081e0002c6",
        ...
      },
      ...
      {
        "id": "5447eff680e61e08260002ed",
        ...
      }
    ]
  }
}
```

Note that the ID of the last object returned in the response ("5447eff680e61e08260002ed").

**Next page (page 2)**

To get Page 2 results, a where clause is added that limits the results to those objects whose \_id field is less than the last object on Page 1 results ("5447eff680e61e08260002ed").

Request:

```
curl -X GET -d 'where={"_id":{"$lt":"5447eff680e61e08260002ed"}}'
"<HOST>/v1/users/query.json?key=<KEY>&new_pagination=true&pretty_json=true"
```

Response (abbreviated):

```
{
  "response": {
    "users": [
      {
        "id": "5447efed80e61e08260002ec",
        ...
      },
        ...
      {
        "id": "5447ef9f80e61e081e0002c1",
        ...
      }
    ]
  }
}
```

Note that the first and last IDs of objects returned on Page 2 are "5447efed80e61e08260002ec" and "5447ef9f80e61e081e0002c1", respectively. To get the previous page of results (Page 1) at this point, you could query for objects with IDs greater than the first object in the Page 2 results ("5447efed80e61e08260002ec"). In this case, however, the user requests the next page (Page 3) results, as shown below.

**Next page (page 3)**

To get Page 3 results, the where limits results to those objects whose \_id field is less the last object returned in Page 2 results ("5447ef9f80e61e081e0002c1").

```
$ curl -X GET -d 'where={"_id":{"$lt":"5447ef9f80e61e081e0002c1"}}'
"<HOST>/v1/users/query.json?key=<KEY>&new_pagination=true&pretty_json=true"
```

Response (abbreviated):

```
{
  "response": {
    "users": [
      {
        "id": "5446d5d980e61e0826000093",
        ...
      },
      ...
    ]
  }
}
```

Note that the first object returned has the ID "5446d5d980e61e0826000093".

**Previous page (page 2)**

At this point, if you query for objects with IDs greater than the first object returned in Page 3, you would, logically, get Page 1 results, not Page 2. Instead, you need to further limit the range to those objects with IDs less than or equal to that of the first object from the Page 2 results; or, equivalently, less than that of the last object id from Page 1 results.

Continuing the example, the request and response (abbreviated) for these approaches are shown below:

```
$ curl -X GET -d 'where={"_id":{"$gt":"5446d5d980e61e0826000093", "$lte":"5447efed80e61e08260002ec"}}'
"<HOST>/v1/users/query.json?key=<KEY>&new_pagination=true&pretty_json=true"
{
  "response": {
    "users": [
      {
        "id": "5447efed80e61e08260002ec",
        ...
      },
      ...
      {
        "id": "5447ef9f80e61e081e0002c1",
        ...
    ]
  }
}

$ curl -X GET -d 'where={"_id":{"$gt":"5446d5d980e61e0826000093", "$lt":"5447eff680e61e08260002ed"}}'
"<HOST>/v1/users/query.json?key=<KEY>&new_pagination=true&pretty_json=true"
{
  "response": {
    "users": [
      {
        "id": "5447efed80e61e08260002ec",
        ...
      },
      ...
      {
        "id": "5447ef9f80e61e081e0002c1",
        ...
      }
    ]
  }
}
```

## Search API overview

{{% alert title="⚠️ Warning" color="primary" %}}The search API is deprecated since Release 1.3.0. Applications created before Arrow Cloud Release 1.3.0 can continue to use the deprecated search API, but new applications will need to use the query API with the $text query operator.{{% /alert %}}

Several MBS objects provide a search API that performs a case-insensitive, full-text search of the given keywords on a list of predefined fields. Please refer to individual object's API documentation for a list of searchable fields. For instance, the [Places.search](/arrowdb/latest/#!/api/Places-method-search) method will search within [Places.name](/arrowdb/latest/#!/api/Places-property-name) and [Places.tags](/arrowdb/latest/#!/api/Places-property-tags).

The Search API is fixed in terms of the searchable fields; use the [query](#QueryAPIAvailability) API to perform more flexible searches.

### Search API parameters

The following parameters are available for search operations:

* page

* per\_page

* q

#### page

Request page number starting at 1. The default is 1.

#### per\_page

The number of results per page. The default is 10.

#### q

The keyword or phrase for which to search.

### Search API availability

Search methods are available for the following pre-built MBS objects, as well as for custom fields.

* [Events](/arrowdb/latest/#!/api/Events-method-search)

* [Friends](/arrowdb/latest/#!/api/Friends-method-search)

* [Places](/arrowdb/latest/#!/api/Places)

* [Users](/arrowdb/latest/#!/api/Users)
