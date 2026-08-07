---
title: "GET /managedServers/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_managedservers_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /managedServers/{ID}


Returns a resource representation of the server having the specified ID.

Request

To get a resource representation of the server, send the GET HTTP request to the /managedServers/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/managedServers/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/managedServers/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /managedServers/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the server connected to Veeam Backup & Replication, for example: urn:veeam:ManagedServer:15942270-fb56-4dcc-96e9-5f80e4725a15. |
| Name | String | Full DNS name or IP address of the server connected to Veeam Backup & Replication, for example: 172.16.1.102. |
| Description | String | Description specified for the server in Veeam Backup & Replication. |
| ManagedServerType | String | Type of the server connected to Veeam Backup & Replication. Possible values:   * ESX * VC * Linux * Local * Windows * ESXi * HvServer * HvCluster * Scvmm * BackupServer * SanHost * SmbServer * SmbCluster * VcdSystem * Cloud * AzureWinServer * VmSnapshotStorageHost * ConfigurationService * ExternalInfrastructureProxy * NdmpServer * ExternalInfrastructureServer |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=ManagedServer](get_query_managedserver.md).

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that contains the managed server in the backup infrastructure. |
| /managedServers/{ID} | Alternate | Alternate URL of the [/managedServers/{ID}](managedservers_id.md) resource. |
| /hierarchyRoots/{ID} | Related | URL of the [/hierarchyRoots/{ID}](hierarchyroots_id.md) resource — a related virtualization host. |

Example

The example below returns an entity representation of the server having ID 4e24d83f-2403-455c-8454-54e4eda8da34:

|  |
| --- |
| Request:  GET https://localhost:9398/api/managedServers/4e24d83f-2403-455c-8454-54e4eda8da34?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <ManagedServer xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://localhost:9398/api/managedServers/4e24d83f-2403-455c-8454-54e4eda8da34?format=Entity" Type="ManagedServer" Name="enterprise03.tech.local" UID="urn:veeam:ManagedServer:4e24d83f-2403-455c-8454-54e4eda8da34" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://localhost:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f?format=Entity" Name="enterprise01.tech.local" Type="BackupServer" Rel="Up" />         <Link Href="https://localhost:9398/api/managedServers/4e24d83f-2403-455c-8454-54e4eda8da34" Name="enterprise03.tech.local" Type="ManagedServerReference" Rel="Alternate" />         <Link Href="https://localhost:9398/api/hierarchyRoots/4e24d83f-2403-455c-8454-54e4eda8da34?format=Entity" Name="enterprise03.tech.local" Type="HierarchyRoot" Rel="Related" />     </Links>     <Description>Created by Administrator</Description>     <ManagedServerType>Windows</ManagedServerType> </ManagedServer> |

Page updated 2026-07-29

