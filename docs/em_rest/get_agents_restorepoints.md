---
title: "GET /agents/restorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_restorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /agents/restorePoints


Returns a resource representation of a restore points collection for backups created by Veeam Agent managed by Veeam Backup & Replication. Backups are created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

Request

To get a list of restore points, send the GET HTTP request to the /agents/restorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/restorePoints |

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

In the response body, the REST API returns a representation of the /agents/restorePoints resource collection.

Example

The example below returns a list of all restore points for Veeam Agent backups created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/restorePoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:RestorePoint:7be71fcb-7301-4efa-9c24-011dc67f063c" Name="Dec 18 2025  9:01PM" Href="http://local.host:9399/api/restorePoints/7be71fcb-7301-4efa-9c24-011dc67f063c" Type="RestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/f6307c50-934e-48ce-90a3-6ad0abe003bb" Name="Agent Backup Job SQL - sql12ten.local" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/7be71fcb-7301-4efa-9c24-011dc67f063c?format=Entity" Name="Dec 18 2025  9:01PM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/restorePoints/7be71fcb-7301-4efa-9c24-011dc67f063c/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/restorePoints/7be71fcb-7301-4efa-9c24-011dc67f063c/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   <Ref UID="urn:veeam:RestorePoint:1b484c7e-8cb8-4245-9969-021a148339d9" Name="Dec 17 2025  3:00AM" Href="http://local.host:9399/api/restorePoints/1b484c7e-8cb8-4245-9969-021a148339d9" Type="RestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e" Name="Agent Backup rhel72 lvm - rhel72" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/1b484c7e-8cb8-4245-9969-021a148339d9?format=Entity" Name="Dec 17 2025  3:00AM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/restorePoints/1b484c7e-8cb8-4245-9969-021a148339d9/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/restorePoints/1b484c7e-8cb8-4245-9969-021a148339d9/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   <Ref UID="urn:veeam:RestorePoint:67e4d9b0-a461-41e6-b5e8-037af89e2a88" Name="Dec 17 2025  2:00AM" Href="http://local.host:9399/api/restorePoints/67e4d9b0-a461-41e6-b5e8-037af89e2a88" Type="RestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e" Name="Agent Backup rhel72 lvm - rhel72" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/67e4d9b0-a461-41e6-b5e8-037af89e2a88?format=Entity" Name="Dec 17 2025  2:00AM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/restorePoints/67e4d9b0-a461-41e6-b5e8-037af89e2a88/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/restorePoints/67e4d9b0-a461-41e6-b5e8-037af89e2a88/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   <Ref UID="urn:veeam:RestorePoint:e9317843-b70c-4b20-89be-03b6225a12ec" Name="Dec 17 2025  1:00AM" Href="http://local.host:9399/api/restorePoints/e9317843-b70c-4b20-89be-03b6225a12ec" Type="RestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e" Name="Agent Backup rhel72 lvm - rhel72" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/e9317843-b70c-4b20-89be-03b6225a12ec?format=Entity" Name="Dec 17 2025  1:00AM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/restorePoints/e9317843-b70c-4b20-89be-03b6225a12ec/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/restorePoints/e9317843-b70c-4b20-89be-03b6225a12ec/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   <Ref UID="urn:veeam:RestorePoint:289276e1-90e9-40f2-90cb-058e0923e8ae" Name="Dec 17 2025  1:00AM" Href="http://local.host:9399/api/restorePoints/289276e1-90e9-40f2-90cb-058e0923e8ae" Type="RestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/f6307c50-934e-48ce-90a3-6ad0abe003bb" Name="Agent Backup Job SQL - sql12ten.local" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/289276e1-90e9-40f2-90cb-058e0923e8ae?format=Entity" Name="Dec 17 2025  1:00AM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/restorePoints/289276e1-90e9-40f2-90cb-058e0923e8ae/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/restorePoints/289276e1-90e9-40f2-90cb-058e0923e8ae/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   <Ref UID="urn:veeam:RestorePoint:efad73dd-904d-4542-aee1-06f6f604a3e3" Name="Dec 16 2025  6:00PM" Href="http://local.host:9399/api/restorePoints/efad73dd-904d-4542-aee1-06f6f604a3e3" Type="RestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e" Name="Agent Backup rhel72 lvm - rhel72" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/efad73dd-904d-4542-aee1-06f6f604a3e3?format=Entity" Name="Dec 16 2025  6:00PM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/restorePoints/efad73dd-904d-4542-aee1-06f6f604a3e3/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/restorePoints/efad73dd-904d-4542-aee1-06f6f604a3e3/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   <Ref UID="urn:veeam:RestorePoint:bcb83207-7af9-47cb-900d-07f97202cfe5" Name="Dec 16 2025  5:00PM" Href="http://local.host:9399/api/restorePoints/bcb83207-7af9-47cb-900d-07f97202cfe5" Type="RestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e" Name="Agent Backup rhel72 lvm - rhel72" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/bcb83207-7af9-47cb-900d-07f97202cfe5?format=Entity" Name="Dec 16 2025  5:00PM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/restorePoints/bcb83207-7af9-47cb-900d-07f97202cfe5/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/restorePoints/bcb83207-7af9-47cb-900d-07f97202cfe5/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   <Ref UID="urn:veeam:RestorePoint:930dce7a-43e1-4a79-abc2-091edf08729c" Name="Dec 16 2025  5:00AM" Href="http://local.host:9399/api/restorePoints/930dce7a-43e1-4a79-abc2-091edf08729c" Type="RestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/f6307c50-934e-48ce-90a3-6ad0abe003bb" Name="Agent Backup Job SQL - sql12ten.local" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/930dce7a-43e1-4a79-abc2-091edf08729c?format=Entity" Name="Dec 16 2025  5:00AM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/restorePoints/930dce7a-43e1-4a79-abc2-091edf08729c/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/restorePoints/930dce7a-43e1-4a79-abc2-091edf08729c/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   <Ref UID="urn:veeam:RestorePoint:ba42c34b-1420-4fb8-ae6f-0a2aa72d9117" Name="Dec 19 2025  1:01AM" Href="http://local.host:9399/api/restorePoints/ba42c34b-1420-4fb8-ae6f-0a2aa72d9117" Type="RestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/25338b6f-2c0b-4e03-b039-c200f62225e0" Name="Agent Backup Job SQL - sql2025.local" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/ba42c34b-1420-4fb8-ae6f-0a2aa72d9117?format=Entity" Name="Dec 19 2025  1:01AM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/restorePoints/ba42c34b-1420-4fb8-ae6f-0a2aa72d9117/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/restorePoints/ba42c34b-1420-4fb8-ae6f-0a2aa72d9117/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

