---
title: "get_cloudfailoverplans_id_includes"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudfailoverplans_id_includes.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a list of VMs added to the cloud failover plan that has the specified ID.

Request

To get a list of all VMs added to the cloud failover plan, send the GET HTTP request to the /cloud/cloudFailoverPlans/{ID}/includes resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID}/includes |

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

In the response body, the REST API returns a representation of the /cloud/cloudFailoverPlans/{ID}/includes resource collection.

Example

The example below returns a list of VMs added to the cloud failover plan that has ID e8d3df9a-70ba-492e-b39d-ab772e7defd5.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/cloudFailoverPlans/e8d3df9a-70ba-492e-b39d-ab772e7defd5/includes    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
