{"title":"Axway API Builder","weight":"50"}

{{% alert title="❗️ Warning" color="danger" %}}*API Builder 3.x is deprecated*

Support for API Builder 3.x will cease on 30 April 2020. Use the [v3 to v4 upgrade guide](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_v3_to_v4_upgrade_guide.html) to migrate all your applications to [API Builder 4.x](https://docs.axway.com/bundle/API_Builder_4x_allOS_en/page/api_builder_getting_started_guide.html).

Contact [support@axway.com](mailto:support@axway.com) if you require migration assistance.{{% /alert %}}

## At a Glance

Axway API Builder is an opinionated framework to build and deploy applications to the cloud.

### API Builder

API Builder lets you build and deploy API endpoints that can be consumed by any client application. API Builder applications are made up of several components:

* **API Builder APIs** can be defined in two ways:

    * **Programmatically**: Defined in JavaScript via the API Builder API. These are custom endpoints that allow you to access and execute custom operations on data.

    * **Configuration**: Defined as Swagger 2.0 document. These are files which describe and document RESTful APIs which are composed of one or more endpoints.

* **API Builder Blocks** are filters that allow you to pre- or post-process data

* **API Builder Codeblocks** are flow-nodes which can be used within Flows to implement advanced business logic not possible through the configuration of supplied flow-nodes alone

* **API Builder Connectors** are adapters that allow you to read and write data to and from an external data source, such as [Mobile Backend Services](/docs/appc/Mobile_Backend_Services/), MySQL, Salesforce, and MongoDB, or in server memory

* **API Builder Endpoints** are endpoints as described by a configuration-based API

* **API Builder Flows** are graphs of pre-defined flow-nodes which are used to implement the business logic of an endpoint

* **API Builder Models** are structured data with predefined API endpoints to access them

**Relevant Topics:** [API Builder Getting Started Guide](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Getting_Started_Guide/), [API Builder Project](/docs/appc/Axway_API_Builder/API_Builder/API_Builder_Developer_Guide/API_Builder_Project/), [API Builder API reference](#!/api/Arrow)

### AMPLIFY Runtime Services

AMPLIFY Runtime Services hosts applications, built with API Builder, and Appcelerator pre-built services, which includes the Mobile Backend Services.

* **Mobile Backend Services** (formerly known as ArrowDB) provides pre-built REST objects, such as Users or Photos. Mobile Backend Services can be integrated with your Titanium, Node.js, Android, or iOS application.

* **Mobile Backend Services** provides the ability to send push notifications to Android and iOS devices subscribed to push channels. Mobile Backend Services can be integrated with your Titanium, Android or iOS application.

**Relevant Topics**: [AMPLIFY Runtime Services](/docs/appc/AMPLIFY_Runtime_Services/), [Mobile Backend Services](/docs/appc/Mobile_Backend_Services/)
