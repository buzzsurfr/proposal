# enkuklio

_A global API registry_

## Name Origin

_Enkuklio_ is a variation from the Modern Latin phrase for encyclopedia. _enkuklios paideia_ traslates literally to "all-round education".

There exists a reverse translation: enkuklio is Esperanto for "inkwell".

## Problem

APIs have been around since the 1940s, but were made popular around 2004[¹](#references)--when technology and software stopped relying on a “human” component for data. Prior to that, client/server was the basic model in which a full client was written and shipped. In order to facilitate faster use, CLIs were made popular to allow administrators and developers to move faster. APIs are ultimately for allowing applications to talk to each other, and there has been a steady evolution in the protocols used for different applications to talk to each other.

However, collecting the details of applications from a global perspective has limited support within the community (see [Alternate Solutions and Considerations](#alternate-solutions-and-considerations)). A solution is needed where companies and organizations can catalog their applications (and sub-resources) across a wide array of compute locations, including cloud, on-prem, data center, private WAN, and third-party services. Many companies have older applications and APIs that use different protocols, and the goal of enkuklio is to identify _ALL_ of them.

## Tenets

1. Human-readable collection/registry/catalog of APIs.
2. Identify the services and functions within those APIs.
3. Globally distributable set.
4. No dependencies on any of the applications or their environments.

## Protocol Support

The list of protocols that may be supported include (but not limited to, can add more if there's a community need):

* JSON-RPC
* XML-RPC
* HTTP
* MQTT
* Webhooks 
* SOAP
* REST
* GraphQL
* gRPC
* WSDL/WADL
* XML
* OpenAPI
* AsyncAPI
* Kafka Connect
* Avro

There are advantages and disadvantages to the different protocols, but the purpose of this project is to catalog them and not to compare them.

## Research

There are other application registries/API registries that exist, but they focus on consolidation of the services and functions into a centralized gateway. Instead, we want to focus on identifying the different APIs as a distributed set and provide both human-readable and programmatic means to discover those APIs, services, and functions, regardless of the protocol.

Since APIs often reflect the core business values and purpose, often there are more than one API or gateway that represents the same service, or more than one service that represents the same function. The goal is to identify those cases as a framework for building distributed routing rules over a global context (e.g. “global mesh”). The identification of these pieces is why there’s not a good global mesh solution today.

### Alternate Solutions and Considerations

* Google API Registry API
  * https://opensource.googleblog.com/2021/01/the-api-registry-api.html
  * Only for Google APIs
  * Only allows for discovery of APIs not of specific services or functions
* Apigee Registry
  * https://github.com/apigee/registry
* Apicurio
  * https://apicur.io
  * Only a schema registry
* Many DNS solutions
  * Amazon Route 53
  * GSLB
  * Only focused on DNS, which solves problem from a network layer but doesn’t understand application layer
  * Most solutions that try (using SRV records) can’t get detailed enough for what we need here.
* Network Service Mesh
  * https://networkservicemesh.io
* AWS Service Catalog
  * Focused on the components of the applications
  * but some of the registry concepts apply
* Backstage.io 
  * Correct model for discovery, but not extensible/relatable enough
  * No concept of multiple endpoint
  * Not distributed design
  * This might actually work. It’s a CNCF sandbox project, and if we can get the necessary tweaks in (to support services and possibly functions), then we may be able to make it work.

## Design

There are two primary components to this platform:
* Registry, where APIs are stored and updated based upon metadata
* Discovery, allowing to query/search based on parameters/attributes/etc

### Registry

Registry will keep track of APIs, services, and functions as baseline resources.

Metadata for APIs will include a version (as path or tag), schema, and endpoints. There has to be a way to uniquely identify APIs as well as tell if they are the same API with multiple endpoints.

Schema should be detected automatically but allow for manual configuration as well

One important function (for future features) is tracking multiple endpoints of the same service/API. This will be used for a future feature to start setting up for a true “global mesh” or intelligent disaster recovery/high availability.

### Discovery

Discovery should not be inline for anything. There’s no need, and that’s another service.

Discovery will have multiple modes.

* DNS which is targeted around TCP or non-application-aware applications. DNS discovery can discover API endpoints fairly easily, but cannot find services without using SRV records and won’t easily discover functions.
* API (inception) where you can get application-aware context for APIs, services, and functions. The actual API can be gRPC, GraphQL, REST, or really anything—but should be dynamically built and configurable.


## References

1. ^ Kin Lane (2019). _Intro to APIs: History of APIs_. https://blog.postman.com/intro-to-apis-history-of-apis/