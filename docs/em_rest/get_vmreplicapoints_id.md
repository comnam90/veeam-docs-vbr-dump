---
title: "GET /vmReplicaPoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vmreplicapoints_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /vmReplicaPoints/{ID}


Returns a resource representation of a VM replica restore point having the specified ID.

Request

To get a restore point for a specific VM replica, send the GET HTTP request to the /vmReplicaPoints/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /vmReplicaPoints/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the VM replica point resource. |
| Name | String | Name of the VM replica point, for example: dc-hv@2025-08-21 11:03:38. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| VmName | String | Name of the VM for which the restore point has been created. |
| Algorithm | String | Replication method used to create the restore point. Possible values:   * Full * ReversedIncremental * Incremental * SyntheticFull |
| PoinType | String | Type of the VM replica point. Possible values:   * Full * ReverseIncrement * Increment * Snapshot |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=VmReplicaPoint](get_query_vmreplicapoint.md).

Links

Response Body

| Reference | Relationship | Description |
| /vmReplicaPoints/{ID}?action=failover | Failover | URL for the [POST /vmReplicaPoints/{ID}?action=failover](post_vmreplicapoints_id_actionrestore.md) request. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that created the replica restore point. |
| /replicas/{ID} | Up | URL of the [/replicas/{ID}](replicas_id.md) resource — a VM replica for which the restore point was created. |
| /vmReplicaPoints/{ID} | Alternate | Alternate URL of the [/vmReplicaPoints/{ID}](vmreplicapoints_id.md) resource. |
| /vmReplicaPoints/{ID}/mounts | Down | URL of the [/vmReplicaPoints/{ID}/mounts](vmreplicapoints_id_mountpoint.md) resource — a collection of mount points that provide access to guest OS files of the VM. |
| /vmReplicaPoints/{ID}/mounts | Create | URL for the [POST /vmReplicaPoints/{ID}/mounts](post_vmreplicapoints_id_mountpoints.md) request. |

Example

The example below returns an entity resource representation of a VM replica restore point having ID 7bd7de06-ec7c-4067-b10b-081e4a69ccc3:

|  |
| --- |
| Request:  GET https://localhost:9398/api/vmReplicaPoints/7bd7de06-ec7c-4067-b10b-081e4a69ccc3?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <VmReplicaPoint xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://localhost:9398/api/vmReplicaPoints/7bd7de06-ec7c-4067-b10b-081e4a69ccc3?format=Entity" Type="VmReplicaPoint" Name="apache\_replica@2025-10-18 20:00:30" UID="urn:veeam:VmReplicaPoint:7bd7de06-ec7c-4067-b10b-081e4a69ccc3" VmDisplayName="apache\_replica" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://localhost:9398/api/vmReplicaPoints/7bd7de06-ec7c-4067-b10b-081e4a69ccc3?action=failover" Rel="Failover" />         <Link Href="https://localhost:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f" Name="enterprise01.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://localhost:9398/api/replicas/f8864ea3-8ddf-45b3-b81b-6d95b58a7d9b" Name="Replication Job 1" Type="ReplicaReference" Rel="Up" />         <Link Href="https://localhost:9398/api/vmReplicaPoints/7bd7de06-ec7c-4067-b10b-081e4a69ccc3" Name="apache\_replica@2025-10-18 20:00:30" Type="VmReplicaPointReference" Rel="Alternate" />         <Link Href="https://localhost:9398/api/vmReplicaPoints/7bd7de06-ec7c-4067-b10b-081e4a69ccc3/mounts" Type="VmReplicaPointMountList" Rel="Down" />         <Link Href="https://localhost:9398/api/vmReplicaPoints/7bd7de06-ec7c-4067-b10b-081e4a69ccc3/mounts" Type="VmReplicaPointMount" Rel="Create" />     </Links>     <CreationTimeUTC>2025-10-18T20:00:30.423Z</CreationTimeUTC>     <VmName>apache\_replica</VmName>     <Algorithm>Full</Algorithm>     <PointType>Snapshot</PointType> </VmReplicaPoint> |

Page updated 2026-07-29

