---
title: "get_replicas_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_replicas_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a replica having the specified ID. The replica is created on the backup server connected to Veeam Backup Enterprise Manager.

Request

To get a replica, send the GET HTTP request to the /replicas/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/replicas/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /replicas/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the replica resource, for example: urn:veeam:Replica:58c917c7-7b7a-41ff-8676-226656c35c05. |
| Name | String | Name of the replica resource, for example: DNS Replication. |
| Platform | String | Platform for which the job is created. Possible values:   * VMware * Hyperv * vCloud |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=Replica](get_query_replica.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /repositories/{ID} | Up | URL of the [/repositories/{ID}](repositories_id.md) resource — a repository where replica metadata is stored. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the replication job was configured. |
| /replicas/{ID} | Alternate | Alternate URL of the [/replicas/{ID}](replicas_id.md) resource. |
| /replicas/{ID}/vmReplicaPoints | Down | URL of the [/vmReplicaPoints](vmreplicapoints.md) resource — a collection of restore points for separate replicated VMs processed by the replication job. |

Example

A sample request below returns a replica having ID fe4d9334-8801-440c-9994-5a16181d7fb0.

|  |
| --- |
| Request:  GET https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" UID="urn:veeam:Replica:fe4d9334-8801-440c-9994-5a16181d7fb0"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
