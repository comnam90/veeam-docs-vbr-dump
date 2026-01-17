---
title: "GET /query?type=BackupServer"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_backupserver.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of backup servers connected to Veeam Backup Enterprise Manager. For details, see [/backupServers](backupservers.md).

Request

To get a list of backup servers connected to Veeam Backup Enterprise Manager, send the GET HTTP request to the query with the type parameter set to BackupServer.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=BackupServer |

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
| UID | UidType | UID of the backup server connected to Veeam Backup Enterprise Manager, for example: urn:veeam:BackupServer:15942270-fb56-4dcc-96e9-5f80e4725a15. |
| Name | String | Name of the backup server connected to Veeam Backup Enterprise Manager, for example: BACKUPSERVER. |
| Description | String | Description specified for the backup server in Veeam Backup Enterprise Manager. |
| IpOrDnsName | String | IP or DNS name that has been used for adding the backup server to Veeam Backup Enterprise Manager, for example, 172.16.11.22. |
| Port | Int64 | Port used by Veeam Backup Enterprise Manager for collecting data from backup servers. By default, port 9392 is used. |
| Version | String | Version of Veeam Backup & Replication installed on the backup server, for example: 13.0.0.1420. |

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

In the response body, the REST API returns a representation of the /backupServers resource collection.

Example

The example below returns an entity resource representation of a collection of backup servers that are connected to Veeam Backup Enterprise Manager and that have version 11.0.0.837 of Veeam Backup & Replication installed.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=BackupServer&format=Entities&filter=Version=="11.0.0.837"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
