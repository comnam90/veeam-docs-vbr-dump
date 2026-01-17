---
title: "GET /cdpReplicas/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplicas_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a CDP replica having the specified ID. The CDP replica is created by the backup server connected to Veeam Backup Enterprise Manager.

Request

To get a CDP replica, send the GET HTTP request to the /cdpReplicas/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplicas/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /cdpReplicas/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the CDP replica, for example: urn:veeam:Replica:urn:veeam:CdpReplica:24ae37ad-4d28-4568-8467-98d8770bb722. |
| Name | String | Name of the CDP replica, for example: CDP Policy 1. |
| BackupServer | String | Name of the backup server parent to the CDP replica resource. |
| PolicyUid | UidType | UID of the CDP policy parent to the replica, for example:145f3365-6ec0-44e9-9538-8c8c34ebdcce. |
| PolicyName | String | Name of the CDP policy parent to the replica, for example: CDP Policy 1. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CdpReplica](get_query_cdpreplica.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the CDP policy was configured. |
| /cdpPolicies/{ID} | Up | URL of the [/cdpPolicies/{ID}](cdppolicies_id.md) resource — a CDP policy that processes the replica. |
| /cdpReplicas/{ID}/vms | Down | URL of the [/cdpPolicies/{ID}/includes](cdppolicies_id_includes.md) resource — a collection of VMs and VM containers processed by the CDP policy. |
| /cdpReplicas/{ID} | Alternate | Alternate URL of the [/cdpReplicas/{ID}](cdpreplicas_id.md) resource. |

Example

A sample request below returns a replica having ID 24ae37ad-4d28-4568-8467-98d8770bb722.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplicaReference" Href="https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722" Name="CDP Policy 1" UID="urn:veeam:CdpReplica:24ae37ad-4d28-4568-8467-98d8770bb722"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
