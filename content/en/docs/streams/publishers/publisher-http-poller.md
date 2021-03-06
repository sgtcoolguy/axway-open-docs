---
title: HTTP Poller Publisher
linkTitle: HTTP Poller Publisher
weight: 150
date: 2019-04-02
description: Learn how to configure a topic associated to a HTTP Poller publisher.
---

## HTTP Poller Publisher

Polling describes the mechanism used to retrieve data from an API: the client first needs to send a request to a server and the server responds by sending the requested data.
Since it is not possible for the client to know when the data is updated, it usually sends requests as often as possible to try to stick to reality and ends up using a lot of bandwidth and resources to receive the same data several times.
Streams provides the ability to instantly turns any request/response API into a real-time event-driven data feed: The HTTP poller publisher will poll the target URL at the given period and publish the content in the associated topic.
Streams will then fan out the content (snapshot, computed patches) to all subscribed client as soon as a change is detected in the response of the target URL.

### http-poller publisher configuration

The http-poller publisher requires some specific configuration.

| Attribute     | Mandatory | Default Value  | Description            |
|---------------|:---------:|----------------|------------------------|
| url           | yes       | none           | Target URL to request  |
| pollingPeriod | no        | PT5S (5 sec)   | Period at witch the target URL will be requested. Min: PT0.5S Max: PT1H. Visit [ISO-8601 format](https://en.wikipedia.org/wiki/ISO_8601#Durations) for details. |
| headers       | no        | none           | Map of key/value pairs that will be injected as HTTP headers when requesting the target URL |

```json
{
  "name": "myHttpPollerTopic",
  "publisher": {
    "type": "http-poller",
    "config": {
        "url": "target URL",
        "pollingPeriod": "PT5S",
        "headers": {
            "CustomHeader": "value",
            "CustomHeader2": "value1,value2",
            ...
        }
    }
  }
}
```

### Removing http headers from configuration

In order to remove a header from publisher's configuration, set its value to `null` when calling `PATCH /topics/{{topicId}}` endpoint:

```json
{
  "publisher": {
    "config": {
        "headers": {
            "CustomHeader": null,
        }
    }
  }
}
```
