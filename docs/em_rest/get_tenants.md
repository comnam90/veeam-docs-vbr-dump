---
title: "GET /cloud/tenants"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tenants.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/tenants


Returns a resource representation of a collection of tenant accounts created on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of tenant accounts, send the [GET /query?type=CloudTenant](get_query_cloudtenant.md) request. |

Request

To get a list of tenant accounts, send the GET HTTP request to the /cloud/tenants resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants |

Request Headers

The request contains the following headers:

Request Headers

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

In the response body, the REST API returns a representation of the /cloud/tenants resource collection.

Example

The example below returns a list of tenant accounts created on all backup servers that are currently connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/b3ed42c9-3022-4958-864f-3df32e8436f9" Name="UCM Company" UID="urn:veeam:CloudTenant:b3ed42c9-3022-4958-864f-3df32e8436f9">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/b3ed42c9-3022-4958-864f-3df32e8436f9?format=Entity" Name="UCM Company" />     </Links>   </Ref>   <Ref Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/9e76e394-9dfe-4089-bc0d-569c5376ae86" Name="Applied Systems Company" UID="urn:veeam:CloudTenant:9e76e394-9dfe-4089-bc0d-569c5376ae86">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/9e76e394-9dfe-4089-bc0d-569c5376ae86?format=Entity" Name="Applied Systems Company" />     </Links>   </Ref>   <Ref Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89" Name="ABC Company" UID="urn:veeam:CloudTenant:4f90635a-7ecc-49fe-beb6-60b37eb4bd89">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89?format=Entity" Name="ABC Company" />     </Links>   </Ref>   <Ref Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/20602b2b-d55b-436c-9010-b4c7046c294a" Name="Tri-M Company" UID="urn:veeam:CloudTenant:20602b2b-d55b-436c-9010-b4c7046c294a">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/20602b2b-d55b-436c-9010-b4c7046c294a?format=Entity" Name="Tri-M Company" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

