---
title: "GET /security/roles/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_security_roles_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a security role having the specified ID. The security role belongs to a list of roles used in Veeam Backup Enterprise Manager.

Veeam Backup Enterprise Manager REST API exposes the following security roles:

* Portal Administrator
* Portal User
* VM Restore Operator
* File Restore Operator
* Exchange Restore Operator
* Oracle Restore Operator
* SQL Restore Operator

Request

To get a security role used in Veeam Backup Enterprise Manager, send the GET HTTP request to the /security/roles/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/security/roles/{ID} |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Query Parameters

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

In the response body, the REST API returns an entity or an entity reference of the /security/roles/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the security role used in Veeam Backup Enterprise Manager, for example:urn:veeam:EnterpriseRole:d19a3d33-cb77-4ffe-94e6-001432483a4e. |
| Name | String | Name of the security role used in Veeam Backup Enterprise Manager, for example: Portal User. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /security/roles/{ID} | Alternate | Alternate URL of the [/security/roles/{ID}](security_roles_id.md) resource. |

Example

A sample request below returns the Portal User security role in used Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="EnterpriseRoleReference" Href="https://localhost:9398/api/security/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e" Name="Portal User" UID="urn:veeam:EnterpriseRole:d19a3d33-cb77-4ffe-94e6-001432483a4e"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
