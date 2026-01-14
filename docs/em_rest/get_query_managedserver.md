---
title: "get_query_managedserver"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_managedserver.html"
last_updated: "7/7/2023"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of servers that are managed by backup servers connected to Veeam Backup Enterprise Manager.

Request

To get a list of managed servers, send the GET HTTP request to the query with the type parameter set to ManagedServer.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=ManagedServer |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

| Parameter | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the server connected to Veeam Backup & Replication, for example: urn:veeam:ManagedServer:15942270-fb56-4dcc-96e9-5f80e4725a15. |
| Name | String | Full DNS name or IP address of the server connected to Veeam Backup & Replication. for example: 172.16.1.102. |
| Description | String | Description specified for the server in Veeam Backup & Replication. |
| ManagedServerType | String | Type of the server connected to Veeam Backup & Replication. Possible values:   * ESX * VC * Linux * Local * Windows * ESXi * HvServer * HvCluster * Scvmm * BackupServer * SanHost * SmbServer * SmbCluster * VcdSystem * Cloud * AzureWinServer * VmSnapshotStorageHost * ConfigurationService * ExternalInfrastructureProxy * NdmpServer * ExternalInfrastructureServer |

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

In the response body, the REST API returns a representation of the /ManagedServers resource collection.

Example

The example below returns an entity resource representation of a collection of VMware vCenter Servers managed by backup servers that are connected to Enterprise Manager. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=ManagedServer&format=Entities&sortAsc=name&filter=ManagedServerType==VC    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 7/7/2023

Page content applies to build 13.0.1.1071
