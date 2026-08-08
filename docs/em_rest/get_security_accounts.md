---
title: "GET /security/accounts"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_security_accounts.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /security/accounts


Returns a collection of accounts having specific security roles in Veeam Backup Enterprise Manager.

Request

To get a list of accounts having specific security roles in Veeam Backup Enterprise Manager, send the GET HTTP request to the /security/accounts resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/security/accounts |

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

In the response body, the REST API returns a representation of the /security/accounts resource collection.

Example

The example below returns a list of accounts having specific security roles in Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/accounts  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/d1b025b4-af19-4a8d-9eeb-2db43e4710f4" Name="BUILTIN\Administrators" UID="urn:veeam:EnterpriseAccount:d1b025b4-af19-4a8d-9eeb-2db43e4710f4">     <Links>       <Link Rel="Alternate" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/d1b025b4-af19-4a8d-9eeb-2db43e4710f4?format=Entity" />     </Links>   </Ref>   <Ref Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7" Name="BUILTIN\Users" UID="urn:veeam:EnterpriseAccount:de19303b-bcf3-428b-b113-ac0b2cf46bd7">     <Links>       <Link Rel="Alternate" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7?format=Entity" />     </Links>   </Ref>   <Ref Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/2cd80a69-077c-400f-a714-cafe97bc8f60" Name="SRV02\Administrator" UID="urn:veeam:EnterpriseAccount:2cd80a69-077c-400f-a714-cafe97bc8f60">     <Links>       <Link Rel="Alternate" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/2cd80a69-077c-400f-a714-cafe97bc8f60?format=Entity" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

