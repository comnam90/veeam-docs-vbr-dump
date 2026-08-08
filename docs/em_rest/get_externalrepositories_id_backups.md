---
title: "GET /externalRepositories/{ID}/backups"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_externalrepositories_id_backups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /externalRepositories/{ID}/backups


Returns a resource representation of a collection of all backups on backup servers connected to Veeam Backup Enterprise Manager filtered by an external repository with a specified ID as a target repository. The backups are also represented in the [/backups](backups.md) resource collection.

Request

To get a list of backups, send the GET HTTP request to the /externalRepositories/{ID}/backups resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/externalRepositories/{ID}/backups |

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

In the response body, the REST API returns a representation of the /externalRepositories/{ID}/backups resource collection.

Example

The example below returns a list of all backups from an external repository having the specified ID.

|  |
| --- |
| Request:  GET https://localhost:9398/api/externalRepositories/{ID}/backups  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:Backup:752b210a-0b35-4db8-b864-62c742aaa7b8" Name="AborWin2025r2\_i-0e274c7b93d261e28 Backup (AborCPM25\_07)" Href="http://local.host:9399/api/backups/752b210a-0b35-4db8-b864-62c742aaa7b8" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae" Name="External repository" Type="ExternalRepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/752b210a-0b35-4db8-b864-62c742aaa7b8?format=Entity" Name="AborWin2025r2\_i-0e274c7b93d261e28 Backup (AborCPM25\_07)" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/752b210a-0b35-4db8-b864-62c742aaa7b8/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/backups/50b010e6-4522-492a-a18e-d430c1bd4384" Name="Parent Backup" Type="BackupReference" Rel="Up"/>     </Links>   </Ref>   <Ref UID="urn:veeam:Backup:50b010e6-4522-492a-a18e-d430c1bd4384" Name="AborCPM25\_07" Href="http://local.host:9399/api/backups/50b010e6-4522-492a-a18e-d430c1bd4384" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae" Name="External repository" Type="ExternalRepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/50b010e6-4522-492a-a18e-d430c1bd4384?format=Entity" Name="AborCPM25\_07" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/50b010e6-4522-492a-a18e-d430c1bd4384/childbackups" Type="BackupReferenceList" Rel="Up"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

