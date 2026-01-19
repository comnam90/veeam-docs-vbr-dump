---
title: "GET /agents/jobs/{ID}/includes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_jobs_id_includes.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /agents/jobs/{ID}/includes


Returns a collection of protected computers and protection groups processed by the Veeam Agent backup job with the specified ID.

Request

To get a list of all protected computers and protection groups processed by the Veeam Agent backup job, send the GET HTTP request to the /agents/jobs/{ID}/includes resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/jobs/{ID}/includes |

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

In the response body, the REST API returns a representation of the /agents/jobs/{ID}/includes resource collection.

Example

The example below returns a list of of protected computers and protection groups processed by the Veeam Agent backup job having ID b9b42e54-0e9e-42d0-a2f0-b0138596b537.

|  |
| --- |
| Request:  GET https://enterprise06.tech.local:9398/api/agents/jobs/b9b42e54-0e9e-42d0-a2f0-b0138596b537/includes    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |


