---
title: "get_query_vappreplicapoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_vappreplicapoint.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns resource representation of a collection of restore points of separate vApps replicas. For details, see [/vAppReplicaPoints](vappreplicapoints.md).

Request

To get a list of restore points of separate vApps replicas, send the GET HTTP request to the query with the type parameter set to vAppReplicaPoint.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=vAppReplicaPoint |

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
| UID | UidType | UID of the vApp replica point resource. |
| Name | String | Name of the vApp replica point, for example: vApp01@2021-02-04 00:08:35. |
| vAppDisplayName | String | Display name of the vApp for which the restore point has been created. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| vAppName | String | Name of the vApp for which the restore point has been created. |
| Type | String | Type of the vApp replica point. Possible values:   * Full * ReverseIncrement * Increment * Snapshot |
| Algorithm | String | Replication method used to create the restore point. Possible values:   * Full * ReversedIncremental * Incremental * SyntheticFull |
| ReplicaUid | UidType | UID of the vApp replica parent to the vApp replica point resource. |
| ReplicaName | String | Name of the vApp replica parent to the vApp replica point resource. |
| BackupServerUid | UidType | UID of the backup server where the vApp replica restore point has been created. |
| BackupServerName | String | Name of the backup server where the vApp replica restore point has been created. |

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

In the response body, the REST API returns a representation of the /vAppReplicaPoints resource collection.

Example

The example below returns a list of vApp replica restore points created on backup servers connected to Veeam Backup Enterprise Manager

The example below returns an entity resource representation of a collection of vApp replica restore points created for vApp vApp002. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VAppReplicaPoint&format=Entities&sortDesc=CreationTime&filter=VAppName==vApp002    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
