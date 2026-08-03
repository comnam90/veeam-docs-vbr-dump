---
title: "GET /cdpReplica/vApps"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplicas_id_vapps.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cdpReplica/vApps


Returns a collection of all vApps that are replicated by CDP policies for VMware Cloud Director.

Request

To get a collection of vApps that are replicated by CDP policies, send the GET HTTP request to the /cdpReplica/vApps resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplica/vApps |

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

In the response body, the REST API returns a representation of the /cdpReplica/vApps resource collection.

Example

A sample request below returns a collection of all vApps that are replicated by CDP policies for VMware Cloud Director.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplica/vApps  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <EntityReferences xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <Ref UID="urn:veeam:VAppCdpReplica:4d408966-827f-4142-811f-90be94c842a9" Name="vApp02" Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9" Type="VAppCdpReplicaReference">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9?format=Entity" Name="vApp02" Type="VAppCdpReplica" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:VAppCdpReplica:571252ff-c227-4204-b9f8-e1f32a52496b" Name="vApp-TS" Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/571252ff-c227-4204-b9f8-e1f32a52496b" Type="VAppCdpReplicaReference">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/571252ff-c227-4204-b9f8-e1f32a52496b?format=Entity" Name="vApp-TS" Type="VAppCdpReplica" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

