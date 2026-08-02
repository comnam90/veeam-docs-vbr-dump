---
title: "GET /security/roles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_security_roles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /security/roles


Returns a collection of security roles used for access management in Veeam Backup Enterprise Manager REST API. For details on security roles, see [Security Roles](security_roles_concept.md).

Request

To get a list of security roles used in Veeam Backup Enterprise Manager, send the GET HTTP request to the /security/roles resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/security/roles |

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

In the response body, the REST API returns a representation of the /security/roles resource collection.

Example

The example below returns a list of security roles used in Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/roles  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <EntityReferences xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <Ref UID="urn:veeam:EnterpriseRole:d19a3d33-cb77-4ffe-94e6-001432483a4e" Name="Portal User" Href="https://enterprise04.tech.local:9398/api/security/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:f78a92b8-9f06-4f1e-b522-4f0927cabd0f" Name="SQL Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/f78a92b8-9f06-4f1e-b522-4f0927cabd0f" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/f78a92b8-9f06-4f1e-b522-4f0927cabd0f?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:e9d90e66-b6d4-49dc-8986-73cf33489623" Name="Oracle Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/e9d90e66-b6d4-49dc-8986-73cf33489623" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/e9d90e66-b6d4-49dc-8986-73cf33489623?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:f84a8b62-49b8-4d0c-b25b-92321b52bab6" Name="File Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:f83e4c81-0815-452f-9377-9d573dd9d481" Name="Exchange Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/f83e4c81-0815-452f-9377-9d573dd9d481" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/f83e4c81-0815-452f-9377-9d573dd9d481?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:5f37a46b-9ce2-40f4-8a62-b45b079257fc" Name="Portal Administrator" Href="https://enterprise04.tech.local:9398/api/security/roles/5f37a46b-9ce2-40f4-8a62-b45b079257fc" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/5f37a46b-9ce2-40f4-8a62-b45b079257fc?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:c11c0c38-ba8b-49c7-bf70-fc2058fff1e2" Name="VM Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/c11c0c38-ba8b-49c7-bf70-fc2058fff1e2" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/c11c0c38-ba8b-49c7-bf70-fc2058fff1e2?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref> </EntityReferences> |

Page updated 2026-07-29

