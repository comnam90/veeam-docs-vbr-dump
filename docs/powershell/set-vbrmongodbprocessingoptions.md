---
title: "Set-VBRMongoDBProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrmongodbprocessingoptions.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRMongoDBProcessingOptions

In this article

Short Description

Modifies processing options for each MongoDB replica set.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Switch to automatic node selection.

|  |
| --- |
| Set-VBRMongoDBProcessingOptions -Options <VBRMongoDBProcessingOptions> [-BackupObject <VBRDiscoveredMongoDB>] [-AllowBackupFromPrimary <Boolean>] [-AutoSelectBackupSourceNode]  [<CommonParameters>] |

* Switch to preferred node selection.

|  |
| --- |
| Set-VBRMongoDBProcessingOptions -Options <VBRMongoDBProcessingOptions> [-BackupObject <VBRDiscoveredMongoDB>] [-AllowBackupFromPrimary <Boolean>] [-BackupSourceNode <VBRDiscoveredMongoDBReplicaSetNode>] [-AllowBackupSourceNodeFailover <Boolean>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies and modifies MongoDB processing options to switch between two types of backup nodes selection:

* Automatic selection of backup nodes.
* Preferred selection of backup nodes.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the processing options for Veeam Application Backup for MongoDB backup operations. | Accepts the [VBRMongoDBProcessingOptions](vbrmongodbprocessingoptions.md) object. To create this object, run the [New-VBRMongoDBProcessingOptions](new-vbrmongodbprocessingoptions.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| BackupObject | Specifies an array of discovered application entities: individual computers, databases and protection groups. The cmdlet adds these entities to the application backup policy. | Accepts the [VBRDiscoveredMongoDB](vbrdiscoveredmongodb.md) object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | False | Named | True (ByPropertyName) |
| AllowBackupFromPrimary | Allows backup from primary nodes.  Note: This parameter is required only in cases where there is more than one node. | Boolean | False | Named | True (ByPropertyName) |
| AutoSelectBackupSourceNode | Selects the backup node automatically. | SwitchParameter | False | Named | True (ByPropertyName) |
| BackupSourceNode | Specifies the selected node to be backed up.  Keep in mind the following limitations for node selection:   * The node must be operational. If there are any node operational errors and the AllowBackupSourceNodeFailover parameter is enabled, you can proceed with the node selection.   If the node is primary, it must be the only operational node and the AllowBackupFromPrimary parameter must be enabled. Otherwise, the backup operation fails.   * Nodes used in previous backup operations are used again, if no node has been specifically selected. * Repeated use of a primary node in multiple backup operations is possible only if the AllowBackupFromPrimary parameter is set and there are no additional nodes. Otherwise, the backup operation fails.   Note: This parameter is not required when AutoSelectBackupSourceNode is used. | Accepts the [VBRDiscoveredMongoDBReplicaSetNode](vbrdiscoveredmongodbreplicasetnode.md) object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | False | Named | True (ByPropertyName) |
| AllowBackupSourceNodeFailover | Allows switching to automatic node selection if the manually selected node is not available and the AutoSelectBackupSourceNode parameter is not enabled. | Boolean | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRMongoDBProcessingOptions](vbrmongodbprocessingoptions.md#VBRMongoDBProcesingOptions) object that defines MongoDB database processing settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Change Existing Processing Options To Allow Backup From Primary Node

|  |  |
| --- | --- |
| This example shows how to change the existing replica set processing options to be able to perform backup operations from the primary node.  |  | | --- | | $rs = Get-VBRDiscoveredApplication -MongoDBEntityType ReplicaSet  $procop = New-VBRMongoDBProcessingOptions -BackupObject $rs[0] -AllowBackupFromPrimary $false -AutoSelectBackupSourceNode  $procop1 = Set-VBRMongoDBProcessingOptions -Options $procop[0] -AllowBackupFromPrimary $true |  Perform the following steps:   1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet to get the replica set. Specify the MongoDBEntityType parameter value. Save the result to the $rs variable. 2. Run the [New-VBRMongoDBProcessingOptions](new-vbrmongodbprocessingoptions.md) cmdlet.  * Specify the BackupObject parameter value with the $rs variable. * Specify the AllowBackupFromPrimary parameter with the $false variable. * Set the switch parameter AutoSelectBackupSourceNode. * Save the result to the $procop variable.  1. Run the Set-VBRMongoDBProcessingOptions cmdlet. Specify the Options parameter value with the $procop variable. Specify the AllowBackupFromPrimary parameter with the $true variable. Save the result to the $procop1 variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Change Preferred Node In Existing Processing Options

|  |  |
| --- | --- |
| This example shows how to change the preferred node in existing replica set processing options.  |  | | --- | | $rs = Get-VBRDiscoveredApplication -MongoDBEntityType ReplicaSet  $node = Get-VBRDiscoveredApplication -MongoDBEntityType ReplicaSetNode  $procop = New-VBRMongoDBProcessingOptions -BackupObject $rs[0] -AllowBackupFromPrimary $true -BackupSourceNode $node[0] -AllowBackupSourceNodeFailover $true  $procop1 = Set-VBRMongoDBProcessingOptions -Options $procop[0] -BackupSourceNode $node[1] |  Perform the following steps:   1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet to get the replica set. Specify the MongoDBEntityType parameter value. Save the result to the $rs variable. 2. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet to get the replica set node. Specify the MongoDBEntityType parameter value. Save the result to the $node variable. 3. Run the [New-VBRMongoDBProcessingOptions](new-vbrmongodbprocessingoptions.md) cmdlet.  * Specify the BackupObject parameter value with the $rs variable. * Specify the AllowBackupFromPrimary parameter value with the $true variable. * Specify the BackupSourceNode parameter value with the $node variable. * Specify the AllowBackupSourceNodeFailover parameter value with the $true variable. * Save the result to the $procop variable.  1. Run the Set-VBRMongoDBProcessingOptions cmdlet. Specify the Options parameter value with the $procop variable. Specify the BackupSourceNode parameter value with the $node variable. Choose a different ordinal value to use a different node. Save the result to the $procop1 variable. |

Related Commands

* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)
* [New-VBRMongoDBProcessingOptions](new-vbrmongodbprocessingoptions.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
