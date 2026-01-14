---
title: "get_nas_fileservers_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas_fileservers_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of the file share with the specified ID. The file share is added on a backup server connected to Veeam Backup Enterprise Manager.

Request

To get a resource representation of the file share, send the GET HTTP request to the /nas/fileServers/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/fileServers/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/fileServers/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /nas/fileServers/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the file share, for example: urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c. |
| Name | String | Name of the file share, for example: \\srv12\share. |
| ServerType | String | Type of the file share:   * FileServer * SmbServer * NfsServer |
| HierarchyObjRef | HierarchyObjRefType | Reference to the file share, for example: urn:NasBackup:FileServer:35ab6523-0e40-4d92-a0ea-11465791cd91.1131bc00-36c0-4355-87fc-7f748aceb978. |
| SmbServerOptions | SmbServerOptionsInfoType | Access settings for an SMB server. For details, see [SMB Server Options](#smb). |
| NfsServerOptions | FNfsServerOptionsInfoType | Access settings for an NFS server. For details, see [NFS Server Options](#nfs). |
| FileServerOptions | FileServerOptionsInfoType | Access settings for a file server. For details, see [File Server Options](#file). |
| ProcessingOptions | ProcessingOptionsInfoType | File share processing settings. For details, see [Processing Options](#processing). |
| NASServerAdvancedOptions | NASServerAdvancedOptionsInfoType | Advanced settings for the file share. For details, see [NAS Server Advanced Options](#nas). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=FileServer](get_query_fileserver.md).

SMB Server Options

The SmbServerOptions element contains the following SMB server options.

| Element | Type | Description |
| --- | --- | --- |
| Path | String | Path to an SMB file share. |
| CredentialsId | String | Credentials that are used to access the shared folder. |

NFS Server Options

The NfsServerOptions element contains the following NFS server options.

| Element | Type | Description |
| --- | --- | --- |
| Path | String | Path to an NFS file share. |

File Server Options

The FileServerOptions element contains the following file server options.

| Element | Type | Description |
| --- | --- | --- |
| ServerUid | UidType | UID of a managed server, for example: urn:veeam:FileServer:f5d9ea1f-ef70-4e51-af3d-c760380d5347. |

Processing Options

The ProcessingOptions element contains the following processing options.

| Element | Type | Description |
| --- | --- | --- |
| ServerUid | UidType | UID of a file server. |
| CacheRepositoryUid | UidType | UID of a cache repository where temporary cache files are stored. |

NAS Server Advanced Options

The NASServerAdvancedOptions element contains the following NAS server advanced options.

| Element | Type | Description |
| --- | --- | --- |
| ProcessingMode | String | Processing mode that defines if Veeam Backup & Replication uses snapshots for backups. |
| StorageSnapshotPath | String | Path to the folder on the file share where the file share snapshot is saved. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that contains the file server in the backup infrastructure. |
| /nas/fileServers//{ID} | Alternate | Alternate URL of the [/nas/fileServers/{ID}](nas_fileservers_id.md) resource. |

Example

The example below returns an entity representation of the file share having ID 517be4c8-9c43-4e7c-9f59-4e368d3a8f3c.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas/fileServers/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <FileServer xmlns="http://www.veeam.com/ent/v1.0" Type="FileServer" Href="https://srv12.tech.local:9398/api/nas/fileServers/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c?format=Entity" Name="\\srv12\share" UID="urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
