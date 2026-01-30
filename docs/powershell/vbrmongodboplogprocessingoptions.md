---
title: "VBRMongoDBOplogProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmongodboplogprocessingoptions.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# VBRMongoDBOplogProcessingOptions


Contains oplog processing options for MongoDB replica sets.

Properties

| Property | Type | Description |
| --- | --- | --- |
| BackupObject | Object | Specifies an array of MongoDB replica set and protection group objects. |
| OplogProcessingEnabled | Boolean | Enables the backup of oplogs. |
| OplogRetentionPolicy | [VBRMongoDBOplogRetentionPolicy](enums.md#VBRMongoDBOplogRetentionPolicy) | Specifies the oplog retention policy settings. |
| OplogBackupPeriod | Int32 | Specifies the interval in minutes at which the system collects the oplog backup after a full backup operation.  The default value is 15 minutes. |
| OplogRetentionPeriod | Int32 | Specifies the retention period of the oplog in the backup repository in days.  The default value is 15 days. |


