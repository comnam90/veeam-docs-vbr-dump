---
title: "GET /security/accounts/{ID}/roles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_security_accounts_id_roles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /security/accounts/{ID}/roles


Returns a collection of security roles assigned to the specified Veeam Backup Enterprise Manager account. For details on security roles, see [Security Roles](security_roles_concept.md).

Request

To get a collection of security roles assigned to the account having the specified ID, send the GET HTTP request to the /security/accounts/{ID}/roles resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/roles |

Request Header

The request contains the following headers:

Request Header

| Header | Required | Description |
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

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /security/accounts/{ID}/roles resource.

Example

A sample request below returns security roles assigned to the account having ID d6701c3d-15f4-421d-b376-c0e2634bc1f4:

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <EnterpriseAccountInRoleList xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6" Rel="Delete" />         </Links>         <RoleName>File Restore Operator</RoleName>     </EnterpriseAccountInRole>     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/c11c0c38-ba8b-49c7-bf70-fc2058fff1e2">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/c11c0c38-ba8b-49c7-bf70-fc2058fff1e2" Rel="Delete" />         </Links>         <RoleName>VM Restore Operator</RoleName>     </EnterpriseAccountInRole>     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f83e4c81-0815-452f-9377-9d573dd9d481">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f83e4c81-0815-452f-9377-9d573dd9d481" Rel="Delete" />         </Links>         <RoleName>Exchange Restore Operator</RoleName>     </EnterpriseAccountInRole>     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f78a92b8-9f06-4f1e-b522-4f0927cabd0f">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f78a92b8-9f06-4f1e-b522-4f0927cabd0f" Rel="Delete" />         </Links>         <RoleName>SQL Restore Operator</RoleName>     </EnterpriseAccountInRole>     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e" Rel="Delete" />         </Links>         <RoleName>Portal User</RoleName>     </EnterpriseAccountInRole> </EnterpriseAccountInRoleList> |

Page updated 2026-07-29

