---
title: "GET /cdpReplicas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplicas.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cdpReplicas


Returns a collection of CDP replicas created by all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of CDP replicas, send the [GET /query?type=CdpReplica](get_query_cdpreplica.md) request. |

Request

To get a collection of replicas, send the GET HTTP request to the /cdpReplicas resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplicas |

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

In the response body, the REST API returns a representation of the /cdpReplicas resource collection.

Example

The example below returns a collection of all CDP replicas created by backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplicas  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CdpReplicaReference" Href="https://localhost:9398/api/cdpReplicas/7665222c-2e99-4a3f-b892-1827ba8d1eee" Name="CDP Policy 2" UID="urn:veeam:CdpReplica:7665222c-2e99-4a3f-b892-1827ba8d1eee">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Alternate" Type="CdpReplica" Href="https://localhost:9398/api/cdpReplicas/7665222c-2e99-4a3f-b892-1827ba8d1eee?format=Entity" Name="CDP Policy 2" />     </Links>   </Ref>   <Ref Type="CdpReplicaReference" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722" Name="CDP Policy 1" UID="urn:veeam:CdpReplica:24ae37ad-4d28-4568-8467-98d8770bb722">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Alternate" Type="CdpReplica" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722?format=Entity" Name="CDP Policy 1" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

