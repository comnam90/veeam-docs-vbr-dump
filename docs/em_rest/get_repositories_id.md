---
title: "GET /repositories/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_repositories_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a backup repository having the specified ID. The backup repository is created on the backup server connected to Veeam Backup Enterprise Manager.

Request

To get a backup repository, send the GET HTTP request to the /repositories/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/repositories/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /repositories/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the backup repository resource, for example: urn:veeam:Repository:b609c947-dd30-4295-8b57-cc880329dbd6. |
| Name | String | Name of the backup repository, for example: Backups Vol2. |
| Capacity | Int64 | Total space available on the backup repository. |
| FreeSpace | Int64 | Free space available on the backup repository. |
| Kind | String | Type of the backup repository. Possible values:   * WindowsLocal * LinuxLocal * CifsShare * DDBoost * Cloud * HPStoreOnce * ExaGrid * Foreign * SanSnapshot * HPStoreOnceIntegration * Extendable * Quantum * Nfs |

To view query parameters that you can use for filtering or sorting, see  [GET /query?type=Repository](get_query_repository.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that contains the repository in the backup infrastructure. |
| /repositories/{ID} | Alternate | Alternate URL of the [/repositories/{ID}](repositories_id.md) resource. |
| /repositories/{ID}/backups | Down | URL of the [/backups](backups.md) resource — a collection of backups stored in the backup repository. |
| /repositories/{ID}/replicas | Down | URL of the [/replicas](replicas.md) resource — a collection of replicas whose metadata is stored in the backup repository. |

Example

The example below returns a backup repository having ID bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6.

|  |
| --- |
| Request:  GET https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Repository xmlns="http://www.veeam.com/ent/v1.0" Type="Repository" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6?format=Entity" Name="Backup Volume 01" UID="urn:veeam:Repository:bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
