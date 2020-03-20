{"title":"ACS 1.1.5 - 15 September 2014","weight":"50"}

The 1.1.5 release of Appcelerator Cloud Services includes the following new features and bug fixes.

## New features and behavior changes

* **New Paging Restriction on Queries** — Previously, if a query matched 1 million records (for example) ACS performed a sort and limit on those records in memory, which was highly inefficient. There is now a "hard stop" on queries at 5000 records. This means that if a query matches 1 million records, ACS will only look at the first 5000, in random order, and then sort on them. To narrow down query results, developers should now use range-based queries using a where clause. See the [documentation and examples](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Search_and_Query_APIs/) for more information.

* A new parameter named **count** has been added to all query methods. When a query contains count=true as a parameter, the meta object in the response contains a count field whose value is the total number of objects that matched the query. See the examples for more information.

* The page and per\_page query parameters are no longer supported in ACS 1.1.5, and responses do not contain page, per\_page, total\_pages, or total\_results fields. Applications created with ACS 1.1.4 and earlier can continue to these parameters, but they will eventually be deprecated and removed. Developers are encouraged to migrate their applications to use the [range-based queries](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Search_and_Query_APIs/) available in ACS 1.1.5.

* **Batch delete** — [Batch delete](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Admin_Access/) of ACS objects is now performed asynchronously in a separate process, rather than immediately on method invocation.

* **Deleted Objects and Dependencies** — When an object is deleted that has dependencies, the dependent objects are not deleted. For instance, if you delete a Users object that had a [Photos](/arrowdb/latest/#!/api/Photos) object specified as the user's primary photo, the corresponding Photos object is not deleted.

* **Wildcard regular expressions** are now not allowed in [query operations](/docs/appc/Mobile_Backend_Services/Mobile_Backend_Services_Guide/Search_and_Query_APIs/). For example, the ACS query where="color": {"$regex" :"^.\*b"} will result in the following error:

    ```
    This regex query is not supported, regex expression should start with ^letter or ^digit.
    ```

* When [creating an ACL](/arrowdb/latest/#!/api/ACLs) the public\_read and public\_write parameters must now be strings

* The **[CustomObjects.count](/arrowdb/latest/#!/api/CustomObjects-method-count)** method has been modified to include the object type in the request (objects/<object>/count.json, for example), and only returns the count for the specified type. The count field is returned in the meta JSON response object, and not in the response object.

    ```
    $ curl -X GET "http://${HOST}/v1/car/count.json?key=${KEY}&pretty_json=true"
      {
        "meta": {
          "code": 200,
          "status": "ok",
          "method_name": "objectsCount",
          "count": 15
      }
    ```

* The response of count methods for all ACS objects now includes a method\_name field, and the count field is included in the meta object and not the response object.

    ```
    $ curl -X GET "http://${HOST}/v1/checkins/count.json?key=${KEY}&pretty_json=true"
    {
      "meta": {
        "code": 200,
        "status": "ok",
        "method_name": "checkinsCount",
        "count": 15
    }
    ```

## Bug fix

* Fixed an issue where subscribing a device using the subscribe\_token method did not increment the application's push notifications count.
