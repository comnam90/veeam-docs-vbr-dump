---
title: "Specifications"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/em_web_api_specifications.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

In this section, you will find general notes and requirements on how to work with the Veeam Backup Enterprise Manager REST API.

Transport Protocol

Veeam Backup Enterprise Manager REST API is based on Hypertext Transfer Protocol version 1.1. For secure connections, the REST API can be used over HTTPS. For details, see the [TLS Certificate](ssl_encryption.md) section.

Media Type

Veeam Backup Enterprise Manager REST API resources are represented in XML and JSON formats. The media type is defined in the Content-Type request header. For details, see the [Header Format](em_web_api_specifications.md#header_format) section.

If you use XML, ensure that the order of parameters in the request body of POST and PUT requests is correct. For more information about the required parameter order, see request body examples for the relevant request.

XML Schema Definitions

All resources and specifications in the Veeam Backup Enterprise Manager REST API are described in the RestAPI.xsd file based on the XML schema definition. The XSD file defines the structure, content and semantics of elements and types used in the Veeam Backup Enterprise Manager REST API. Third-party tools and libraries can use the XSD file to generate data structures that represent elements described by the XML schema.

You can find the XSD specification file in the installation folder of Veeam Backup Enterprise Manager.

* For Enterprise Manager on Microsoft Windows: %Program Files%\Veeam\Backup and Replication\Enterprise Manager\schemas\RestAPI.xsd
* For Enterprise Manager on Linux: /opt/veeam/vbem/schemas/RestAPI.xsd

Header Format

In the Veeam Backup Enterprise Manager REST API, the client and the server include specific headers in request and response message.

Request Header

The following headers are used in the HTTP requests:

| Header | Description | Value | Required/Optional |
| --- | --- | --- | --- |
| Authorization | Identifies an authenticated user who makes requests to the server. | Basic username:password (base64 encoded) | Must be sent with a request for creating a new logon session. For details, see the [HTTP Authentication](http_authentication.md) session. |
| Content-Type | Identifies the media type and syntax of the request body message. | application/xml | Must be sent with all requests that have a request body message. |
| X-RestSvcSessionId | Identifies a logon session used to work with Enterprise Manager REST API. | Session ID copied from the server reply to the Create new logon session request. | Must be sent with all requests to the server. For details, see the [HTTP Authentication](http_authentication.md) session. |
| Accept | Identifies the media type and syntax of the response. | application/xml or application/json | Must be sent with requests that require response in the JSON format.  Can be sent with requests that require response in the XML format. If a request does not contain the header, the server will return a response in the XML format as well. |

Response Header

In server responses sent to the client from the server, the following headers are used:

| Header | Description | Value | Required/Optional |
| --- | --- | --- | --- |
| Content-Length | Identifies the length of the response body message. | Length of the response body message in bytes. | Contained in all responses with the response body message. |
| Content-Type | Identifies the media type and syntax of the response body message. | application/xml or application/json | Contained in all responses with the response body message. |
| Location | Contains a URL for the resource that was created in response to the POST HTTP request. | URL for the created resource. | Contained in responses to the POST HTTP requests |
| X-RestSvcSessionId | Contains an ID for a new logon session. | ID of the created logon session. | Contained in the response to the Create new logon session request. For details, see the [HTTP Authentication](http_authentication.md) session. |
| Set-Cookie | Contains the X-RestSvcSessionId header for a new logon session. | X-RestSvcSessionId header and its value — ID of the created logon session. | Contained in the response to the Create new logon session request. For details, see the [HTTP Authentication](http_authentication.md) session. |

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
