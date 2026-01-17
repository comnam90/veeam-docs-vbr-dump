---
title: "GET /query?type=VmReplicaPoint"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_vmreplicapoint.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of restore points for separate replicated VMs. For details, see [/vmReplicaPoints](vmreplicapoints.md).

Request

To get a list of restore points for separate replicated VMs, send the GET HTTP request to the query with the type parameter set to VmReplicaPoint.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=VmReplicaPoint |

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
| UID | UidType | UID of the VM replica point resource. |
| Name | String | Name of the VM replica point, for example: dc-hv@2014-08-21 11:03:38. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| Type | String | Type of the VM replica point. Possible values:   * Full * ReverseIncrement * Increment * Snapshot |
| Algorithm | String | Replication method used to create the restore point. Possible values:   * Full * ReversedIncremental * Incremental * SyntheticFull |
| ReplicaUid | UidType | UID of the VM replica parent to the VM replica point resource. |
| ReplicaName | String | Name of the VM replica parent to the VM replica point resource. |
| VmDisplayName | String | Name of the VM for which the restore point has been created. |
| BackupServerUid | UidType | UID of the backup server on which the VM replica restore point has been created. |
| BackupServerName | String | Name of the backup server on which the VM replica restore point has been created. |

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

In the response body, the REST API returns a representation of the /vmReplicaPoints resource collection.

Example

The example below returns an entity resource representation of a collection of restore points created for replicated VM ubuntu88. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VmReplicaPoint&format=Entities&sortDesc=CreationTime&filter=VmDisplayName==ubuntu88    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
