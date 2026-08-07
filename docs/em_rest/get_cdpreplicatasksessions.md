---
title: "GET /cdpReplicaTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplicatasksessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cdpReplicaTaskSessions


Returns a collection of CDP replication task sessions that run on backup servers connected to Veeam Backup Enterprise Manager. Note, the request only returns the sessions that has been created for the last 30 days.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of CDP replication task sessions, send the [GET /query?type=CdpReplicaTaskSession](get_query_cdpreplicatasksession.md) request. |

Request

To get a collection of CDP replication task sessions, send the GET HTTP request to the /cdpReplicaTaskSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplicaTaskSessions |

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

In the response body, the REST API returns a representation of the /cdpReplicaTaskSessions resource collection.

Example

The example below returns a list of all CDP replication task sessions that run on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplicaTaskSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/2ec4d35f-b5d8-4cb3-9d11-12e1d5792625" Name="virt03-ubuntu01@2025-02-12 00:00:10" UID="urn:veeam:CdpReplicaTaskSession:2ec4d35f-b5d8-4cb3-9d11-12e1d5792625">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/2ec4d35f-b5d8-4cb3-9d11-12e1d5792625?format=Entity" Name="virt03-ubuntu01@2025-02-12 00:00:10" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/9ce23efa-6378-4042-93a2-58733449c261" Name="virt03-vm02@2025-02-11 17:22:52" UID="urn:veeam:CdpReplicaTaskSession:9ce23efa-6378-4042-93a2-58733449c261">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8" Name="CDP Policy 2@2025-02-11 17:13:47" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/9ce23efa-6378-4042-93a2-58733449c261?format=Entity" Name="virt03-vm02@2025-02-11 17:22:52" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/d6dc67ab-90a1-4c5e-825b-897d16d166b0" Name="virt03-vm01@2025-02-11 17:12:56" UID="urn:veeam:CdpReplicaTaskSession:d6dc67ab-90a1-4c5e-825b-897d16d166b0">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/40fa1841-227c-4b07-aeca-5d84e6816c8b" Name="CDP Policy 1@2025-02-11 17:12:45" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/d6dc67ab-90a1-4c5e-825b-897d16d166b0?format=Entity" Name="virt03-vm01@2025-02-11 17:12:56" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/9ca90d43-a145-4ab1-9840-8cd29805e8ea" Name="virt03-vm02@2025-02-11 17:13:48" UID="urn:veeam:CdpReplicaTaskSession:9ca90d43-a145-4ab1-9840-8cd29805e8ea">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8" Name="CDP Policy 2@2025-02-11 17:13:47" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/9ca90d43-a145-4ab1-9840-8cd29805e8ea?format=Entity" Name="virt03-vm02@2025-02-11 17:13:48" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/54c47e13-e599-4e75-9c67-9377d54e9fde" Name="virt03-vm01@2025-02-11 19:15:52" UID="urn:veeam:CdpReplicaTaskSession:54c47e13-e599-4e75-9c67-9377d54e9fde">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/54c47e13-e599-4e75-9c67-9377d54e9fde?format=Entity" Name="virt03-vm01@2025-02-11 19:15:52" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/a583a5af-b2dc-43d2-8150-ae12acf75ec5" Name="virt03-vm01@2025-02-11 19:08:40" UID="urn:veeam:CdpReplicaTaskSession:a583a5af-b2dc-43d2-8150-ae12acf75ec5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/a583a5af-b2dc-43d2-8150-ae12acf75ec5?format=Entity" Name="virt03-vm01@2025-02-11 19:08:40" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/3e7687b2-7eb1-499c-ae2a-b01c99336a86" Name="virt03-ubuntu01@2025-02-11 23:49:16" UID="urn:veeam:CdpReplicaTaskSession:3e7687b2-7eb1-499c-ae2a-b01c99336a86">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/3e7687b2-7eb1-499c-ae2a-b01c99336a86?format=Entity" Name="virt03-ubuntu01@2025-02-11 23:49:16" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/dedd78c4-2ace-4203-a2be-ca051d4fc86e" Name="virt03-vm02@2025-02-11 20:00:26" UID="urn:veeam:CdpReplicaTaskSession:dedd78c4-2ace-4203-a2be-ca051d4fc86e">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8" Name="CDP Policy 2@2025-02-11 17:13:47" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/dedd78c4-2ace-4203-a2be-ca051d4fc86e?format=Entity" Name="virt03-vm02@2025-02-11 20:00:26" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/41b57841-7f15-4400-b224-e55851605364" Name="virt03-ubuntu01@2025-02-11 23:36:35" UID="urn:veeam:CdpReplicaTaskSession:41b57841-7f15-4400-b224-e55851605364">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/41b57841-7f15-4400-b224-e55851605364?format=Entity" Name="virt03-ubuntu01@2025-02-11 23:36:35" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/92aca37b-6ccd-470c-8808-ea9f0b5bf1b3" Name="virt03-vm01@2025-02-12 00:00:08" UID="urn:veeam:CdpReplicaTaskSession:92aca37b-6ccd-470c-8808-ea9f0b5bf1b3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/92aca37b-6ccd-470c-8808-ea9f0b5bf1b3?format=Entity" Name="virt03-vm01@2025-02-12 00:00:08" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-28

