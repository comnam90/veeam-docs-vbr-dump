---
title: "Start-VBRViInstantRecoveryDiskMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrviinstantrecoverydiskmigration.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Start-VBRViInstantRecoveryDiskMigration


Short Description

Starts publish VM virtual disks to the production environment.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRViInstantRecoveryDiskMigration -InstantRecovery <InstantRecovery> [-Datastore <CViDatastoreItem>] [-DiskMigrationMappingRule <VBRViDiskMigrationRule[]>] [-StoragePolicy <VBRViStoragePolicy>] [-SourceProxy <CViProxy[]>] [-TargetProxy <CViProxy[]>] [-UseDataTransportEngine] [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet publish VM virtual disks to the production environment. To publish the disks, it uses the Quick Migration mechanism.

|  |
| --- |
| Important |
| You can run this cmdlet only after you have performed [Instant VM Disk Recovery](instant_vm_disk_recovery.md). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies an Instant VM Disc Recovery session. The cmdlet will start quick migration of VM virtual discs that are recovered during this session. | Accepts the InstantRecovery object. To create this object, run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. | True | 0 | True (ByValue, |
| Datastore | Specifies a datastore. The cmdlet will publish VM virtual disks to this datastore. | Accepts the following types of objects:   * The CViDatastoreItem object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. * The CViDatastoreCluster object. To create this object, run the [Find-VBRViDatastoreCluster](find-vbrvidatastorecluster.md) cmdlet. | False | Named | False |
| DiskMigrationMappingRule | Specifies an array of mapping settings of VM virual disks. The cmdlet will publish the recovered VM virual disks to the datastores that you define in these mapping settings.  Provide this parameter to define mapping settings for multiple VM virtual disks. | Accepts the VBRViDiskMigrationRule[] object. To create this object, run the [New-VBRViDiskMigrationMappingRule](new-vbrvidiskmigrationmappingrule.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the VMware storage policy profile that must be applied to the restored virtual disks. | Accepts the VBRViStoragePolicy object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| SourceProxy | Specifies an array of the source backup proxies that you want to use as source backup proxies. | Accepts the CViProxy[] object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| TargetProxy | Specifies an array of the target backup proxies that you want to use as target backup proxies. | Accepts the CViProxy[] object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| UseDataTransportEngine | Defines that the cmdet will enable the data transport engine, | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform VM restore even if the geographic location of the repository where VM backups reside and the target host location does not match. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupSession object that contains settings of the publish operation VM virtual disks to the production environment.

Examples

Publishing VM Virtual Disks to Production Environment

This example shows how to publish VM virtual disks to the production environment. The cmdlet will publish the disks to the datastore as it is defines in the mapping settings of the VM virtual disks.

|  |
| --- |
| $sesson = Get-VBRInstantRecovery  $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disks = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  $mapping = New-VBRViDiskMigrationMappingRule -TargetVirtualDevice $disks  Start-VBRViInstantRecoveryDiskMigration -InstantRecovery $sesson -DiskMigrationMappingRule $mapping -Force -RunAsync |

Perform the following steps:

1. Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet.  Save the result to the $sesson variable.
2. Get the mapping settings of VM virtual disks:

* Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
* Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.
* Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $disks variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore session in the array).

* Run the [New-VBRViVirtualDeviceMappingRule](new-vbrvivirtualdevicemappingrule.md) cmdlet. Set the $disks variable as the TargetVirtualDevice parameter value. Save the result to the $mapping variable.

1. Run the Start-VBRViInstantRecoveryDiskMigration cmdlet. Specify the following settings:

* Set the $sesson variable as the InstantRecovery parameter value.
* Set the $mapping variable as the DiskMigrationMappingRule parameter value.
* Provide the Force parameter.
* Provide the RunAsync parameter.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md)
* [New-VBRViVirtualDeviceMappingRule](new-vbrvivirtualdevicemappingrule.md)


