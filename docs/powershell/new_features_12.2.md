---
title: "New Features"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new_features_12.2.html"
last_updated: "9/2/2024"
product_version: "13.0.1.1071"
---

# New Features


This section contains information on new features that were introduced in Veeam PowerShell v12.2.

Replication

In this version, you can run new cmdlets to create and manage replica re-IPv6 rules.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRViReplicaReIpIPv6Rule](new-vbrvireplicareipipv6rule.md) | Creates a new VMware replica re-IPv6 rule. | | [New-VBRHvReplicaReIpIPv6Rule](new-vbrhvreplicareipipv6rule.md) | Creates a new Hyper-V replica re-IPv6 rule. | |

Unstructured Data Backup

In this version, you can run new cmdlets to add Microsoft Azure Blob Storage or Microsoft Azure Data Lake object storage repositories as unstructured data source to the inventory and manage their settings.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRAzureStorageServer](add-vbrazurestorageserver.md) | Adds Microsoft Azure object storage as unstructured data source to the inventory. | | [Set-VBRAzureStorageServer](set-vbrazurestorageserver.md) | Modifies settings of Microsoft Azure object storage added as unstructured data source to the inventory. | |

Veeam Plug-Ins for Enterprise Applications

This section describes new cmdlets for managing application backup policies for MongoDB.

Application Backup Policy Settings for MongoDB Backup

In this version, you can run new cmdlets to perform and manage MongoDB backups.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Add-VBRMongoDBBackupJob](add-vbrmongodbbackupjob.md) | Creates MongoDB backup policies. | | [Set-VBRMongoDBBackupJob](set-vbrmongodbbackupjob.md) | Modifies MongoDB backup policies. | | [Get-VBRMongoDBComputer](get-vbrmongodbcomputer.md) | Returns a list of all computers within specified replica sets. | | [New-VBRMongoDBContainer](new-vbrmongodbcontainer.md) | Creates a MongoDB container for an array of existing custom credentials. | | [Set-VBRMongoDBContainer](set-vbrmongodbcontainer.md) | Modifies MongoDB containers that include an array of custom credentials. | | [New-VBRMongoDBCustomCredentials](new-vbrmongodbcustomcredentials.md) | Creates custom credentials for computers within MongoDB replica sets to be selected for backup operations. | | [New-VBRMongoDBDeployment](new-vbrmongodbdeployment.md) | Connects to and adds MongoDB replica sets to protection groups. | | [New-VBRMongoDBProcessingOptions](new-vbrmongodbprocessingoptions.md) | Creates processing options for each MongoDB replica set. | | [Set-VBRMongoDBProcessingOptions](set-vbrmongodbprocessingoptions.md) | Modifies processing options for each MongoDB replica set. | |


