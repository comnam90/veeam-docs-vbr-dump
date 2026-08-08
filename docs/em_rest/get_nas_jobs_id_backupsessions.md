---
title: "GET /nas/jobs/{ID}/backupSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas_jobs_id_backupsessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /nas/jobs/{ID}/backupSessions


Returns a resource representation of a collection of sessions performed for the file share backup job with the specified ID. File share backup job sessions are also displayed in the representation of the [/backupSessions](backupsessions.md) resource collection.

Note, the request only returns the sessions that has been created for the last 30 days.

Request

To get a list of sessions performed for the file share backup job with the specified ID, send the GET HTTP request to the /nas/jobs/{ID}/backupSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/jobs/{ID}/backupSessions |

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

In the response body, the REST API returns a representation of the /nas/jobs/{ID}/backupSessions resource.

Example

The example below returns a list of sessions performed for the file share backup job with ID d6b01759-40f0-43ee-940e-496bdd13973c.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas/jobs/d6b01759-40f0-43ee-940e-496bdd13973c/backupSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/19b6f0f8-777f-4aed-bc76-4584d7867e45" Name="NFS Share Backup@2025-01-30 20:31:10" UID="urn:veeam:BackupJobSession:19b6f0f8-777f-4aed-bc76-4584d7867e45">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/d6b01759-40f0-43ee-940e-496bdd13973c" Name="NFS Share Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/19b6f0f8-777f-4aed-bc76-4584d7867e45?format=Entity" Name="NFS Share Backup@2025-01-30 20:31:10" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/19b6f0f8-777f-4aed-bc76-4584d7867e45/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/ede4c840-1947-44e8-b179-4c77f667161d" Name="NFS Share Backup@2025-01-31 17:34:49" UID="urn:veeam:BackupJobSession:ede4c840-1947-44e8-b179-4c77f667161d">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/d6b01759-40f0-43ee-940e-496bdd13973c" Name="NFS Share Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/ede4c840-1947-44e8-b179-4c77f667161d?format=Entity" Name="NFS Share Backup@2025-01-31 17:34:49" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/ede4c840-1947-44e8-b179-4c77f667161d/taskSessions" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-28

