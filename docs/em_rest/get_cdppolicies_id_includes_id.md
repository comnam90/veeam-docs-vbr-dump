---
title: "GET /cdpPolicies/{ID}/includes/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdppolicies_id_includes_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a representation of a VM or a VM container having the specified ID and processed by the CDP policy having the specified ID.

Request

To get a representation of a VM or a VM container processed by the CDP policy, send the GET HTTP request to the /cdpPolicies/{ID}/includes/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpPolicies/{ID}/includes/{ID} |

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

In the response body, the REST API returns the /cdpPolicies/{ID}/includes/{ID} resource that contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| ObjectInJobId | String | ID of the VM or VM container processed by the CDP policy, for example: e310aa12-eff2-41f4-97c8-631b677fc17f. |
| HierarchyObjRef | HierarchyObjRefType | Reference to the VM or VM container added to the CDP policy, for example: urn:VMware:Vm:d68c782f-ec0a-4bf3-b3c1-04c552b64fdf.vm-85541. |
| Name | String | Name of the VM or VM container processed by the CDP policy, for example: DC-SRV. |
| DisplayName | String | Display name of the VM or VM container processed by the CDP policy, for example: DC-SRV. |
| GuestProcessingOptions | GuestProcessingOptionsType | Options for application-aware image processing. For details, see [Guest Processing Options](cdp_guestprocessingoptions.md). |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /cdpPolicies/{ID} | Up | URL of the [/jobs/{ID}](jobs_id.md) resource — a CDP policy that processes the object. |
| /cdpPolicies/{ID}/includes/{ID} | Delete | URL for the [DELETE /cdpPolicies/{ID}/includes/{ID}](delete_cdppolicies_id_includes_id.md) request. |

Example

A sample request below returns a resource representation of the VM having ID 7493cec7-e8d9-4d88-b5e9-8fc651370462 that is processed by the CDP policy having ID 872a3860-3805-43b8-bcf6-388384bfed33.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33/includes/7493cec7-e8d9-4d88-b5e9-8fc651370462    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
