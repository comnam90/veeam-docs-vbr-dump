---
title: "GET /backupTaskSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backuptasksessions_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupTaskSessions/{ID}


Returns a resource representation of a task having the specified ID. The parent backup job for the task is created and run on the backup server connected to Veeam Backup Enterprise Manager.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V
* Veeam Agent computers running Microsoft Windows or Linux

Request

To get a task having the specified ID, send the GET HTTP request to the URL of the /backupTaskSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupTaskSessions/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /backupTaskSessions/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the backup task session. |
| Name | String | Name of the backup task session, for example: dc-hv@2025-08-25 05:01:09. |
| JobSessionUid | UidType | UID of the backup job session parent to the backup task session resource. |
| CreationTime | DateTime | Date and time when the backup task session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the backup task session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the backup task session. Possible values:   * InProgress * Pending * Completed |
| Result | String | Result of the backup task session. Possible values:   * Success * Warning * Failed |
| Reason | String | Reason for which the backup task session has been completed with the Warning or Failed result. |
| TotalSize | Long | Size of all restore points produced by the backup job. |
| VmUid | UidType | UID of the VM that is processed in the backup task session. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=BackupTaskSession](get_query_backuptasksession.md).

Links

Response Body

| Reference | Relationship | Description |
| BackupServerReference | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — backup server where the related backup job was created. |
| BackupJobSessionReference | Up | URL of the [/backupSessions/{ID}](backupsessions_id.md) resource parent to the backup task session. |
| BackupTaskSessionReference | Alternate | Alternate URL of the [/backupTaskSessions/{ID}](backuptasksessions_id.md) resource. |
| VmRestorePoint | Related | URL of the [/vmRestorePoints/{ID}](vmrestorepoints_id.md) resource — a VM restore point created during the backup task session. |

Example

The example request below returns a resource representation of a task having ID 88322206-a645-4aa3-9228-028ce51e7c0f.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupTaskSessions/88322206-a645-4aa3-9228-028ce51e7c0f?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <BackupTaskSession xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://localhost:9398/api/backupTaskSessions/88322206-a645-4aa3-9228-028ce51e7c0f?format=Entity" Type="BackupTaskSession" Name="AnT\_VM2@2025-10-11 20:06:09" UID="urn:veeam:BackupTaskSession:88322206-a645-4aa3-9228-028ce51e7c0f" VmDisplayName="AnT\_VM2" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://localhost:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f" Name="enterprise01.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://localhost:9398/api/backupSessions/0d3a8230-3db1-4cc1-a7b2-3b0b5c8f784c" Name="vCD Job Template@2025-10-11 20:00:04" Type="BackupJobSessionReference" Rel="Up" />         <Link Href="https://localhost:9398/api/backupTaskSessions/88322206-a645-4aa3-9228-028ce51e7c0f" Name="AnT\_VM2@2025-10-11 20:06:09" Type="BackupTaskSessionReference" Rel="Alternate" />         <Link Href="https://localhost:9398/api/vmRestorePoints/a3571c27-a3a9-4ac8-8dfb-71a2336b3218?format=Entity" Name="AnT\_VM2-bFpa@2025-10-11 20:06:23" Type="VmRestorePoint" Rel="Related" />     </Links>     <JobSessionUid>urn:veeam:BackupJobSession:0d3a8230-3db1-4cc1-a7b2-3b0b5c8f784c</JobSessionUid>     <CreationTimeUTC>2025-10-11T20:06:09.627Z</CreationTimeUTC>     <EndTimeUTC>2025-10-11T20:07:09.347Z</EndTimeUTC>     <State>Completed</State>     <Result>Success</Result>     <Reason />     <TotalSize>12884901888</TotalSize>     <VmUid>urn:VMware:Vm:a87d15db-dd70-4769-acd6-41bae88219d4.vm-91826</VmUid> </BackupTaskSession> |

Page updated 2026-07-28

