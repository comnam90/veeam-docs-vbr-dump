---
title: "Guest Processing Options"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/guestprocessingoptions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The GuestProcessingOptions element contains the following guest processing options.

| Element | Type | Description |
| --- | --- | --- |
| VssSnapshotOptions | VssSnapshotOptionsType | Application-aware processing options. For details, see [Application-Aware Processing Options](#vss). |
| WindowsGuestFSIndexingOptions | WindowsGuestFSIndexingOptionsType | Options for Microsoft Windows OS file indexing. For details, see [File Indexing Options](#index). |
| LinuxGuestFSIndexingOptions | LinuxGuestFSIndexingOptionsType | Options for Linux OS file indexing. For details, see [File Indexing Options](#index). |
| SQLBackupOptions | SqlBackupOptionsType | Options for Microsoft SQL and Oracle database transaction logs backup. For details, see [SQL Backup Options](#sql). |
| WindowsCredentialsId | String | ID of guest OS credentials for starting the indexing runtime process in Microsoft Windows OS. |
| LinuxCredentialsId | String | ID of guest OS credentials for starting the indexing runtime process in Linux OS. |
| FSFileExcludeOptions | FSFileExcludeOptionsType | File exclusion options. For details, see [File Exclusion Options](#exclude). |
| OracleBackupOptions | OracleBackupOptionsType | Options for Oracle database backup. For details, see [Oracle Backup Options](#oracle). |

Application-Aware Processing Options

The VssSnapshotOptions element contains the following application-aware processing options.

| Element | Type | Description |
| --- | --- | --- |
| VssSnapshotMode | String | Mode of application-aware image processing. Possible values:   * RequireSuccess * IgnoreFailures * Disabled |
| IsCopyOnly | Boolean | Defines whether copy-only backups must be created or transaction logs for Microsoft Exchange, Microsoft SQL and Oracle VMs must be processed. Possible values:   * True * False   If you set this option to False, you should pass parameters for transaction log handling:   * In the [SqlBackupOptions](#sql) element — for Microsoft SQL VMs * In the [OracleBackupOptions](#oracle) element — for Oracle VMs |
| UsePersistentGuestAgent | Boolean | Defines whether to use persistent guest agents on the protected VM for application-aware processing. Possible values:   * True * False   The default value is False. |

File Indexing Options

The WindowsGuestFSIndexingOptions and LinuxGuestFSIndexingOptions elements contain the following application-aware processing options.

| Element | Type | Description |
| --- | --- | --- |
| FileSystemIndexingMode | String | File indexing options. Possible values:   * EveryFolders * SpecifiedFolders * ExceptSpecifiedFolders |
| IncludedIndexingFolders | StringListType | List of folders that must be indexed. This parameter should be specified if the SpecifiedFolders option is passed in the FileSystemIndexingMode parameter. |
| ExcludedIndexingFolders | StringListType | List of folders that must be excluded from indexing. This parameter should be specified if the ExceptSpecifiedFolders option is passed in the FileSystemIndexingMode parameter. |

SQL Backup Options

The SqlBackupOptions element contains the following application-aware processing options.

| Element | Type | Description |
| --- | --- | --- |
| TransactionLogsProcessing | String | Transaction logs processing mode. Possible values:   * OnlyOnSuccessJob * Backup |
| BackupLogsFrequencyMin | Int | Frequency for transaction logs backup in minutes. |
| UseDbBackupRetention | Boolean | Defines whether retention policy is set for transaction logs backup. |
| RetainDays | Int | Number of days for transaction logs to be kept. This parameter should be specified if the UseDbBackupRetention option is set to True. |

File Exclusion Options

The FSFileExcludeOptions element contains the following application-aware processing options.

| Element | Type | Description |
| --- | --- | --- |
| BackupScope | Int | Guest OS file exclusion mode. Possible values:   * 1 * 2 |
| IncludeList | StringListType | List of files and folders that must be included in the backup. This parameter should be specified if the 1 value is passed in the BackupScope parameter. |
| ExcludeList | StringListType | List of files and folders that must be excluded from the backup. This parameter should be specified if the 2 value is passed in the BackupScope parameter. |

Oracle Backup Options

The OracleBackupOptions element contains the following application-aware processing options.

| Element | Type | Description |
| --- | --- | --- |
| BackupLogsEnabled | Boolean | Defines whether transaction logs backup is enabled. Possible values:   * True * False |
| BackupLogsFrequencyMin | Int | Frequency for transaction logs backup in minutes. This parameter should be specified if the BackupLogsEnabled option is set to True. |
| UseDbBackupRetention | Boolean | Defines whether retention policy is set for transaction logs backup. |
| RetainDays | Int | Number of days for transaction logs to be kept. This parameter should be specified if the UseDbBackupRetention option is set to True. |
| ArchivedLogsTruncation | String | Archived logs truncation mode. Possible values:   * ByAge * BySize |
| ArchivedLogsMaxAgeHours | Int | Time period in hours for archived logs to be kept. This parameter should be specified if the ByAge option is passed in the ArchivedLogsTruncation parameter. |
| ArchivedLogsMaxSizeMb | Int | Maximum size for archived logs in gigabytes. This parameter should be specified if the BySize option is passed in the ArchivedLogsTruncation parameter. |
| SysdbaCredsId | String | Credentials of the account that has SYSDBA rights on the Oracle database. This parameter should be specified if you use separate accounts to access the VM guest OS and to connect to the Oracle database. Otherwise, credentials passed in the WindowsCredentialsId/LinuxCredentialsId parameter will be used. |
| ProxyAutoSelect | Boolean | Defines whether automatic log shipping server selection is enabled. |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
