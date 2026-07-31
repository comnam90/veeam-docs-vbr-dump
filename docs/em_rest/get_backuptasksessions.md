---
title: "GET /backupTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backuptasksessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupTaskSessions


Returns a resource representation of a collection of backup task sessions that are performed on all backup servers connected to Veeam Backup Enterprise Manager. Note, the request only returns the sessions that has been created for the last 30 days.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of backup task sessions, send the [GET /query?type=BackupTaskSession](get_query_backuptasksession.md) request. |

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V
* Veeam Agent computers running Microsoft Windows or Linux

Request

To get a list of backup task sessions, send the GET HTTP request to the /backupTaskSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupTaskSessions |

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

In the response body, the REST API returns a representation of the /backupTaskSessions resource collection.

Example

The example below returns a list of all backup tasks performed on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupTaskSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/9c1abbfb-48a2-4042-b2f0-1ac12adecdb6" Name="VM01@2025-10-19 06:07:13" UID="urn:veeam:BackupTaskSession:9c1abbfb-48a2-4042-b2f0-1ac12adecdb6">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/bce9741f-d6aa-43ca-a229-1706c2eea0e7" Name="vApp 01 Backup Job@2025-10-19 06:05:03" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/9c1abbfb-48a2-4042-b2f0-1ac12adecdb6?format=Entity" Name="w2k3-x64-from-temmplate@2025-10-19 06:07:13" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/20caf784-f9b4-4826-b544-1ad8a99031b7" Name="dns@2025-03-01 11:27:04" UID="urn:veeam:BackupTaskSession:20caf784-f9b4-4826-b544-1ad8a99031b7">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/672d10c5-3b5c-474b-9550-e16707898b91" Name="Daily NetApp Snapshots@2025-03-01 11:25:36" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/20caf784-f9b4-4826-b544-1ad8a99031b7?format=Entity" Name="dns@2025-03-01 11:27:04" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/76051d5e-1760-4f02-819c-264f2448df97" Name="oracle@2025-10-18 13:09:58" UID="urn:veeam:BackupTaskSession:76051d5e-1760-4f02-819c-264f2448df97">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/4dcc1993-c7e8-4e4d-a82b-48716dd148a2" Name="Oracle Backup@2025-10-18 13:09:06" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/76051d5e-1760-4f02-819c-264f2448df97?format=Entity" Name="oracle@2025-10-18 13:09:58" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/b9033a9f-50bc-4c18-b8de-29107c033a13" Name="dhcp@2025-03-01 11:27:04" UID="urn:veeam:BackupTaskSession:b9033a9f-50bc-4c18-b8de-29107c033a13">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/672d10c5-3b5c-474b-9550-e16707898b91" Name="Daily NetApp Snapshots@2025-03-01 11:25:36" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/b9033a9f-50bc-4c18-b8de-29107c033a13?format=Entity" Name="dhcp@2025-03-01 11:27:04" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/88767486-89d6-4340-92f0-2ad615a8f21b" Name="srv04@2025-10-19 05:23:44" UID="urn:veeam:BackupTaskSession:88767486-89d6-4340-92f0-2ad615a8f21b">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/d46e39e0-1131-4585-91a7-e828ce7eafae" Name="Fileserver Backup@2025-10-19 05:22:52" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/88767486-89d6-4340-92f0-2ad615a8f21b?format=Entity" Name="srv04@2025-10-19 05:23:44" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/28803e33-6366-4604-83d1-2b670a4469f2" Name="sql02@2025-01-01 18:11:12" UID="urn:veeam:BackupTaskSession:28803e33-6366-4604-83d1-2b670a4469f2">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/8738ca5c-bda0-44cf-973d-6d46175d7522" Name="Daily NetApp Snapshots@2025-01-01 18:10:30" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/28803e33-6366-4604-83d1-2b670a4469f2?format=Entity" Name="sql02@2025-01-01 18:11:12" />     </Links>   </Ref> </EntityReferences |

Page updated 2026-07-28

