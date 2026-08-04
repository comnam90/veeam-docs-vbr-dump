---
title: "GET /query?type=BackupTaskSession"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_backuptasksession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=BackupTaskSession


Returns a resource representation of a collection of backup task sessions that are performed on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/backupTaskSessions](backuptasksessions.md).

Request

To get a list of backup task sessions, send the GET HTTP request to the query with the type parameter set to BackupTaskSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=BackupTaskSession |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
| UID | UidType | ID of the backup task session. |
| Name | String | Name of the backup task session, for example: dc-hv@2025-08-25 05:01:09. |
| CreationTime | DateTime | Date and time when the backup task session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the backup task session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the backup task session. Possible values:   * InProgress * Pending * Completed |
| Result | String | Result of the backup task session. Possible values:   * Success * Warning * Failed |
| Reason | String | Reason for which the backup task session has been completed with the Warning or Failed result. |
| TotalSize | Long | Size of all restore points produced by the backup job. |
| JobSessionUid | UidType | UID of the backup job session parent to the backup task session resource. |
| JobUid | UidType | UID of the backup job parent to the backup task session resource. |
| JobName | String | Name of the backup job parent to the backup task session resource. |
| BackupServerUid | UidType | UID of the backup server on which the backup job is created. |
| BackupServerName | String | Name of the backup server on which the backup job is created. |
| VmDisplayName | String | Name of the VM that is processed in the backup task session. |

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

In the response body, the REST API returns a representation of the /backupTaskSessions resource collection.

Example

The example below returns an entity resource representation of a collection of last 3 backup task sessions started for VM dbserver01 and that were failed. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=BackupTaskSession&format=Entities&sortDesc=CreationTime&pageSize=3&page=1&filter=Result==Failed;VmDisplayName==dbserver01  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <BackupTaskSessions>       <BackupTaskSession Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/38ceb150-e0a8-4f87-8a17-243afc1b98f4?format=Entity" Name="dbserver01@2025-06-05 01:04:29" VmDisplayName="dbserver01" UID="urn:veeam:BackupTaskSession:38ceb150-e0a8-4f87-8a17-243afc1b98f4">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/35c24055-bdee-4e43-b655-a42de408d2ec" Name="Backup Job 1@2025-06-05 01:03:37" />           <Link Rel="Alternate" Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/38ceb150-e0a8-4f87-8a17-243afc1b98f4" Name="dbserver01@2025-06-05 01:04:29" />         </Links>         <JobSessionUid>urn:veeam:BackupJobSession:35c24055-bdee-4e43-b655-a42de408d2ec</JobSessionUid>         <CreationTimeUTC>2025-06-05T01:04:29.56Z</CreationTimeUTC>         <EndTimeUTC>2025-06-05T01:04:44.53Z</EndTimeUTC>         <State>Completed</State>         <Result>Failed</Result>         <Reason>Error: There is not enough space on the disk. Failed to write data to the file [C:\Backup\Backup Job 1\Backup Job 1D2025-06-05T030355\_06C7.vib]. Failed to backup text locally. Backup: [VBK: 'veeamfs:0:de28dc43-b8ee-4e17-8e63-3d38b6604033 (vm-62228)\summary.xml@C:\Backup\Backup Job 1\Backup Job 1D2025-06-05T030355\_06C7.vib']. Agent failed to process method {DataTransfer.BackupText}. Agent failed to process method {DataTransfer.BackupText}. </Reason>         <TotalSize>0</TotalSize>         <VmUid>urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-62228</VmUid>       </BackupTaskSession>       <BackupTaskSession Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/e381e791-db27-492a-889b-1ed1f8217016?format=Entity" Name="dbserver01@2025-05-13 05:00:30" VmDisplayName="dbserver01" UID="urn:veeam:BackupTaskSession:e381e791-db27-492a-889b-1ed1f8217016">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/2d4de050-b10b-4ece-8ce6-204293ddc01a" Name="Backup Job 1@2025-05-13 05:00:10" />           <Link Rel="Alternate" Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/e381e791-db27-492a-889b-1ed1f8217016" Name="dbserver01@2025-05-13 05:00:30" />         </Links>         <JobSessionUid>urn:veeam:BackupJobSession:2d4de050-b10b-4ece-8ce6-204293ddc01a</JobSessionUid>         <CreationTimeUTC>2025-05-13T05:00:30.853Z</CreationTimeUTC>         <EndTimeUTC>2025-05-13T05:01:57.83Z</EndTimeUTC>         <State>Completed</State>         <Result>Failed</Result>         <Reason>Hard disk 1 (0 B)</Reason>         <TotalSize>0</TotalSize>         <VmUid>urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-62228</VmUid>       </BackupTaskSession>       <BackupTaskSession Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/c8de8f77-46d7-4671-b789-f490cd710692?format=Entity" Name="dbserver01@2025-05-12 05:00:31" VmDisplayName="dbserver01" UID="urn:veeam:BackupTaskSession:c8de8f77-46d7-4671-b789-f490cd710692">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/147e88c6-f806-4a45-ae9c-01ad4bfa062f" Name="Backup Job 1@2025-05-12 05:00:11" />           <Link Rel="Alternate" Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/c8de8f77-46d7-4671-b789-f490cd710692" Name="dbserver01@2025-05-12 05:00:31" />         </Links>         <JobSessionUid>urn:veeam:BackupJobSession:147e88c6-f806-4a45-ae9c-01ad4bfa062f</JobSessionUid>         <CreationTimeUTC>2025-05-12T05:00:31.12Z</CreationTimeUTC>         <EndTimeUTC>2025-05-12T05:01:58.407Z</EndTimeUTC>         <State>Completed</State>         <Result>Failed</Result>         <Reason>Hard disk 1 (0 B)</Reason>         <TotalSize>0</TotalSize>         <VmUid>urn:VMware:Vm:de28dc43-b8ee-4e17-8e63-3d38b6604033.vm-62228</VmUid>       </BackupTaskSession>     </BackupTaskSessions>   </Entities>   <PagingInfo PagesCount="7" PageSize="3" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=BackupTaskSession&format=Entities&sortDesc=CreationTime&pageSize=3&page=1&filter=Result==Failed;VmDisplayName==dbserver01" />       <Link Rel="Next" Href="https://localhost:9398/api/query?type=BackupTaskSession&format=Entities&sortDesc=CreationTime&pageSize=3&page=2&filter=Result==Failed;VmDisplayName==dbserver01" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=BackupTaskSession&format=Entities&sortDesc=CreationTime&pageSize=3&page=7&filter=Result==Failed;VmDisplayName==dbserver01" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-28

