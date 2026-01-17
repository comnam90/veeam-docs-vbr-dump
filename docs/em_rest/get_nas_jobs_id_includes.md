---
title: "GET /nas/jobs/{ID}/includes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas_jobs_id_includes.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /nas/jobs/{ID}/includes


Returns a list of files and folders processed by file share backup job having the specified ID.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of files and folders processed by file share backup job, send the [GET /query?type=NasObject](get_query_nasobject.md) request. |

Request

To get a list of all files and folders processed by the file share backup job, send the GET HTTP request to the /nas/jobs/{ID}/includes resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/jobs/{ID}/includes |

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

In the response body, the REST API returns a representation of the /nas/jobs/{ID}/includes resource collection.

Example

The example below returns a list of files and folders processed by the file share backup job having ID 93dfbb3e-f420-45cf-addc-4ee9297113f2.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/includes    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <NASObjects xmlns="http://www.veeam.com/ent/v1.0"> |


