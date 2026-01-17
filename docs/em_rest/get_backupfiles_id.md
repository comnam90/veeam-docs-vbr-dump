---
title: "GET /backupFiles/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupfiles_id.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a backup file with the specified ID. The backup file is created on or imported to the backup server connected to Veeam Backup Enterprise Manager.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a backup file, send the GET HTTP request to the /backupFiles/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupFiles/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupFiles/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /backupFiles/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the backup file resource, for example: urn:veeam:BackupFile:0874ab95-10e5-4f25-84df-2782ad81f3e5. |
| Name | String | Name of the backup file, for example: Webserver BackupD2016-09-20T175902.vib. |
| FilePath | String | Path to the backup file. |
| BackupSize | Long | Size of the backup file (in bytes). |
| DataSize | Long | Size of the backed-up data (in bytes). |
| DeduplicationRatio | Double | Data deduplication ratio. |
| CompressRatio | Double | Data compression ratio. |
| CreationTimeUtc | DateTime | Date and time when the backup file was created. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| FileType | String | Type of the backup file. Possible values:   * vbk * vib * vrb |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=BackupFile](get_query_backupfile.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backups/{ID} | Up | URL of the [/backups/{ID}](backups_id.md) parent to the backup file. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource parent to the backup file. |
| /backupFiles/{ID} | Alternate | Alternate URL of the [/backupFiles/{ID}](backupfiles_id.md) resource. |
| /backupFiles/{ID}/restorePoints | Down | URL of the [/restorePoints](restorepoints.md) resource — a collection of restore points contained in the backup file. |
| /backupFiles/{ID}/vmRestorePoints | Down | URL of the [/vmRestorePoints](vmrestorepoints.md) resource — a collection of VM restore points contained in the backup file. |

Example

The example below returns an entity resource representation of a backup file with ID 6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4:

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <BackupFile xmlns="http://www.veeam.com/ent/v1.0" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4?format=Entity" Name="Webserver Backup CopyD2016-09-20T000000.vbk" UID="urn:veeam:BackupFile:6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4"> |

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
