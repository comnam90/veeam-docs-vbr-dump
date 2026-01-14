---
title: "get_tenants_id_subtenants"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tenants_id_subtenants.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a list of subtenant accounts created for the tenant account with the specified ID.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of subtenants accounts, send the [GET /query?type=CloudSubtenant](get_query_cloudsubtenant.md) request. |

Request

To get a list of subtenant accounts, send the GET HTTP request to the /cloud/tenants/{ID}/subtenants resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/subtenants |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/subtenants resource.

Example

The example below returns a list of subtenant accounts created for the tenant account with ID 28ddf9b9-12fa-431a-a34c-a327f05c3920.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CloudSubtenants xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
