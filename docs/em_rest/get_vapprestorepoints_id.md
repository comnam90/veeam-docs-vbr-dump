---
title: "GET /vAppRestorePoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vapprestorepoints_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /vAppRestorePoints/{ID}


Returns a resource representation of a vApp restore point having the specified ID.

Supported Platforms

The request is supported for the VMware Cloud Director platform.

Request

To get a vApp restore point, send the GET HTTP request to the /vAppRestorePoints/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vAppRestorePoints/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /vAppRestorePoints/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the vApp point resource. |
| Name | String | Name of the vApp restore point, for example: vApp02@2025-08-24 05:03:25. |
| CreationTime | DateTime | Date and time when the vApp restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| Algorithm | String | Backup method used to create the vApp restore point. Possible values:   * Full * ReversedIncremental * Incremental * SyntheticFull |
| PointType | String | Type of the vApp restore point. Possible values:   * Full * Increment * ReverseIncrement |
| HierarchyObjRef | HierarchyObjRefType | Reference to the vApp. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=vAppRestorePoint](get_query_vapprestorepoint.md).

Links

Response Body

| Reference | Relationship | Description |
| /vAppRestorePoints/{ID}?action=restore | Restore | URL for the [POST /vAppRestorePoints/{ID}?action=restore](post_vapprestorepoints_id_actionrestore.md) request. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that created the restore point. |
| /restorePoints/{ID}/ | Up | URL of the [/restorePoints/{ID}](restorepoints_id.md) resource — a parent restore point. |
| /vAppRestorePoints//{ID} | Alternate | Alternate URL of the [/vAppRestorePoints/{ID}](vapprestorepoints_id.md) resource. |

Example

The example below returns an entity resource representation of a vApp restore point having ID f920aeea-b75a-4687-88ae-09d07c83ca63.

|  |
| --- |
| Request:  GET https://localhost:9398/api/vAppRestorePoints/f920aeea-b75a-4687-88ae-09d07c83ca63?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <VAppRestorePoint xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://localhost:9398/api/vAppRestorePoints/f920aeea-b75a-4687-88ae-09d07c83ca63?format=Entity" Type="VAppRestorePoint" Name="AnT\_vApp1\_replica@2025-10-20 20:04:14" UID="urn:veeam:VAppRestorePoint:f920aeea-b75a-4687-88ae-09d07c83ca63" VAppDisplayName="AnT\_vApp1\_replica" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://localhost:9398/api/vAppRestorePoints/f920aeea-b75a-4687-88ae-09d07c83ca63?action=restore" Rel="Restore" />         <Link Href="https://localhost:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f" Name="enterprise01.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://localhost:9398/api/restorePoints/1c5d9edf-9a8f-4fa7-88ff-a31eefe94f15" Name="Oct 20 2025  8:00PM" Type="RestorePointReference" Rel="Up" />         <Link Href="https://localhost:9398/api/vAppRestorePoints/f920aeea-b75a-4687-88ae-09d07c83ca63" Name="AnT\_vApp1\_replica@2025-10-20 20:04:14" Type="VAppRestorePointReference" Rel="Alternate" />     </Links>     <CreationTimeUTC>2025-10-20T20:04:14.407Z</CreationTimeUTC>     <Algorithm>Incremental</Algorithm>     <PointType>Increment</PointType>     <HierarchyObjRef>urn:vCloud:Vapp:24a14898-77d0-4881-bbf8-c8ba71ce4d55.urn:vcloud:vapp:39b1bdc8-9d0b-475d-8f12-24c289f4c069</HierarchyObjRef> </VAppRestorePoint> |

Page updated 2026-07-29

