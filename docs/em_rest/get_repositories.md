---
title: "GET /repositories"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_repositories.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /repositories


Returns a resource representation of the collection of backup repositories created on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of backup repositories, send the [GET /query?type=Repository](get_query_repository.md) request. |

Request

To get a list of repositories, send the GET HTTP request to the /repositories resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/repositories |

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

In the response body, the REST API returns a representation of the /repositories resource collection.

Example

The example below returns a list of all backup repositories created on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/repositories  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   </Ref>   <Ref Type="RepositoryReference" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6" Name="Backup Volume 01" UID="urn:veeam:Repository:bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Repository" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6?format=Entity" Name="Backup Volume 01" />       <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6/backups" />       <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6/replicas" />     </Links>   </Ref>   <Ref Type="RepositoryReference" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55" Name="Default Backup Repository" UID="urn:veeam:Repository:cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Repository" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55?format=Entity" Name="Default Backup Repository" />       <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55/backups" />       <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55/replicas" />     </Links>   </Ref>   <Ref Type="RepositoryReference" Href="https://localhost:9398/api/repositories/eed5ff37-79f4-4d2b-bad6-7c82b399ba61" Name="Alpha Repository" UID="urn:veeam:Repository:eed5ff37-79f4-4d2b-bad6-7c82b399ba61">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Repository" Href="https://localhost:9398/api/repositories/eed5ff37-79f4-4d2b-bad6-7c82b399ba61?format=Entity" Name="Alpha Repository" />       <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/eed5ff37-79f4-4d2b-bad6-7c82b399ba61/backups" />       <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/eed5ff37-79f4-4d2b-bad6-7c82b399ba61/replicas" />     </Links>   </Ref>   <Ref Type="RepositoryReference" Href="https://localhost:9398/api/repositories/98fbd079-f5ae-48f8-8ec2-e148333fef93" Name="Omega Cloud Vol1" UID="urn:veeam:Repository:98fbd079-f5ae-48f8-8ec2-e148333fef93">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="Repository" Href="https://localhost:9398/api/repositories/98fbd079-f5ae-48f8-8ec2-e148333fef93?format=Entity" Name="Omega Cloud Vol1" />       <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/98fbd079-f5ae-48f8-8ec2-e148333fef93/backups" />       <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/98fbd079-f5ae-48f8-8ec2-e148333fef93/replicas" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

