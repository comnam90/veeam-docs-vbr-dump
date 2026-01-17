---
title: "POST /jobs/{ID}/includes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_jobs_id_includes.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Adds a VM or VM container to the job.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To add a VM or VM container to the job, send the POST HTTP request to the /jobs/{ID}/includes resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/jobs/{ID}/includes |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of the VM or VM container you want to add to the job. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| HierarchyObjRef | HierarchyObjRefType | Reference to the VM or VM container added to the job. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 1/1 |
| HierarchyObjName | String | Name of the VM or VM container added to the job. | No | 1/1 |
| GuestProcessingOptions | GuestProcessing OptionsType | Options for application-aware image processing. For details, see [Guest Processing Options](guestprocessingoptions.md). | Yes | 0/1 |

Guest Processing Options

You can define the following guest processing options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VssSnapshotOptions | VssSnapshotOptionsType | Application-aware processing options. For details, see [Application-Aware Processing Options](post_jobs_id_includes.md#vss). | Yes | 0/1 |
| WindowsGuestFSIndexingOptions | WindowsGuestFSIndexingOptionsType | Options for Microsoft Windows OS file indexing. For details, see [File Indexing Options](post_jobs_id_includes.md#index). | Yes | 0/1 |
| LinuxGuestFSIndexingOptions | LinuxGuestFSIndexingOptionsType | Options for Linux OS file indexing. For details, see [File Indexing Options](post_jobs_id_includes.md#index). | Yes | 0/1 |
| SQLBackupOptions | SqlBackupOptionsType | Options for Microsoft SQL and Oracle database transaction logs backup. For details, see [SQL Backup Options](post_jobs_id_includes.md#sql). | Yes | 0/1 |
| WindowsCredentialsId | String | Guest OS credentials for starting the indexing runtime process in Microsoft Windows OS. | Yes | 0/1 |
| LinuxCredentialsId | String | Guest OS credentials for starting the indexing runtime process in Linux OS. | Yes | 0/1 |
| FSFileExcludeOptions | FSFileExcludeOptionsType | File exclusion options. For details, see [File Exclusion Options](post_jobs_id_includes.md#exclude). | Yes | 0/1 |
| OracleBackupOptions | OracleBackupOptionsType | Options for Oracle database backup. For details, see [Oracle Backup Options](post_jobs_id_includes.md#oracle). | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "HierarchyObjRef": "urn:VMware:VM:00000000-0000-0000-0000-000000000000.vm-518",   "HierarchyObjName": "oracle01",   "GuestProcessingOptions": {     "IncludedIndexingFolders": [],     "ExcludedIndexingFolders": [],     "VssSnapshotOptions": {       "VssSnapshotMode": "RequireSuccess",       "IsCopyOnly": false,       "UsePersistentGuestAgent": false     },     "WindowsGuestFSIndexingOptions": {       "FileSystemIndexingMode": "ExceptSpecifiedFolders",       "IncludedIndexingFolders": [],       "ExcludedIndexingFolders": [         "%windir%",         "%ProgramFiles%",         "%ProgramFiles(x86)%",         "%ProgramW6432%",         "%TEMP%"       ]     },     "LinuxGuestFSIndexingOptions": {       "FileSystemIndexingMode": "ExceptSpecifiedFolders",       "IncludedIndexingFolders": [],       "ExcludedIndexingFolders": [         "/cdrom",         "/dev",         "/media",         "/mnt",         "/proc",         "/tmp",         "/lost+found"       ]     },     "SqlBackupOptions": {       "TransactionLogsProcessing": "Backup",       "BackupLogsFrequencyMin": 15,       "UseDbBackupRetention": true,       "RetainDays": 15     },     "WindowsCredentialsId": "00000000-0000-0000-0000-000000000000",     "LinuxCredentialsId": "00000000-0000-0000-0000-000000000000",     "FsFileExcludeOptions": {       "BackupScope": 2,       "IncludeLists": [],       "ExcludeLists": [         "C:/TMP"       ]     },     "OracleBackupOptions": {       "BackupLogsEnabled": true,       "BackupLogsFrequencyMin": 15,       "UseDbBackupRetention": true,       "RetainDays": 15,       "ArchivedLogsTruncation": "BySize",       "ArchivedLogsMaxSizeMb": 10240,       "SysdbaCredsId": "00000000-0000-0000-0000-000000000000",       "ProxyAutoSelect": true     }   }  } |

Application-Aware Processing Options

You can define the following application-aware processing options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VssSnapshotMode | String | Mode of application-aware image processing. Possible values:   * RequireSuccess * IgnoreFailures * Disabled | Yes | — |
| IsCopyOnly | Boolean | Defines whether copy-only backups must be created or transaction logs for Microsoft Exchange, Microsoft SQL and Oracle VMs must be processed. Possible values:   * True * False   If you set this option to False, you should pass parameters for transaction log handling:   * In the [SqlBackupOptions](post_jobs_id_includes.md#sql) element — for Microsoft SQL VMs * In the [OracleBackupOptions](post_jobs_id_includes.md#oracle) element — for Oracle VMs | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <VssSnapshotOptions>   <VssSnapshotMode>RequireSuccess</VssSnapshotMode>   <IsCopyOnly>false</IsCopyOnly> </VssSnapshotOptions> |

JSON Representation

|  |
| --- |
| "VssSnapshotOptions": {    "VssSnapshotMode": "RequireSuccess",    "IsCopyOnly": false  } |

File Indexing Options

You can define the following file indexing options for the job. File indexing options should be specified separately for Microsoft Windows and Linux OS:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| FileSystemIndexingMode | String | File indexing options. Possible values:   * EveryFolders * SpecifiedFolders * ExceptSpecifiedFolders | Yes | — |
| IncludedIndexingFolders | StringListType | List of folders that must be indexed. This parameter should be specified if the SpecifiedFolders option is passed in the FileSystemIndexingMode parameter. | Yes | — |
| ExcludedIndexingFolders | StringListType | List of folders that must be excluded from indexing. This parameter should be specified if the ExceptSpecifiedFolders option is passed in the FileSystemIndexingMode parameter. | Yes | — |

For example:

XML Representation

|  |
| --- |
| <WindowsGuestFSIndexingOptions>   <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>   <IncludedIndexingFolders />   <ExcludedIndexingFolders>     <Path>%windir%</Path>     <Path>%ProgramFiles%</Path>     <Path>%ProgramFiles(x86)%</Path>     <Path>%ProgramW6432%</Path>     <Path>%TEMP%</Path>   </ExcludedIndexingFolders> </WindowsGuestFSIndexingOptions> |

JSON Representation

|  |
| --- |
| "WindowsGuestFSIndexingOptions": {   "FileSystemIndexingMode": "ExceptSpecifiedFolders",   "IncludedIndexingFolders": [],   "ExcludedIndexingFolders": [     "%windir%",     "%ProgramFiles%",     "%ProgramFiles(x86)%",     "%ProgramW6432%",     "%TEMP%"   ]  } |

SQL Backup Options

You can define the following transaction logs backup options for Microsoft SQL VMs:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| TransactionLogsProcessing | String | Transaction logs processing mode. Possible values:   * OnlyOnSuccessJob * Backup | Yes | — |
| BackupLogsFrequencyMin | Int | Frequency for transaction logs backup in minutes. | Yes | 0/1 |
| UseDbBackupRetention | Boolean | Defines whether retention policy is set for transaction logs backup. | Yes | 0/1 |
| RetainDays | Int | Number of days for transaction logs to be kept. This parameter should be specified if the UseDbBackupRetention option is set to True. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <SqlBackupOptions>   <TransactionLogsProcessing>Backup</TransactionLogsProcessing>   <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>   <UseDbBackupRetention>true</UseDbBackupRetention>   <RetainDays>15</RetainDays> </SqlBackupOptions> |

JSON Representation

|  |
| --- |
| "SqlBackupOptions": {  "TransactionLogsProcessing": "Backup",   "BackupLogsFrequencyMin": 15,   "UseDbBackupRetention": true,   "RetainDays": 15  } |

File Exclusion Options

You can define the following file exclusion options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| BackupScope | Int | Guest OS file exclusion mode. Possible values:   * 1 * 2 | Yes | — |
| IncludeList | StringListType | List of files and folders that must be included in the backup. This parameter should be specified if the 1 value is passed in the BackupScope parameter. | Yes | — |
| ExcludeList | StringListType | List of files and folders that must be excluded from the backup. This parameter should be specified if the 2 value is passed in the BackupScope parameter. | Yes | — |

For example:

XML Representation

|  |
| --- |
| <FSFileExcludeOptions>    <BackupScope>2</BackupScope>    <IncludeList />   <ExcludeList>      <Path>C:/TMP</Path>    </ExcludeList>  </FSFileExcludeOptions> |

JSON Representation

|  |
| --- |
| "FsFileExcludeOptions": {   "BackupScope": 2,   "IncludeLists": [],   "ExcludeLists": [     "C:/TMP"   ]  } |

Oracle Backup Options

You can define the following Oracle database backup options for the job:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| BackupLogsEnabled | Boolean | Defines whether transaction logs backup is enabled. Possible values:   * True * False | Yes | — |
| BackupLogsFrequencyMin | Int | Frequency for transaction logs backup in minutes. This parameter should be specified if the BackupLogsEnabled option is set to True. | Yes | 0/1 |
| UseDbBackupRetention | Boolean | Defines whether retention policy is set for transaction logs backup. | Yes | 0/1 |
| RetainDays | Int | Number of days for transaction logs to be kept. This parameter should be specified if the UseDbBackupRetention option is set to True. | Yes | 0/1 |
| ArchivedLogsTruncation | String | Archived logs truncation mode. Possible values:   * ByAge * BySize | Yes | — |
| ArchivedLogsMaxAgeHours | Int | Time period in hours for archived logs to be kept. This parameter should be specified if the ByAge option is passed in the ArchivedLogsTruncation parameter. | Yes | 0/1 |
| ArchivedLogsMaxSizeMb | Int | Maximum size for archived logs in gigabytes. This parameter should be specified if the BySize option is passed in the ArchivedLogsTruncation parameter. | Yes | 0/1 |
| SysdbaCredsId | String | Credentials of the account that has SYSDBA rights on the Oracle database. This parameter should be specified if you use separate accounts to access the VM guest OS and to connect to the Oracle database. Otherwise, credentials passed in the WindowsCredentialsId/LinuxCredentialsId parameter will be used. | Yes | — |
| ProxyAutoSelect | Boolean | Defines whether automatic log shipping server selection is enabled. | Yes | — |

For example:

XML Representation

|  |
| --- |
| <OracleBackupOptions>   <BackupLogsEnabled>true</BackupLogsEnabled>   <BackupLogsFrequencyMin>15</BackupLogsFrequencyMin>   <UseDbBackupRetention>true</UseDbBackupRetention>   <RetainDays>15</RetainDays>   <ArchivedLogsTruncation>BySize</ArchivedLogsTruncation>   <ArchivedLogsMaxSizeMb>10240</ArchivedLogsMaxSizeMb>   <SysdbaCredsId>00000000-0000-0000-0000-000000000000</SysdbaCredsId>   <ProxyAutoSelect>true</ProxyAutoSelect> </OracleBackupOptions> |

JSON Representation

|  |
| --- |
| "OracleBackupOptions": {   "BackupLogsEnabled": true,   "BackupLogsFrequencyMin": 15,   "UseDbBackupRetention": true,   "RetainDays": 15,   "ArchivedLogsTruncation": "BySize",   "ArchivedLogsMaxSizeMb": 10240,   "SysdbaCredsId": "00000000-0000-0000-0000-000000000000",   "ProxyAutoSelect": true  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 202 Accepted.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a task that has been created to perform the requested operation. To track the status of the operation, send the [GET /tasks/{ID}](get_tasks_id.md) request.

The task resource also contains a link to the task deletion operation. To stop the task execution, send the [DELETE /task/{ID}](delete_task_id.md) request to the URL in the link.

Example

The example below adds a VM having MoID vm-10266 to the job having ID f365fbd8-fbd2-43ad-9f7a-c87cd390a0d9.

|  |
| --- |
| Request:  POST https://localhost:9398/api/jobs/f365fbd8-fbd2-43ad-9f7a-c87cd390a0d9/includes    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CreateObjectInJobSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <HierarchyObjRef>urn:VMware:VM:00000000-0000-0000-0000-000000000000.vm-10266</HierarchyObjRef>   <HierarchyObjName>exch02</HierarchyObjName>   <GuestProcessingOptions>     <AppAwareProcessingMode>RequireSuccess</AppAwareProcessingMode>     <FileSystemIndexingMode>ExceptSpecifiedFolders</FileSystemIndexingMode>     <IncludedIndexingFolders/>     <ExcludedIndexingFolders>       <Path>%windir%</Path>       <Path>%ProgramFiles%</Path>       <Path>%TEMP%</Path>     </ExcludedIndexingFolders>     <CredentialsId/>   </GuestProcessingOptions> </CreateObjectInJobSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>UpdateJob</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>UpdateJob</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
