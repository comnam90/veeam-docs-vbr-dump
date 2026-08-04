---
title: "GET /security/accounts/{ID}/scopes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_security_accounts_id_scopes.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /security/accounts/{ID}/scopes


Returns a collection of restore scopes defined for the specified account. The account is added to Veeam Backup Enterprise Manager and is assigned a specific security role.

Request

To get a collection of restore scopes defined for the account having the specified ID, send the GET HTTP request to the /security/accounts/{ID}/scopes resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/scopes |

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

In the response body, the REST API returns a representation of the /security/accounts/{ID}/scopes resource.

Example

The example below returns a collection of restore scopes for the account having ID d6701c3d-15f4-421d-b376-c0e2634bc1f4:

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <EnterpriseAccountHierarchyScopes xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <EnterpriseAccountHierarchyScope Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/db0fd3c6-5f71-44f9-9bb1-1c61fc8b9fe2">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/db0fd3c6-5f71-44f9-9bb1-1c61fc8b9fe2" Rel="Delete" />         </Links>         <Name>172.24.145.152</Name>         <HierarchyRootName>24a14898-77d0-4881-bbf8-c8ba71ce4d55</HierarchyRootName>         <Platform>vCloud</Platform>         <HierarchyObjectType>VcdSystem</HierarchyObjectType>         <State>Processed</State>     </EnterpriseAccountHierarchyScope>     <EnterpriseAccountHierarchyScope Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf" Rel="Delete" />         </Links>         <Name>Enterprise</Name>         <HierarchyRootName>d68c782f-ec0a-4bf3-b3c1-04c552b64fdf</HierarchyRootName>         <Platform>VMware</Platform>         <HierarchyObjectType>ResourcePool</HierarchyObjectType>         <State>Processed</State>     </EnterpriseAccountHierarchyScope>     <EnterpriseAccountHierarchyScope Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf" Rel="Delete" />         </Links>         <Name>Enterprise</Name>         <HierarchyRootName>83963a7e-d43f-4fea-9036-466898c9c9e7</HierarchyRootName>         <Platform>VMware</Platform>         <HierarchyObjectType>ResourcePool</HierarchyObjectType>         <State>Processed</State>     </EnterpriseAccountHierarchyScope>     <EnterpriseAccountHierarchyScope Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf" Rel="Delete" />         </Links>         <Name>Enterprise</Name>         <HierarchyRootName>a26349ce-8c8a-47a2-af10-58afdd9fcece</HierarchyRootName>         <Platform>VMware</Platform>         <HierarchyObjectType>ResourcePool</HierarchyObjectType>         <State>Processed</State>     </EnterpriseAccountHierarchyScope> </EnterpriseAccountHierarchyScopes> |

Page updated 2026-07-29

