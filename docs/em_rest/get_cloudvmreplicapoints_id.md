---
title: "GET /cloud/vmReplicaPoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudvmreplicapoints_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/vmReplicaPoints/{ID}


Returns a resource representation of a VM replica restore point that has the specified ID. VM is replicated with the tenant replication job.

Request

To get a restore point for a specific tenant VM replica, send the GET HTTP request to the /cloud/vmReplicaPoints/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/vmReplicaPoints/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /cloud/vmReplicaPoints/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the VM replica point resource. |
| Name | String | Name of the VM replica point, for example: dc-hv@2025-12-25 20:03:56. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| PointType | String | Type of the VM replica point. Possible values:   * CDP * Full * ReverseIncrement * Increment * Snapshot |
| State | String | State of the tenant VM replica. Possible values:   * Unknown * Ready * Failover  * Failback * PermanentFailover |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudVmReplicaPoint](get_query_cloudvmreplicapoint.md).

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server of the Service Provider. |
| /cloud/replicas/{ID} | Up | URL of the [/cloud/replicas/{ID}](cloudreplicas_id.md) resource — a cloud replica that contains the VM replica point. |
| /cloud/vmReplicaPoints/{ID} | Alternate | Alternate URL of the [/cloud/vmReplicaPoints/{ID}](cloudvmreplicapoints_id.md) resource. |

Example

The example below returns an entity resource representation of the VM replica restore point having ID 61ad8531-045d-421a-9ba6-d220b5f80b64:

|  |
| --- |
| Request:  GET https://localhost:9398/api/vmReplicaPoints/61ad8531-045d-421a-9ba6-d220b5f80b64?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <CloudVmReplicaPoint xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise06.tech.local:9398/api/cloud/vmReplicaPoints/61ad8531-045d-421a-9ba6-d220b5f80b64?format=Entity" Type="CloudVmReplicaPoint" Name="apache05@2025-11-03 18:01:25" UID="urn:veeam:CloudVmReplicaPoint:61ad8531-045d-421a-9ba6-d220b5f80b64" VmDisplayName="apache05" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterprise06.tech.local:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/replicas/062a386c-2b1a-4a01-aa55-8fc851573787" Name="apache05" Type="CloudReplicaReference" Rel="Up" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/vmReplicaPoints/61ad8531-045d-421a-9ba6-d220b5f80b64" Name="apache05@2025-11-03 18:01:25" Type="CloudVmReplicaPointReference" Rel="Alternate" />     </Links>     <CreationTimeUTC>2025-11-03T18:01:25.93Z</CreationTimeUTC>     <PointType>Snapshot</PointType>     <State>Ready</State> </CloudVmReplicaPoint> |

Page updated 2026-07-29

