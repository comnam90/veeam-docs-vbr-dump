---
title: "GET /nas/backupSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas_backupsessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /nas/backupSessions


Returns a resource representation of a collection of sessions performed for file share backup jobs configured in Veeam Backup & Replication on all backup servers connected to Veeam Backup Enterprise Manager. File share backup job sessions are also displayed in the representation of the [/backupSessions](backupsessions.md) resource collection.

Note, the request only returns the sessions that has been created for the last 30 days.

Request

To get a list of sessions performed for file share backup jobs configured in Veeam Backup & Replication, send the GET HTTP request to the /nas/backupSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/backupSessions |

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

In the response body, the REST API returns a representation of the /nas/backupSessions resource.

Example

The example below returns a list of sessions for file share backup jobs configured in Veeam Backup & Replication on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas/backupSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/67fb7275-6c25-47ed-9232-01fdb1f49c76" Name="Shared Files Backup@2025-01-16 19:41:50" UID="urn:veeam:BackupJobSession:67fb7275-6c25-47ed-9232-01fdb1f49c76">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/67fb7275-6c25-47ed-9232-01fdb1f49c76?format=Entity" Name="Shared Files Backup@2025-01-16 19:41:50" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/67fb7275-6c25-47ed-9232-01fdb1f49c76/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/9cf2bea8-8d7d-4472-9aa4-0427d5c85af5" Name="Shared Files Backup@2025-01-29 15:00:01" UID="urn:veeam:BackupJobSession:9cf2bea8-8d7d-4472-9aa4-0427d5c85af5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/9cf2bea8-8d7d-4472-9aa4-0427d5c85af5?format=Entity" Name="Shared Files Backup@2025-01-29 15:00:01" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/9cf2bea8-8d7d-4472-9aa4-0427d5c85af5/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/02c1c7bb-c0cf-4c55-905b-05fa701df63b" Name="Shared Files Backup@2025-01-16 18:07:12" UID="urn:veeam:BackupJobSession:02c1c7bb-c0cf-4c55-905b-05fa701df63b">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/02c1c7bb-c0cf-4c55-905b-05fa701df63b?format=Entity" Name="Shared Files Backup@2025-01-16 18:07:12" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/02c1c7bb-c0cf-4c55-905b-05fa701df63b/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/b9885ec7-25bf-4b1a-a49e-08fdc71d3f34" Name="Shared Files Backup@2025-01-03 16:00:23" UID="urn:veeam:BackupJobSession:b9885ec7-25bf-4b1a-a49e-08fdc71d3f34">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/19c86016-d66b-4887-bca5-950aa821ac42" Name="Shared Files Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/b9885ec7-25bf-4b1a-a49e-08fdc71d3f34?format=Entity" Name="Shared Files Backup@2025-01-03 16:00:23" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/b9885ec7-25bf-4b1a-a49e-08fdc71d3f34/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/d80bba6e-26b4-4f07-bbf5-0b447a63b303" Name="Shared Files Backup@2025-01-21 15:00:10" UID="urn:veeam:BackupJobSession:d80bba6e-26b4-4f07-bbf5-0b447a63b303">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/d80bba6e-26b4-4f07-bbf5-0b447a63b303?format=Entity" Name="Shared Files Backup@2025-01-21 15:00:10" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/d80bba6e-26b4-4f07-bbf5-0b447a63b303/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/8fcc5d1d-fa34-46af-bbdf-10cdcb3e9f67" Name="Shared Files Backup@2025-01-24 15:00:17" UID="urn:veeam:BackupJobSession:8fcc5d1d-fa34-46af-bbdf-10cdcb3e9f67">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/8fcc5d1d-fa34-46af-bbdf-10cdcb3e9f67?format=Entity" Name="Shared Files Backup@2025-01-24 15:00:17" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/8fcc5d1d-fa34-46af-bbdf-10cdcb3e9f67/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/94d24cc8-5c92-477f-ab0d-17d197f33df5" Name="Shared Files Backup@2025-01-10 16:00:10" UID="urn:veeam:BackupJobSession:94d24cc8-5c92-477f-ab0d-17d197f33df5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/19c86016-d66b-4887-bca5-950aa821ac42" Name="Shared Files Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/94d24cc8-5c92-477f-ab0d-17d197f33df5?format=Entity" Name="Shared Files Backup@2025-01-10 16:00:10" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/94d24cc8-5c92-477f-ab0d-17d197f33df5/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/fff0575c-1ef1-457c-a07a-1a304637d840" Name="Shared Files Backup@2025-01-06 16:00:20" UID="urn:veeam:BackupJobSession:fff0575c-1ef1-457c-a07a-1a304637d840">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/19c86016-d66b-4887-bca5-950aa821ac42" Name="Shared Files Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/fff0575c-1ef1-457c-a07a-1a304637d840?format=Entity" Name="Shared Files Backup@2025-01-06 16:00:20" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/fff0575c-1ef1-457c-a07a-1a304637d840/taskSessions" />     </Links>   </Ref>  ... </EntityReferences> |

Page updated 2026-07-28

