---
title: "Add-VBRScaleOutBackupRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrscaleoutbackuprepository.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-VBRScaleOutBackupRepository

In this article

Short Description

Adds scale-out backup repositories to the backup infrastructure.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRScaleOutBackupRepository -PolicyType <VBRScaleOutBackupRepositoryPolicyType> -Extent <CBackupRepository[]> [-Name <String>] [-Description <String>] [-UsePerVMBackupFiles] [-PerformFullWhenExtentOffline] [-EnableCapacityTier] [-ForceStrictPlacementPolicy] [-OperationalRestorePeriod <Int32>] [-EnableOverridePolicy] [-OverrideSpaceThreshold <Int32>] [-OffloadWindowOptions <VBRBackupWindowOptions>] [-ObjectStorageRepository <VBRObjectStorageRepository[]>] [-EnableCapacityTierEncryption] [-CapacityTierEncryptionKey <VBREncryptionKey>] [-CapacityTierKMSServer <VBRKMSServer>][-EnableCapacityTierMovePolicy] [-EnableCapacityTierCopyPolicy] [-CapacityTierHealthCheckOptions <VBRHealthCheckOptions>] [-EnableArchiveTier] [-ArchiveObjectStorageRepository <VBRArchiveObjectStorageRepository>] [-EnableArchiveTierEncryption] [-ArchiveTierEncryptionKey <VBREncryptionKey>] [-ArchiveTierKMSServer <VBRKMSServer>] [-ArchivePeriod <Int32>] [-EnableCostOptimizedArchive] [-EnableArchiveFullBackupMode] [-EnablePluginBackupOffload] [-EnableCopyAllPluginBackups] [-EnableCopyAllMachineBackups] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet creates scale-out backup repositories. You can create the scale-out backup repositories with the following options:

* The [performance tier](https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository_sobr_extents.html?ver=13) option. To implement this option, you must add local backup repositories or object storage repositories as performance extents to the scale-out backup repository.

* Performance tier and [capacity tier](https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier.html?ver=13) options. To implement this option, you must add local backup repositories and object storage repositories to the scale-out backup repository.
* Performance tier, capacity tier and archive tier options. To implement this option, you must add local backup repositories, object storage repositories and archive object storage repositories to the scale-out backup repository.

Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get backup repositories.

Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet to get object storage repositories.

By default, Veeam Backup & Replication only moves backup files that form inactive backup chains. For more information about backup chains, see the [Backup Chain Legitimacy](https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier_inactive_backup_chain.html?ver=13) section of User Guide for VMware vSphere.

If you want to move a backup file manually, run the [Start-VBROffloadBackupFile](start-vbroffloadbackupfile.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| PolicyType | Specifies the policy for the scale-out backup repository:   * DataLocality - use this policy to store backup files that belong to the same backup chain. * Performance - to store full and incremental backup files to different extents of the scale-out backup repository.   Note: For performance tier that consists of object storage repositories you must specify the DataLocality policy. | [VBRScaleOutBackupRepositoryPolicyType](enums.md#VBRScaleOutBackupRepositoryPolicyType) | True | Named | True (ByProperty Name) |
| Extent | Specifies the array of backup repositories. The cmdlet will add these repositories as performance extents to the scale-out backup repository. | Accepts the following object:   * GUID * String (repository name) * CBackupRepository[]. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Note: If you want to add an object storage repository as a performance extent, to get this object storage repository run the Get-VBRBackupRepository cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name of the scale-out backup repository. | String | False | Named | True (ByProperty Name) |
| Description | Specifies the description of the scale-out backup repository. | String | False | Named | True (ByProperty Name) |
| UsePerVMBackupFiles | If set to True, the repository will store each VM in the job as a separate backup file.  If set to False, each restore point will contain all VMs in the job.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| PerformFullWhenExtentOffline | If set to True, the job will create an active full backup if the extent with the previous backup file is offline.  If set to False, the job will fail to create an increment.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| EnableCapacityTier | Enables the capacity tier option. Veeam Backup & Replication will move backup files to an object storage.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| OperationalRestorePeriod | For retention policy.  Specifies the number of days to keep backup files on the local repository. When the number of days is passed, Veeam Backup & Replication will move backup files to an object storage.  Note: If you select zero days, Veeam Backup & Replication will move all backup files from the local repository to the object storage immediately. | Int | False | Named | True (ByProperty Name) |
| EnableOverridePolicy | Enables the option to move backup files from the local repository to an object storage when the capacity reaches limits. If set, this option overrides the retention policy. Veeam Backup & Replication will move backup files to an object storage even if the retention policy value has not reached limits.  Use the OverrideSpaceThreshold parameter to specify the capacity value.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| OverrideSpaceThreshold | For the override option.  Specifies the capacity value in percent for the override option. Once the value reaches the limit, Veeam Backup & Replication will move the data from the local repository to an object storage. | Int | False | Named | True (ByProperty Name) |
| OffloadWindowOptions | Specifies the time interval, when Veeam Backup & Replication is allowed will move the backup files to an object storage. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | True (ByProperty Name) |
| ObjectStorageRepository | Specifies an object storage. Veeam Backup & Replication will move the backup files to this object storage. | Accepts the VBRObjectStorageRepository object. To create this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet.  Note: If you want to add an object storage repository as a performance extent, to get this object storage repository run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByProperty Name) |
| Force | Defines that the cmdlet will create the scale-out backup repository without showing up warnings in the PowerShell console.  Default: False. | SwitchParameter | False | Named | False |
| EnableCapacityTierMovePolicy | Defines that the cmdlet will move inactive backup chains to object storage.  Default: False. | SwitchParameter | False | Named | False |
| EnableCapacityTierCopyPolicy | Defines that the cmdlet will copy new backup files to object storage as soon as they are created.  Default: False. | SwitchParameter | False | Named | False |
| EnableArchiveTier | Enables the archive tier option. Veeam Backup & Replication will move backup files to an archive storage.  Default: False. | SwitchParameter | False | Named | True (ByPropertyName) |
| ArchiveObjectStorageRepository | Specifies an archive storage. Veeam Backup & Replication will move the backup files to this archive storage. | Accepts the VBRArchiveObjectStorageRepository object. To create this object, run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. | False | Named | True (ByPropertyName) |
| EnableCapacityTierEncryption | Enables encryption for the capacity tier. Veeam Backup & Replication will encrypt backups offloaded to the capacity tier. | SwitchParameter | False | Named | False |
| CapacityTierEncryptionKey | Specifies a password that Veeam Backup & Replication will use to encrypt backups on the capacity tier.  Note: If you add the capacity tier that has been encrypted, you must specify the password that you used to encrypt data on this tier. You can change a password after you configure the scale-out backup repository. | Accepts the VBREncryptionKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| CapacityTierKMSServer | Specifies the KMS server you want to use to encrypt backups. | Accepts the VBRKMSServer object.  To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| EnableArchiveTierEncryption | Enables encryption for the archive tier. The cmdlet will encrypt backups moved to the archive tier. | SwitchParameter | False | Named | False |
| ArchiveTierEncryptionKey | Specifies a password that Veeam Backup & Replication will use to encrypt backups on the archive tier.  Note: If you add the archive tier that has been encrypted, you must specify the password that you used to encrypt data on this tier. You can change a password after you configure the scale-out backup repository. | Accepts the VBREncryptionKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| ArchiveTierKMSServer | Specifies the KMS server you want to use to encrypt backups. | Accepts the VBRKMSServer object.  To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| ArchivePeriod | For retention policy.  Specifies the number of days to keep backup files on the archive extent. When the number of days is passed, Veeam Backup & Replication will delete outdated backup files. | Int | False | Named | False |
| EnableCostOptimizedArchive | Enables the option to archive backup files only if the remaining retention time is above minimal storage period.  Default: False. | SwitchParameter | False | Named | False |
| EnableArchiveFullBackupMode | Enables the option to store archived backups as standalone fulls, without any dependencies on the previous backup files.  Default: False. | SwitchParameter | False | Named | False |
| EnablePluginBackupOffload | Enables offloading of the backup files created with plugin backup jobs to the capacity tier.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| EnableCopyAllPluginBackups | For backup files created with Veeam Plug-in for SAP HANA, Veeam Plug-in for Oracle RMAN.  Enables copying of all backup files from the performance extents to the capacity extent. If you do not provide this parameter, the cmdlet will not copy these backup files to the capacity extent.  Note: You must provide the EnableCapacityTierCopyPolicy parameter to activate the copy policy.  Default: False. | SwitchParameter | False | Named | False |
| EnableCopyAllMachineBackups | For backup files created with Veeam Agent backup jobs and Veeam backup jobs for VMs.  Enables copying of all backup files from the performance extents to the capacity extent. If you do not provide this parameter, the cmdlet will copy only the latest backup files.  Note: You must provide the EnableCapacityTierCopyPolicy parameter to activate the copy policy.  Default: False. | SwitchParameter | False | Named | False |
| CapacityTierHealthCheckOptions | Specifies the health check schedule options. | Accepts the VBRHealthCheckOptions object. To create this object, run the [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md) cmdlet. | False | Named | False |
| ForceStrictPlacementPolicy | Defines that the cmdlet will enable strict placement policy. If you provide this parameter, Veeam Backup & Replication will not create a backup if it violates the backup placement policy and may result in that a backup job will fail.  Default: False. | SwitchParameter | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Scale-Out Backup Repository with Performance Tier [Backup Repositories Extents]

|  |  |
| --- | --- |
| This example shows hot to create a scale-out backup repository with the following settings:   * The scale-out backup repository contains the performance tier. * The performance tier consists of local backup repositories added as performance extents. * The policy type is set to performance policy type.   |  | | --- | | $ext1 = Get-VBRBackupRepository -Name "LinExtent 1"  $ext2 = Get-VBRBackupRepository -Name "LinExtent 2"  Add-VBRScaleOutBackupRepository -Name "Veeam Performance Scale-Out Repository" –PolicyType Performance -Extent $ext1, $ext2 |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $ext1 variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $ext2 variable. 3. Run the Add-VBRScaleOutBackupRepository cmdlet Specify the Name parameter value. Set the PolicyType parameter to the Performance value. Set the $ext1 and $ext2 variables as the Extent parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Scale-Out Backup Repository with Capacity Tier

|  |  |
| --- | --- |
| This example shows how to create a scale-out backup repository with the following settings:   * The scale-out backup repository contains performance tier and capacity tier.  * The performance tier consists of local backup repositories added as performance extents. * The policy type is set to performance policy type.   |  | | --- | | $ext1 = Get-VBRBackupRepository -Name "LinExtent 1"  $objectstorage = Get-VBRObjectStorageRepository -Name "Amazon S3"  Add-VBRScaleOutBackupRepository -Name "ScaleOutRepository" -Extent $ext1 -PolicyType Performance -EnableCapacityTier -ObjectStorageRepository $objectstorage |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $ext1 variable. 2. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $objectstorage variable. 3. Run the Add-VBRScaleOutBackupRepository cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $ext1 variable as the Extent parameter value. * Set the PolicyType parameter to the Performance value. * Provide the EnableCapacityTier parameter. * Set the $objectstorage variable as the ObjectStorageRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Scale-Out Backup Repository with Performance Tier [Object Storage Extents]

|  |  |
| --- | --- |
| This command creates a scale-out backup repository with the following settings:   * The scale-out backup repository contains the performance tier. * The performance tier consists of object storage repositories added as performance extents.   |  | | --- | | $ext1 = Get-VBRBackupRepository -Name "S3Ext01"  $ext2 = Get-VBRBackupRepository -Name "S3Ext02"  Add-VBRScaleOutBackupRepository -Name SOBR03 -Extent $ext1, $ext2 -PolicyType DataLocality |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $ext1 variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $ext2 variable. 3. Run the Add-VBRScaleOutBackupRepository cmdlet. Specify the Name parameter value. Set the PolicyType parameter to the DataLocality value. Set the $ext1 and $ext2 variables as the ObjectStorageRepository parameter values. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
