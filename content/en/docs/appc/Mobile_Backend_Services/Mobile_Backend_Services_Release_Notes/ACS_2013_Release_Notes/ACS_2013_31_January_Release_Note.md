{"title":"ACS 2013 31 January Release Note","weight":"140"}

Fixed an unhandled exception when a file was passed as the payload of a push notification. For example, a curl command like this would cause an exception:

```
curl -b cookies.txt -c cookies.txt -F "channel=change_request" -F "to_ids=<ids>"
-F "payload=@photo2.jpg"
https://api.cloud.appcelerator.com/v1/push_notification/notify.json?key=<api_key>
```

File payloads are not allowed. With the fix, ACS supplies an error message instead of throwing an exception.
