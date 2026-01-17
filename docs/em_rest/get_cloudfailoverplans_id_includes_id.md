---
title: "GET /cloud/cloudFailoverPlans/{ID}/includes/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudfailoverplans_id_includes_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /cloud/cloudFailoverPlans/{ID}/includes/{ID}


Returns a representation of a VM with the specified ID that is added to the cloud failover plan with the specified ID.

Request

To get a representation of a VM added to the cloud failover plan, send the GET HTTP request to the /cloud/cloudFailoverPlans/{ID}/includes/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID}/includes/{ID} |

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

In the response body, the REST API returns the /cloud/cloudFailoverPlans/{ID}/includes/{ID} resource that contains the following parameters.

| Element | Type | Description |
| --- | --- | --- |
| FailoverPlanVMId | String | ID of the VM added to the cloud failover plan, for example: 231a6e3e-09e6-4641-9322-40898fcb966a. |
| Name | String | Name of the VM added to the cloud failover plan, for example: DC-SRV. |
| Order | Int | Order number for processing the VM by the cloud failover plan. The processing sequence starts with 0. |

Example

The example below returns a reference resource representation of the VM with ID 592cd62d-c7a2-4f19-a545-ed73ab696e42 that is processed by the cloud failover plan with ID e8d3df9a-70ba-492e-b39d-ab772e7defd5.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/cloudFailoverPlans/e8d3df9a-70ba-492e-b39d-ab772e7defd5/includes/592cd62d-c7a2-4f19-a545-ed73ab696e42    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |


