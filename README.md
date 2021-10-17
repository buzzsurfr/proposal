# enkuklio

_A global API registry_

## Name Origin

_Enkuklio_ is a variation from the Modern Latin phrase for encyclopedia. _enkuklios paideia_ traslates literally to "all-round education".

There exists a reverse translation: enkuklio is Esperanto for "inkwell".

## Problem

APIs have been around since the 1940s, but were made popular around 2004[¹](#references)--when technology and software stopped relying on a “human” component for data. Prior to that, client/server was the basic model in which a full client was written and shipped. In order to facilitate faster use, CLIs were made popular to allow administrators and developers to move faster. APIs are ultimately for allowing applications to talk to each other, and there has been a steady evolution in the protocols used for different applications to talk to each other.

However, collecting the details of applications from a global perspective has limited support within the community (see [Alternate Solutions and Considerations](#alternate-solutions-and-considerations)). A solution is needed where companies and organizations can catalog their applications (and sub-resources) across a wide array of compute locations, including cloud, on-prem, data center, private WAN, and third-party services. Many companies have older applications and APIs that use different protocols, and the goal of enkuklio is to identify _ALL_ of them.

### Protocol Support

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

### Alternate Solutions and Considerations

## References

1. ^ Kin Lane (2019). _Intro to APIs: History of APIs_. https://blog.postman.com/intro-to-apis-history-of-apis/