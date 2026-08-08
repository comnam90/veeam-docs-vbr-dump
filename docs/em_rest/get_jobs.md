---
title: "GET /jobs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_jobs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /jobs


Returns a resource representation of a collection of jobs created on all backup servers that are connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Note |
| * You can obtain a collection of jobs if you are logged in under an account with the Portal Administrator role only. * Currently the GET method returns jobs of the Backup, Replication, BackupCopy and ImmediateBackupCopy types only. |

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of jobs, send the [GET /query?type=Job](get_query_job.md) request. |

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a list of jobs created on all backup servers connected to Veeam Backup Enterprise Manager, send the GET HTTP request to the /jobs resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/jobs |

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

In the response body, the REST API returns a representation of the /jobs resource collection.

Example

The example below returns a list of all jobs created on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/jobs  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/065c3eed-175d-4fd8-89c8-2da82b0dcd4f" Name="SQL Server Replication" UID="urn:veeam:Job:065c3eed-175d-4fd8-89c8-2da82b0dcd4f">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/065c3eed-175d-4fd8-89c8-2da82b0dcd4f?format=Entity" Name="SQL Server Replication" />       <Link Rel="Down" Type="ReplicaJobSessionReferenceList" Href="https://localhost:9398/api/jobs/065c3eed-175d-4fd8-89c8-2da82b0dcd4f/replicaSessions" />     </Links>   </Ref>   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/62638c60-74b6-4d6d-8d13-4cd32039f522" Name="Daily NetApp Snapshots" UID="urn:veeam:Job:62638c60-74b6-4d6d-8d13-4cd32039f522">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/62638c60-74b6-4d6d-8d13-4cd32039f522?format=Entity" Name="Daily NetApp Snapshots" />       <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/62638c60-74b6-4d6d-8d13-4cd32039f522/backupSessions" />     </Links>   </Ref>   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720" Name="Oracle Backup" UID="urn:veeam:Job:da4a15c2-04e7-4135-b876-577249d3d720">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720?format=Entity" Name="Oracle Backup" />       <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720/backupSessions" />     </Links>   </Ref>   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/2574fb7b-aca3-485c-8e77-67ef12bd23e8" Name="Webserver Backup" UID="urn:veeam:Job:2574fb7b-aca3-485c-8e77-67ef12bd23e8">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/2574fb7b-aca3-485c-8e77-67ef12bd23e8?format=Entity" Name="Webserver Backup" />       <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/2574fb7b-aca3-485c-8e77-67ef12bd23e8/backupSessions" />     </Links>   </Ref>   <Ref Type="JobReference" Href="https://localhost:9398/api/jobs/fc764ba5-a910-416d-8e06-b6e4782f7fef" Name="Mediaserver Backup" UID="urn:veeam:Job:fc764ba5-a910-416d-8e06-b6e4782f7fef">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Job" Href="https://localhost:9398/api/jobs/fc764ba5-a910-416d-8e06-b6e4782f7fef?format=Entity" Name="Mediaserver Backup" />       <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/fc764ba5-a910-416d-8e06-b6e4782f7fef/backupSessions" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

