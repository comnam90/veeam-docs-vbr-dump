---
title: "get_lookup"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_lookup.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of the [Virtual Infrastructure Lookup](lookup_service.md).

Request

To get a resource of a specific virtual infrastructure object, the client needs to send a request of the following type:

HTTP Request

|  |
| --- |
| GET https://localhost:9398/api/lookup?&hierarchyRef={hierarchyRef} |

or

|  |
| --- |
| GET https://localhost:9398/api/lookup?host={hostUID}&name={objName}&type={objType} |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /lookup resource.

Example

The sample request below returns an object of the VM named DNS; the VM is registered on the Hyper-V host having ID 3a70aa9075-ca31-43bd-99cc-f888b969799b:

|  |
| --- |
| Request:  GET https://localhost:9398/api/lookup?host=urn:veeam:HierarchyRoot:70aa9075-ca31-43bd-99cc-f888b969799b&name=dns&type=vm    Request Header:  X-RestSvcSessionId  NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <HierarchyItems xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
