---
title: "GET /cdpPolicies/{ID}/includes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdppolicies_id_includes.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a collection of VMs and VM containers processed by the CDP policy having the specified ID.

Request

To get a list of all VMs and VM containers processed by the CDP policy, send the GET HTTP request to the /cdpPolicies/{ID}/includes resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpPolicies/{ID}/includes |

Request Headers

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

In the response body, the REST API returns a representation of the /cdpPolicies/{ID}/includes resource collection.

Example

A sample request below returns a list of VMs and VM containers processed by the CDP policy having ID bc933bb6-0cc5-47b6-a1ec-e062b9e29877.

|  |
| --- |
| Request:  GET https://localhost:9398/api/jobs/bc933bb6-0cc5-47b6-a1ec-e062b9e29877/includes    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <ObjectsInJob xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
