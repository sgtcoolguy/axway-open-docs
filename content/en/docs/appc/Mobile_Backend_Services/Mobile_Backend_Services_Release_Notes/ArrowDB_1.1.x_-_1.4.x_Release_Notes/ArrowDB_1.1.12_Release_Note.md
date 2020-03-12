{"title":"ArrowDB 1.1.12 - 05 May 2015","weight":"50"}

## New features

* Add ability to set private file permission on File objects using the s3\_acl field. When creating or updating a File object, set the s3\_acl field to private to only allow logged-in users to access the file. The retrieved URL will be temporary and expire, by default, after five minutes. You can adjust the expiration time with the query or show method's expires field. Previously, all files without an access control list were public.

* Add ability to update the owner of a Place object using the user\_id field. When using the update method, set the user\_id field to the ID of the new owner.


## Bug fix

* Fixed an issue where email templates were failing to insert passed parameters.
