---
title: "GET /vAppReplicaPoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vappreplicapoints_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of the vApp replica restore point having the specified ID.

Request

To get a vApp replica restore point, send the GET HTTP request to the /vAppReplicaPoints/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /vAppReplicaPoints/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the vApp replica point resource. |
| Name | String | Name of the vApp replica point, for example: vApp01@2021-02-04 00:08:35. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| VAppName | String | Name of the vApp for which the restore point has been created. |
| Algorithm | String | Replication method used to create the restore point. Possible values:   * Full * ReversedIncremental * Incremental * SyntheticFull |
| PointType | String | Type of the vApp replica point. Possible values:   * Full * ReverseIncrement * Increment * Snapshot |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=vAppReplicaPoint](get_query_vappreplicapoint.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /vAppReplicaPoints/{ID}?action=failover | Failover | URL for the [POST /vAppReplicaPoints/{ID}?action=failover](post_vappreplicapoints_id_actionfailover.md) request. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that created the restore point. |
| /replicas/{ID} | Up | URL of the [/replicas/{ID}](replicas_id.md) resource — a vApp replica for which the restore point was created. |
| /vAppReplicaPoints/{ID} | Alternate | Alternate URL of the [/vAppReplicaPoints/{ID}](vappreplicapoints_id.md) resource. |
| /vmReplicaPoints/{ID} | Down | URL of the [/vmReplicaPoints/{ID}](vmreplicapoints_id.md) resource — a replica restore point of a VM contained in the vApp. |

Example

The example below returns an entity resource representation of the vApp replica restore point having ID dc01c979-5f6a-409c-bcc2-c3c6ddf439b3:

|  |
| --- |
| Request:  GET https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VAppReplicaPoint xmlns="http://www.veeam.com/ent/v1.0" Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/dc01c979-5f6a-409c-bcc2-c3c6ddf439b3?format=Entity" Name="vApp01@2021-02-04 00:08:35" UID="urn:veeam:VAppReplicaPoint:dc01c979-5f6a-409c-bcc2-c3c6ddf439b3" VAppDisplayName="vApp01"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
