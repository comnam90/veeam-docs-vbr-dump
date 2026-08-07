---
title: "GET /restorePoints/{ID}/agentRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_restorepoints_id_agentrestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /restorePoints/{ID}/agentRestorePoints


Returns a resource representation of a restore points collection for Veeam Agent backups created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

Supported Platforms

The request is supported for Veeam Agent computers running Microsoft Windows or Linux.

Request

To get a list of Veeam Agent backups restore points, send the GET HTTP request to the /restorePoints/{ID}/agentRestorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/restorePoints/{ID}/agentRestorePoints |

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

In the response body, the REST API returns a representation of the /restorePoints/{ID}/agentRestorePoints resource collection.

Example

The example below returns a list of all restore points for Veeam Agent backups created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/restorePoints/7be71fcb-7301-4efa-9c24-011dc67f063c/agentRestorePoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:AgentRestorePoint:69c8ab97-acce-452e-8224-671a665e66ef" Name="sql12ten.local@2025-12-18 21:03:02" Href="http://local.host:9399/api/agents/agentRestorePoints/69c8ab97-acce-452e-8224-671a665e66ef" Type="AgentRestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/7be71fcb-7301-4efa-9c24-011dc67f063c" Name="Dec 18 2025  9:01PM" Type="RestorePointReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupFiles/dc00423c-3875-4e77-9122-13947ad797ba" Name="Agent Backup Job SQL - sql12ten.veea\_5778D2025-12-19T000125.vib" Type="BackupFileReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/agentRestorePoints/69c8ab97-acce-452e-8224-671a665e66ef?format=Entity" Name="sql12ten.tech.local@2025-12-18 21:03:02" Type="AgentRestorePoint" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

