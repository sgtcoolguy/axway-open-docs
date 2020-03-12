{"title":"AMPLIFY Runtime Services Best Practices","weight":"10"} 

This topic provides best practices for creating and deploying applications to AMPLIFY Runtime Services (API Runtime Services).

## Improving application network performance

The distance between a server and client can increase the network latency of your application experiences. The AMPLIFY Runtime Services data center is in Oregon, USA. Your application users might be anywhere, so it's essential to understand how you can reduce network latency in your application.

*   **Use data caching**. Use an in-memory data cache in your AMPLIFY Runtime Services application, when possible, to minimize network requests or file reads that can significantly improve overall application performance. For instance, if your application makes a query that is not time-sensitive, cache the result of the first query for an appropriate period.
    
*   **Minimize the size of the response payload.** Enable ZIP data compression in your responses. Only include data essential to the current state of the application. A common approach to improve mobile application performance is to use one API call to synchronously retrieve a minimum data set to display on the device, and then one or more asynchronous calls to load additional data as needed. This guideline applies to network calls issued from within the app and calls to users to initiate the app.
    
*   **Avoid using AMPLIFY Runtime Services to transfer large sets of data to clients**. If your application aggregates large sets of data that don't change often, you can increase performance by uploading those assets to online storage or a content delivery network (CDN), such as [Amazon S3](http://aws.amazon.com/s3/) or [Amazon CloudFront](http://aws.amazon.com/cloudfront/). The client would make an API call to AMPLIFY Runtime Services to obtain the URL of the CDN-hosted data, and then make another API call using this URL to download the real data.
    
*   **Use a CDN to store static content**. In general, your application should not be used to serve lots of static assets. Developers are encouraged to move all of their application's static content to a CDN and have the client load those assets from there.
    

## Improving application performance and memory usage

**Minimize output logs.** To improve application performance and reduce memory consumption, minimize the number of console logs your application produces.

## Monitoring published applications

**Monitor published applications.** The status of your applications that are published to a production environment should be monitored using Pingdom, New Relic, or a similar website performance monitoring program. For information on Pingdom, refer to the [Pingdom](https://www.pingdom.com/) website. For information on New Relic, refer to the [New Relic](https://newrelic.com/) website.