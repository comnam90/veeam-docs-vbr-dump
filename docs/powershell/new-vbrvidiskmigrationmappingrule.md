---
title: "New-VBRViDiskMigrationMappingRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvidiskmigrationmappingrule.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# New-VBRViDiskMigrationMappingRule


Short Description

Defines mapping settings of recovered VM virtual disks and target datastores.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRViDiskMigrationMappingRule -TargetVirtualDevice <VBRViVirtualDevice> [-DiskType {AsSource | Thin | LazyZeroed | EagerZeroed}] [-Datastore <VBRViDatastoreBase>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines mapping settings of recovered VM virtual disks and target datastores. You can run this cmdlet to specify a particular target datastore for every disk that you want to publish.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| TargetVirtualDevice | Specifies recovered VM virtual disks. The cmdlet will map these disks to the datastore. | Accepts the VBRViVirtualDevice object. To create this object, run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. | True | Named | False |
| DiskType | Specifies the virtual disk type settings. The cmdlet will set the virtual disks types to the specified type during the restore. You can specify one of the following disk types:   * AsSource * Thin * LazyZeroed * EagerZeroed   Default: AsSource | VBRViDiskType | False | Named | False |
| Datastore | Specifies a datastore or a datastore cluster. The cmdlet will map recovered VM virtual disks to the specified datastore or the datastore cluster.  Note: If you do not specify this parameter, the cmdlet will will map recovered VM virtual disks to the default datastore. | Accepts the following types of objects:   * The CViDatastoreItem object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. * The CViDatastoreCluster object. To create this object, run the [Find-VBRViDatastoreCluster](find-vbrvidatastorecluster.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViDiskMigrationMappingRule object that defines mapping settings of recovered VM virtual disks with target datastores. .

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Mapping Recovered Virtual Disks to Default Datastore

|  |  |
| --- | --- |
| This example shows how to map the recovered virtual disks to the default datastore. The cmdlet will map virtual disks of the VM that is backed up by the Winsrv4515 job.  |  | | --- | | $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disks = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  New-VBRViDiskMigrationMappingRule -TargetVirtualDevice $disks |  Perform the following steps:   1. Get the backed-up VM virtual disks:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $disks variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore session in the array).   1. Run the New-VBRViDiskMigrationMappingRule cmdlet. Set the $disks variable as the TargetVirtualDevice parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Mapping Recovered Virtual Disks to Specific Datastore

|  |  |
| --- | --- |
| This example shows how to map the recovered virtual disks to the LocalStore\_0 datastore. This datastore is connected to the WinSrv2073 server. The cmdlet will map virtual disks of the VM that is backed up by the Winsrv4515 job.  |  | | --- | | $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disks = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  $server = Get-VBRServer -Name "WinSrv2073"  $datastore = Find-VBRViDatastore -Server $server -Name "LocalStore\_0"  New-VBRViDiskMigrationMappingRule -TargetVirtualDevice $disks -Datastore $datastore |  Perform the following steps:   1. Get the backed-up VM virtual disks:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $disks variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore session in the array).   1. Get the datastore:  * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $datastore variable.  1. Run the New-VBRViDiskMigrationMappingRule cmdlet. Set the $disks variable as the TargetVirtualDevice parameter value. Set the $datastore variable as the Datastore parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Mapping Recovered Virtual Disks to Datastore Cluster

|  |  |
| --- | --- |
| This example shows how to map the recovered virtual disks to the Cluster\_5 datastore cluster. This datastore cluster is connected to the WinSrv2077 server. The cmdlet will map virtual disks of the VM that is backed up by the Winsrv4515 job.  |  | | --- | | $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disks = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  $server = Get-VBRServer -Name "WinSrv2077"  $datastorecluster = Find-VBRViDatastoreCluster -Server $server -Name "Cluster\_5"  New-VBRViDiskMigrationMappingRule -TargetVirtualDevice $disks -Datastore $datastorecluster |  Perform the following steps:   1. Get the backed-up VM virtual disks:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $disks variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore session in the array).   1. Get the datastore:  * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the [Find-VBRViDatastoreCluster](find-vbrvidatastorecluster.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $datastorecluster variable.  1. Run the New-VBRViDiskMigrationMappingRule cmdlet. Set the $disks variable as the TargetVirtualDevice parameter value. Set the $datastorecluster variable as the Datastore parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)


