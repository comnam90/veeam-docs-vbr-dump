---
title: "GET /externalRepositories/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_externalrepositories_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /externalRepositories/{ID}


Returns a resource representation of an external backup repository having the specified ID. The external backup repository is added to the backup server connected to Veeam Backup Enterprise Manager.

Request

To get a backup repository, send the GET HTTP request to the /externalRepositories/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/externalRepositories/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /externalRepositories/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the external backup repository resource, for example: urn:veeam:ExternalRepository:b609c947-dd30-4295-8b57-cc880329dbd6. |
| Name | String | Name of the external backup repository, for example: Backups Vol2. |
| RepositoryType | String | Type of the external backup repository. Possible values:   * AmazonS3External * AzureStorageExternal * GoogleCloudStorageExternal |
| Path | String | Path to the external backup repository. |
| UsedSpace | Long | Space used on the external backup repository. |
| Description | String | Description the external backup repository. |

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that contains the external backup repository in the backup infrastructure. |
| /externalRepositories/{ID} | Alternate | Alternate URL of the [/externalRepositories/{ID}](externalrepositories_id.md) resource. |
| /externalRepositories/{ID}/backups | Down | URL of the [/externalRepositories/{ID}/backups](externalrepositories_id_backups.md) resource — a collection of backups stored in the external backup repository. |

Example

The example below returns a backup repository having ID 06ff6c99-f457-4fd3-87da-4d00291d3eae.

|  |
| --- |
| Request:  GET https://localhost:9398/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <ExternalRepository Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae?format=Entity" Type="ExternalRepository" Name="External repository" UID="urn:veeam:ExternalRepository:06ff6c99-f457-4fd3-87da-4d00291d3eae" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae" Name="External repository" Type="ExternalRepositoryReference" Rel="Alternate"/>     <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae/backups" Type="BackupReferenceList" Rel="Down"/>   </Links>   <RepositoryType>AmazonS3External</RepositoryType>   <Path>amazonS3://amazon/repository</Path>   <UsedSpace>10037476573</UsedSpace>   <Description>Created by srv02\admin.</Description> </ExternalRepository> |

Page updated 2026-07-29

