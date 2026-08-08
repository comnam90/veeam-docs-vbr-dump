---
title: "GET /restoreSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_restoresessions_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /restoreSessions/{ID}


Returns a restore session having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a restore session having the specified ID, send the GET HTTP request to the /restoreSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/restoreSessions/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /restoreSessions/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the restore session resource, for example: urn:veeam:RestoreSession:ed8e95ca-6ec5-4a2d-978b-e1108c4130b6. |
| Name | String | Name of the restore session resource, for example: sql02@2025-08-26 11:28:33. |
| JobType | String | Type of the restore session. Possible values:   * FileLevelRestore * RestoreVm |
| CreationTime | DateTime | Date and time when the restore session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the restore session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the restore session. Possible values:   * Starting * Stopping * Working * Stopped |
| Result | String | Result of the restore session. Possible values:   * Success * Warning * Failed |
| Progress | Int | Progress of the replication job session (between 1 and 100). |
| RestoredObjRef | HierarchyObjRefType | Reference to the restored object. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=RestoreSession](get_query_restoresession.md).

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that started the restore session. |
| /restoreSessions/{ID} | Alternate | Alternate URL of the [/restoreSessions/{ID}](restoresessions_id.md) resource. |
| /vmRestorePoints/{ID} | Related | URL of the [/vmRestorePoints/{ID}](vmrestorepoints_id.md) resource — a VM restore point used for restore. |

Example

The example below returns an entity resource representation of a restore session having ID ed8e95ca-6ec5-4a2d-978b-e1108c4130b6.

|  |
| --- |
| Request:  GET https://localhost:9398/api/restoreSessions/ed8e95ca-6ec5-4a2d-978b-e1108c4130b6?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <RestoreSession xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise04.tech.local:9398/api/restoreSessions/ed8e95ca-6ec5-4a2d-978b-e1108c4130b6?format=Entity" Type="RestoreSession" Name="ubuntu88@2025-10-21 17:10:02" UID="urn:veeam:RestoreSession:ed8e95ca-6ec5-4a2d-978b-e1108c4130b6" VmDisplayName="ubuntu88" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterprise04.tech.local:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f" Name="enterprise01.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterprise04.tech.local:9398/api/restoreSessions/ed8e95ca-6ec5-4a2d-978b-e1108c4130b6" Name="ubuntu88@2025-10-21 17:10:02" Type="RestoreSessionReference" Rel="Alternate" />         <Link Href="https://enterprise04.tech.local:9398/api/vmRestorePoints/6c958531-3177-4055-b0ce-dc4ef1ce6433" Name="ubuntu88@2025-10-20 20:04:07" Type="VmRestorePointReference" Rel="Related" />     </Links>     <JobType>RestoreVm</JobType>     <CreationTimeUTC>2025-10-21T17:10:02.017Z</CreationTimeUTC>     <State>Working</State>     <Result>None</Result>     <Progress>64</Progress> </RestoreSession> |

Page updated 2026-07-28

