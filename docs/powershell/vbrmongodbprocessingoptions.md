---
title: "VBRMongoDBProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmongodbprocessingoptions.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# VBRMongoDBProcessingOptions

In this article

Contains processing options for MongoDB replica sets.

Properties

| Property | Type | Description |
| --- | --- | --- |
| BackupObject | [VBRDiscoveredMongoDB](vbrdiscoveredmongodb.md) | Specifies an array of discovered replica sets. The cmdlet adds these entities to the application backup policy. |
| AllowBackupFromPrimary | Boolean | Allows backup from primary nodes. |
| AutoSelectBackupSourceNode | Boolean | Selects the backup node automatically. |
| BackupSourceNode | [VBRDiscoveredMongoDBReplicaSetNode](vbrdiscoveredmongodbreplicasetnode.md) | Specifies the selected node to be backed up. |
| AllowBackupSourceNodeFailover | Boolean | Allows switching to automatic node selection if the manually selected node is not available and the AutoSelectBackupSourceNode parameter is not enabled. |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
