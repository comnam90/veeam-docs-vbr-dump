---
title: "GET /nas/jobs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas_jobs_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /nas/jobs/{ID}


Returns a resource representation of the file share backup job resource having the specified ID. The file share backup job is configured in Veeam Backup & Replication.

Request

To get a resource representation of the file share backup job, send the GET HTTP request to the /nas/jobs/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/jobs/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /nas/jobs/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the file share backup job, for example: urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2. |
| Name | String | Name of the file share backup job, for example: Shared Files Backup. |
| Description | String | Description of the file share backup job. |
| Includes | NASObjectListType | Includes a list of file shares processed by the job. For details, see [GET /nas/jobs/{ID}/includes](get_nas_jobs_id_includes.md). |
| StorageOptions | NASJobStorageOptionsInfoType | Defines backup and archive repositories where the file share backup job must store backup files, and settings for moving files and folders to these repositories. For details, see [Storage Options](#storageoptions). |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the job. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the job. Possible values:   * True * False |
| JobScheduleOptions | ScheduleOptionsInfoType | Options that define the schedule by which the job runs. For details, see [Job Scheduling Options](jobscheduleoptions.md). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=NasJob](get_query_nasjob.md).

Storage Options

The StorageOptions element contains the following storage options.

| Element | Type | Description |
| --- | --- | --- |
| BackupRepositoryUid | UidType | UID of the backup repository where backup files must be stored, for example: urn:veeam:Repository:88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec. |
| ShorttermRetentionType | String | Retention policy type for the short-term repository. Possible values:   * Day * Month |
| ShorttermRetentionPeriod | Int | Time period to keep data in the backup repository. When this period is passed, Veeam Backup & Replication moves data to the archive repository if the long-term retention is enabled. |
| LongtermRetentionEnabled | Boolean | Defines whether the long-term retention is enabled. Possible values:   * True * False |
| KeepFileVersionsHistoryOptions | NASJobStorageKeepFileVersionsHistory | Archiving settings. For details, see [Long-Term Retention Settings](#ltr). |
| NASJobAdvancedStorageOptions | NASJobAdvancedStorageOptionsInfoType | Advanced storage settings. For details, see [Advanced Storage Settings](#advanced). |

Long-Term Retention Settings

The KeepFileVersionsHistoryOptions element contains the following archiving settings.

| Element | Type | Description |
| --- | --- | --- |
| LongtermRetentionType | String | Retention policy type for the short-term repository. Possible values:   * Month * Year |
| LongtermRetentionPeriod | Int | Time period to keep data in the backup repository. When this period is passed, Veeam Backup & Replication moves data to the archive repository if the long-term retention is enabled. |
| BackupRepositoryUid | UidType | UID of the archive repository where backup files must be stored, for example: urn:veeam:Repository:d4b5e196-f3ad-474c-99bc-dfef051dae07. |
| ArchiveFileTypes | NASLongTermArchivalOptionsInfoType | Files that must be archived or excluded from the archive. For detail, see [Long-Term Archival Options](#lta). |

Long-Term Archival Options

The ArchiveFileTypes element contains the following long-term archival options.

| Element | Type | Description |
| --- | --- | --- |
| ActiveFileRetentionEnabled | Boolean | Defines whether retention for active files (files currently existing in the source file share) is enabled. Possible values:   * True * False |
| MaxActiveFileVersionsToKeep | Int | Number of versions to be stored for active files. |
| DeletedFileRetentionEnabled | Boolean | Defines whether retention for deleted files (files deleted from the source file share) is enabled. Possible values:   * True * False |
| MaxDeletedFileVersionsToKeep | Int | Number of versions to be stored for deleted files. |
| FileExtensionsOption | NASJobFileExtensionsOptionsInfoType | Defines extensions of files that must be archived or excluded from the archive. For detail, see [File Extensions](#fileextensions). |

File Extensions

The FileExtensionsOption element contains the following file extensions options.

| Element | Type | Description |
| --- | --- | --- |
| ArchiveFileExtensionsScope | String | Type of the file scope. Possible values   * Any * Specified * ExceptSpecified |
| InclusionMask | FileExtensionInfoListType | File extensions for files to be archived. Represents a list of string Extension parameters. |
| ExclusionMask | FileExtensionInfoListType | File extensions for files to be excluded from the archive. Represents a list of string Extension parameters. |

Advanced Storage Settings

The NASJobAdvancedStorageOptions element contains the following advanced storage settings.

| Element | Type | Description |
| --- | --- | --- |
| ACL | NASJobAdvancedStorageOptionsSecurityOptionsInfoType | Defines how the backup job processes permissions and attributes. Consists of the string FileAttributesChangeTrackingMode parameter. Possible values:   * TrackOnlyFolderAttributesChanges * TrackEverythingAttributesChanges |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the file share backup job was created. |
| /nas/jobs/{ID} | Alternate | Alternate URL of the [/nas/jobs/{ID}](nas_jobs_id.md) resource. |
| /nas/jobs/{ID}/includes | Down | URL of the [/nas/jobs/{ID}/includes](nas_jobs_id_includes.md) resource — a collection of files and folders processed by the file share backup job. |
| /nas/jobs/{ID}/toggleScheduleEnabled | ToggleScheduleEnabled | URL for the [POST /nas/jobs/{ID}/toggleScheduleEnabled](post_nas_jobs_id_actiontogglescheduleenabled.md) request. |
| /nas/jobs/{ID}/backupSessions | Down | URL of the [/nas/jobs/{ID}/backupSessions](nas_jobs_id_backupsessions.md) resource — a collection of backup job sessions performed for the file share backup job. |
| /nas/jobs/{ID}/Start | Start | URL for the [POST /nas/jobs/{ID}/start](post_nas_jobs_id_actionstart.md) request. |
| /nas/jobs/{ID}/Stop | Stop | URL for the [POST /nas/jobs/{ID}/stop](post_nas_jobs_id_actionstop.md) request. |
| /nas/jobs/{ID}/Retry | Retry | URL for the [POST /nas/jobs/{ID}/retry](post_nas_jobs_id_actionretry.md) request. |

Example

The example below returns an entity resource representation of the file share backup job having ID 93dfbb3e-f420-45cf-addc-4ee9297113f2.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <NASJob xmlns="http://www.veeam.com/ent/v1.0" Type="NasJob" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2?format=Entity" Name="Shared Files Backup" UID="urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2"> |


