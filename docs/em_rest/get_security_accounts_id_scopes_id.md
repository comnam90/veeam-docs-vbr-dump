---
title: "GET /security/accounts/{ID}/scopes/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_security_accounts_id_scopes_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a restore scope having the specified ID. The scope is defined for the account that is added to Veeam Backup Enterprise Manager and is assigned a specific security role.

Request

To get a restore scope defined for the account having the specified ID, send the GET HTTP request to the /security/accounts/{ID}/scopes/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/scopes/{ID} |

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

In the response body, the REST API returns the /security/accounts/{ID}/scopes/{ID} resource that contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| Name | String | Name of the virtualization object assigned as a scope, for example: Enterprise. |
| HierarchyRootName | String | ID of the hierarchy root object assigned as a scope, for example: 24a14898-77d0-4881-bbf8-c8ba71ce4d55. |
| Platform | String | Platform of the virtualization object. Possible values:   * VMware * Hyperv * vCloud |
| HierarchyObjectType | String | Type of the hierarchy object, for example: ResourcePool, VcdSystem. |
| State | String | State of the session that processes the scope. Possible values:   * Unprocessed * Processed * Removing |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /security/accounts/{ID}/scopes/{ID} | Delete | URL for the [DELETE /security/accounts /{ID}/scopes/{ID}](delete_security_accounts_id_scopes_id.md) request. |

Example

The example below returns a restore scope having ID bceb75f9-5c10-4f39-9eb5-c000a2fabaee for the account having ID de19303b-bcf3-428b-b113-ac0b2cf46bd7.

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7/scopes/bceb75f9-5c10-4f39-9eb5-c000a2fabaee    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EnterpriseAccountHierarchyScope xmlns="http://www.veeam.com/ent/v1.0" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7/scopes/bceb75f9-5c10-4f39-9eb5-c000a2fabaee"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
