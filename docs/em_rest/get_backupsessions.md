---
title: "GET /backupSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupsessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupSessions


Returns a resource representation of a collection of all backup job sessions performed on all backup servers connected to Veeam Backup Enterprise Manager. Note, the request only returns the sessions that has been created for the last 30 days.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of backup sessions, send the [GET /query?type=BackupJobSession](get_query_backupjobsession.md) request. |

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* Microsoft Hyper-V

Request

To get a list of all sessions for backup job, send the GET HTTP request to the /backupSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupSessions |

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

In the response body, the REST API returns a representation of the /backupSessions resource collection.

Example

The example below returns a list of sessions for backup jobs on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/d2b8d33e-32b5-43be-9d72-02b5d8b290d0" Name="Fileserver Backup@2025-10-19 07:32:44" UID="urn:veeam:BackupJobSession:d2b8d33e-32b5-43be-9d72-02b5d8b290d0">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://localhost:9398/api/jobs/4856ab37-2235-45e8-affe-d515878b01a9" Name="Fileserver Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://localhost:9398/api/backupSessions/d2b8d33e-32b5-43be-9d72-02b5d8b290d0?format=Entity" Name="Fileserver Backup@2025-10-19 07:32:44" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://localhost:9398/api/backupSessions/d2b8d33e-32b5-43be-9d72-02b5d8b290d0/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/bce9741f-d6aa-43ca-a229-1706c2eea0e7" Name="vApp 01 Backup Job@2025-10-19 06:05:03" UID="urn:veeam:BackupJobSession:bce9741f-d6aa-43ca-a229-1706c2eea0e7">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://localhost:9398/api/jobs/b41fdf6f-9adc-473d-8086-6fc6e17117d0" Name="vApp 01 Backup Job" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://localhost:9398/api/backupSessions/bce9741f-d6aa-43ca-a229-1706c2eea0e7?format=Entity" Name="vApp 01 Backup Job@2025-10-19 06:05:03" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://localhost:9398/api/backupSessions/bce9741f-d6aa-43ca-a229-1706c2eea0e7/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/6d0faaea-9e99-4aec-8135-317cc0415602" Name="Fileserver Backup@2025-10-18 15:22:16" UID="urn:veeam:BackupJobSession:6d0faaea-9e99-4aec-8135-317cc0415602">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://localhost:9398/api/jobs/4856ab37-2235-45e8-affe-d515878b01a9" Name="Fileserver Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://localhost:9398/api/backupSessions/6d0faaea-9e99-4aec-8135-317cc0415602?format=Entity" Name="Fileserver Backup@2025-10-18 15:22:16" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://localhost:9398/api/backupSessions/6d0faaea-9e99-4aec-8135-317cc0415602/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/4dcc1993-c7e8-4e4d-a82b-48716dd148a2" Name="Oracle Backup@2025-10-18 13:09:06" UID="urn:veeam:BackupJobSession:4dcc1993-c7e8-4e4d-a82b-48716dd148a2">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720" Name="Oracle Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://localhost:9398/api/backupSessions/4dcc1993-c7e8-4e4d-a82b-48716dd148a2?format=Entity" Name="Oracle Backup@2025-10-18 13:09:06" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://localhost:9398/api/backupSessions/4dcc1993-c7e8-4e4d-a82b-48716dd148a2/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/8738ca5c-bda0-44cf-973d-6d46175d7522" Name="Daily NetApp Snapshots@2025-01-01 18:10:30" UID="urn:veeam:BackupJobSession:8738ca5c-bda0-44cf-973d-6d46175d7522">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://localhost:9398/api/jobs/62638c60-74b6-4d6d-8d13-4cd32039f522" Name="Daily NetApp Snapshots" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://localhost:9398/api/backupSessions/8738ca5c-bda0-44cf-973d-6d46175d7522?format=Entity" Name="Daily NetApp Snapshots@2025-01-01 18:10:30" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://localhost:9398/api/backupSessions/8738ca5c-bda0-44cf-973d-6d46175d7522/taskSessions" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-28

