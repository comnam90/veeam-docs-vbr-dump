---
title: "VBRObjectToTapeJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrobjecttotapejob.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRObjectToTapeJob


Contains object to tape job.

Properties

| Property | Type | Description |
| --- | --- | --- |
| FullBackupPolicy | [VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md) | The full backup creation policy. |
| IncrementalBackupPolicy | [VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md) | The job schedule for creating incremental backups. |
| Object | VBRObjectStorageBackupJobObject[] | The object set as the source for the tape job. |
| EnableFileAclChangeTracking | bool | Enables backup of permissions and attributes for files. |

Related Commands

* [Add-VBRObjectToTapeJob](add-vbrobjecttotapejob.md)
* [Set-VBRObjectToTapeJob](set-vbrobjecttotapejob.md)


