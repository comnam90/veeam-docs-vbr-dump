---
title: "GET /query?type=CloudVmReplicaPoint"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudvmreplicapoint.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# GET /query?type=CloudVmReplicaPoint


Returns a resource representation of a collection of restore points for separate VMs that are replicated with tenant replication jobs. For details, see [/cloud/vmReplicaPoints](cloudvmreplicapoints.md).

The collection includes restore points of the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

Request

To get a list of restore points, send the GET HTTP request to the query with the type parameter set to CloudVmReplicaPoint.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudVmReplicaPoint |

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
| UID | UidType | ID of the VM replica point resource. |
| Name | String | Name of the VM replica point, for example: dc-hv@2015-12-25 20:03:56. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| VmName | String | Name of the tenant VM for which the restore point has been created. |
| Type | String | Type of the VM replica point. Possible values:   * CDP * Full * ReverseIncrement * Increment * Snapshot |
| ReplicaUid | UidType | UID of the tenant VM replica parent to the VM replica point resource. |
| ReplicaName | String | Name of the tenant VM replica parent to the VM replica point resource. |
| VmDisplayName | String | Name of the tenant VM for which the restore point has been created. |
| BackupServerUid | UidType | UID of the backup server on which the account of the tenant who has  created the VM replica restore point had been created. |
| BackupServerName | String | Name of the backup server on which the account of the tenant who has created the VM replica restore point had been created. |
| State | String | State of the tenant VM replica. Possible values:   * Unknown * Ready * Failover  * Failback * PermanentFailover |

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

In the response body, the REST API returns a representation of the /cloud/vmReplicaPoints resource collection.

Example

The example below returns an entity resource representation of a collection of of last 5 replica restore points created for VM filesrv03. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudVmReplicaPoint&format=Entities&sortDesc=CreationTime&pageSize=5&page=1&filter=VmName==filesrv03    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


