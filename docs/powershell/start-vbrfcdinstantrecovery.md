---
title: "Start-VBRFCDInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrfcdinstantrecovery.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Start-VBRFCDInstantRecovery


Short Description

Starts the FCD instant recovery session.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRFCDInstantRecovery -RestorePoint <COib> -TargetCluster <CViClusterItem> [-MappingOptions <VBRFCDInstantRecoveryMappingOptions>] [-CacheDatastore <VBRViDatastore>] [-StoragePolicy <VBRViStoragePolicy>] [-RunAsync] [-Reason <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet starts the FCD instant recovery session.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point for the VM whose virtual disks you want to restore as FCDs. | Accepts the COib object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| TargetCluster | Specifies a cluster to which Veeam Backup & Replication will register FCDs. | Accepts the CViClusterItem object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | 1 | False |
| MappingOptions | Specifies mapping settings of virtual disks that you want to restore as FCDs.  By default, Veeam Backup & Replication assigns the name of the backed-up disk to all types of virtual disks.  Note: If you do not provide this parameter, Veeam Backup & Replication will add all backed-up disks to the FCD instant recovery session. | Accepts the VBRFCDInstantRecoveryMappingOptions object. To create this object, run the [New-VBRFCDInstantRecoveryMappingOptions](new-vbrfcdinstantrecoverymappingoptions.md) cmdlet. | False | Named | False |
| CacheDatastore | Specifies a datastore to keep redo logs for the restored FCDs. | Accepts the VBRViDatastore object. To create this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies a VM storage policy. Veeam Backup & Replication will apply this storage policy for FCDs and for a datastore that keeps redo logs for the restored FCDs.  Note: The encrypted VM storage policy is not applied for FCD disks. However, you can apply this policy for a datastore that keeps redo logs for the restored FCDs. | Accepts the VBRViStoragePolicy object. To create this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Reason | Specifies a reason for performing restore of FCDs. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFCDInstantRecoverySession object that contains settings of FCD instant recovery session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting FCD Instant Recovery Session for all Disks

|  |  |
| --- | --- |
| This example shows how to start FCD instant recovery session for all backed-up disks avaiilable in the Databaseo5 backup. The cmdlet will publish disks to the Workload-C cluster.  |  | | --- | | $backup = Get-VBRBackup -Name "Database05"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $targetCluster = Find-VBRViEntity -Name "Workload-C" -HostsAndClusters  $publishingSession = Start-VBRFCDInstantRecovery -RestorePoint $restorepoint[2] -TargetCluster $targetCluster |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.  1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter. Save the result to the $restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the third restore point will be used.   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Provide the HostsAndClusters parameter. Save the result to the $targetCluster variable.  1. Run the Start-VBRFCDInstantRecovery cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $targetCluster variable as the TargetCluster parameter value. Save the result to the $publishingSession variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting FCD Instant Recovery Session for Specified Disks

|  |  |
| --- | --- |
| This example shows how to start FCD instant recovery session for the Disk1 disk with the following settings:   * The cmdlet will set the RestoredDisk1 to the virtual disk that that is mounted to the datastore. * The cmdlet will set the FCD-Disk1 to the FCD that is registered on the Workload-C cluster.   |  | | --- | | $backup = Get-VBRBackup -Name "Database backup"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $targetCluster = Find-VBRViEntity -Name "Workload-C" -HostsAndClusters  $diskMapping = New-VBRFCDInstantRecoveryMappingOptions -NameInBackup "Disk1" -MountedDiskName "RestoredDisk1" -RegisteredFCDName "FCD-Disk1"  $publishingSession = Start-VBRFCDInstantRecovery -RestorePoint $restorepoint[2] -TargetCluster $targetCluster -MappingOptions $diskMapping |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter. Save the result to the $restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the third restore point is used.   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Provide the HostsAndClusters parameter. Save the result to the $targetCluster variable.  1. Run the [New-VBRFCDInstantRecoveryMappingOptions](new-vbrfcdinstantrecoverymappingoptions.md) cmdlet. Specify the NameInBackup, MountedDiskName and RegisteredFCDName parameter values. Save the result to the $diskMapping variable.  1. Run the Start-VBRFCDInstantRecovery cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $targetCluster variable as the TargetCluster parameter value. Set the $diskMapping variable as the MappingOptions parameter value. Save the result to the $publishingSession variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting FCD Instant Recovery Session with Redo Logs Redirection

|  |  |
| --- | --- |
| This example shows how to start FCD instant recovery session for the Disk1 disk. The cmdlet will write redo logs to the VeeamDatastore datastore. The datastore is assigned the Virtual SAN Default Storage Policy.  |  | | --- | | $server = Get-VBRServer -Name "tech.local"  $datastore = Find-VBRViDatastore -Server $server -Name "VeeamDatastore"  $storagePolicy = Find-VBRViStoragePolicy -Server $server -Datastore $datastore -Name "Virtual SAN Default"  $backup = Get-VBRBackup -Name "Database backup"  $restorepoint = Get-VBRRestorePoint $backup  $targetCluster = Find-VBRViEntity -Name "Workload-Cluster" -HostsAndClusters  $publishingSession = Start-VBRFCDInstantRecovery -RestorePoint $restorepoint[2] -TargetCluster $targetCluster -CacheDatastore $datastore -StoragePolicy $storagePolicy |  Perform the following steps:   1. Get the datastore:  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $datastore variable. 3. Run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. Specify the Server, Datastore and Name parameter values. Save the result to the $storagePolicy variable.  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.  1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Backup parameter. Save the result to the $restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the third restore point will be used.   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Provide the HostsAndClusters parameter. Save the result to the $targetCluster variable.  1. Run the Start-VBRFCDInstantRecovery cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $targetCluster variable as the TargetCluster parameter value. * Set the $datastore variable as the CacheDatastore parameter value. * Set the $storagePolicy variable as the StoragePolicy parameter value. * Save the result to the $publishingSession variable. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md)


