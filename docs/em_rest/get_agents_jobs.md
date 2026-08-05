---
title: "GET /agents/jobs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_jobs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /agents/jobs


Returns a resource representation of a collection of Veeam Agent backup jobs configured in Veeam Backup & Replication on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of Veeam Agent backup jobs, send the [GET /query?type=AgentBackupJob](get_query_agentbackupjob.md) request. |

Request

To get a list of Veeam Agent backup jobs configured in Veeam Backup & Replication on all backup servers connected to Veeam Backup Enterprise Manager, send the GET HTTP request to the /agents/jobs resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/jobs |

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

In the response body, the REST API returns a representation of the /agents/jobs resource collection.

Example

The example below returns a list of all Veeam Agent backup jobs on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/jobs  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:AgentBackupJob:92346ee0-5191-4556-a9c6-ed1a38cdc71b" Name="Agent Backup Job 1" Href="http://local.host:9399/api/agents/jobs/92346ee0-5191-4556-a9c6-ed1a38cdc71b" Type="AgentBackupJobReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/35dfeff8-5104-403b-a208-06e2d9a1da0b" Name="win10x64.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/92346ee0-5191-4556-a9c6-ed1a38cdc71b?format=Entity" Name="Agent Backup Job 1" Type="Job" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/jobs/92346ee0-5191-4556-a9c6-ed1a38cdc71b/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentBackupJob:4dc5d947-9c23-4e1b-976a-ee5911f6a996" Name="Agent Backup rhel72 lvm" Href="http://local.host:9399/api/agents/jobs/4dc5d947-9c23-4e1b-976a-ee5911f6a996" Type="AgentBackupJobReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/4dc5d947-9c23-4e1b-976a-ee5911f6a996?format=Entity" Name="Agent Backup rhel72 lvm" Type="Job" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/jobs/4dc5d947-9c23-4e1b-976a-ee5911f6a996/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentBackupJob:95f84a48-6e05-459a-8f26-f2330c9efdf5" Name="Agent Backup Job SQL" Href="http://local.host:9399/api/agents/jobs/95f84a48-6e05-459a-8f26-f2330c9efdf5" Type="AgentBackupJobReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/95f84a48-6e05-459a-8f26-f2330c9efdf5?format=Entity" Name="Agent Backup Job SQL" Type="Job" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/jobs/95f84a48-6e05-459a-8f26-f2330c9efdf5/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

