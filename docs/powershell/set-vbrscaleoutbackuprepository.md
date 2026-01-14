---
title: "Set-VBRScaleOutBackupRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrscaleoutbackuprepository.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRScaleOutBackupRepository

In this article

Short Description

Modifies scale-out backup repositories.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRScaleOutBackupRepository -Repository <VBRScaleOutBackupRepository> [-Name <String>] [-Description <String>] [-PolicyType <VBRScaleOutBackupRepositoryPolicyType>] [-Extent <CBackupRepository[]>] [-UsePerVMBackupFiles] [-PerformFullWhenExtentOffline] [-EnableCapacityTier] [-ForceStrictPlacementPolicy] [-OperationalRestorePeriod <Int32>] [-EnableOverridePolicy] [-OverrideSpaceThreshold <Int32>] [-OffloadWindowOptions <VBRBackupWindowOptions>] [-ObjectStorageRepository <VBRObjectStorageRepository[]>] [-EnableCapacityTierEncryption] [-CapacityTierEncryptionKey <VBREncryptionKey>] [-CapacityTierKMSServer <VBRKMSServer>] [-PassThru] [-Force] [-EnableCapacityTierMovePolicy] [-EnableCapacityTierCopyPolicy] [-CapacityTierHealthCheckOptions <VBRHealthCheckOptions>] [-EnableArchiveTier] [-ArchiveObjectStorageRepository <VBRArchiveObjectStorageRepository>] [-EnableArchiveTierEncryption] [-ArchiveTierEncryptionKey <VBREncryptionKey>] [-ArchiveTierKMSServer <VBRKMSServer>] [-ArchivePeriod <Int32>] [-EnableCostOptimizedArchive] [-EnableArchiveFullBackupMode] [-EnablePluginBackupOffload] [-EnableCopyAllPluginBackups] [-EnableCopyAllMachineBackups]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of scale-out backup repositories.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies a scale-out repository that you want to modify. | Accepts the VBRScaleOutBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet and provide the ScaleOut parameter. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies a name of a scale-out repository. | String | False | Named | True (ByProperty Name) |
| Description | Specifies a description of a scale-out repository. | String | False | Named | True (ByProperty Name) |
| PolicyType | Specifies the policy for a scale-out repository:   * DataLocality - use this policy to store backup files that belong to the same backup chain together. * Performance - to store full and incremental backup files to different extents of the scale-out backup repository. | VBRScaleOutBackupRepositoryPolicyType | True | Named | True (ByProperty Name) |
| Extent | Specifies an array of backup repositories. The cmdlet will add these repositories as extents to a scale-out repository.  IMPORTANT! The cmdlet will replace the extents currently added to the scale-out backup repository with this array.   * To add an extent, specify all currently added extents plus the new one. * To remove an extent, specify the currently existing extents except for the extent that you want to remove. | Accepts the following object:   * GUID * String (repository name) * CBackupRepository[]. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByProperty Name) |
| UsePerVMBackupFiles | If set to True, the repository will store each VM in the job as a separate backup file.  If set to False, each restore point will contain all VMs in the job.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| PerformFullWhenExtentOffline | If set to True, the job will create an active full backup if the extent with the previous backup file is offline.  If set to False, the job will fail to create an increment.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| EnableCapacityTier | Enables the capacity tier option. Veeam Backup & Replication will move backup files to the object storage.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| OperationalRestorePeriod | For retention policy.  Specifies the number of days to keep backup files on the local repository. When the number of days is passed, Veeam Backup & Replication will move backup files to an object storage.  Note: If you select zero days, Veeam Backup & Replication will move all backup files from the local repository to the object storage immediately. | Int | False | Named | True (ByProperty Name) |
| EnableOverridePolicy | Enables the option to move backup files from the local repository to an object storage when the capacity reaches limits. If set, this option overrides the retention policy. Veeam Backup & Replication will move backup files to an object storage even if the retention policy value has not reached limits.  Default: False. | SwitchParameter | False | Named | True (ByProperty Name) |
| OverrideSpaceThreshold | For the override option.  Specifies the capacity value in percent for the override option. Once the value reaches the limit, Veeam Backup & Replication will move the data from the local repository to an object storage. | Int32 | False | Named | True (ByProperty Name) |
| OffloadWindowOptions | Specifies the time interval, when Veeam Backup & Replication is allowed will move the backup files to an object storage. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | True (ByProperty Name) |
| ObjectStorageRepository | Specifies an object storage. Veeam Backup & Replication will move the backup files to this object storage. | Accepts the VBRObjectStorageRepository object. To create this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | False | Named | True (ByProperty Name) |
| Force | Defines that the cmdlet will create the scale-out backup repository without showing up the notifications in the PowerShell console. | SwitchParameter | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console.  Default: False. | SwitchParameter | False | Named | False |
| EnableCapacityTierMovePolicy | Defines that the cmdlet will move inactive backup chains to object storage. | SwitchParameter | False | Named | False |
| EnableCapacityTierCopyPolicy | Defines that the cmdlet will copy new backup files to object storage as soon as they are created.  Default: False. | SwitchParameter | False | Named | False |
| EnableArchiveTier | Enables the archive tier option. Veeam Backup & Replication will move backup files to an archive storage.  Default: False. | SwitchParameter | False | Named | True (ByPropertyName) |
| ArchiveObjectStorageRepository | Specifies an archive storage. Veeam Backup & Replication will move the backup files to this archive storage. | Accepts the VBRArchiveObjectStorageRepository object. To create this object, run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. | False | Named | True (ByPropertyName) |
| EnableCapacityTierEncryption | Enables encryption for the capacity tier. Veeam Backup & Replication will encrypt backups offloaded to the capacity tier. | SwitchParameter | False | Named | False |
| CapacityTierEncryptionKey | Specifies a password that Veeam Backup & Replication will use to encrypt backups on the capacity tier.  Note: If you add the capacity tier that has been encrypted, you must specify the password that you used to encrypt data on this tier. You can change a password after you configure the scale-out backup repository. | Accepts the VBREncryptionKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| CapacityTierKMSServer | Specifies the KMS server you want to use to encrypt backups. | Accepts the VBRKMSServer object.  To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| EnableArchiveTierEncryption | Enables encryption for the archive tier. The cmdlet will encrypt backups moved to the archive tier. | SwitchParameter | False | Named | False |
| ArchiveTierEncryptionKey | Specifies a password that Veeam Backup & Replication will use to encrypt backups on the archive tier.  Note: If you add the archive tier that has been encrypted, you must specify the password that you used to encrypt data on this tier. You can change a password after you configure the scale-out backup repository. | Accepts the VBREncryptionKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| ArchiveTierKMSServer | Specifies the KMS server you want to use to encrypt backups. | Accepts the VBRKMSServer object.  To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| EnableCopyAllMachineBackups | For backup files created with Veeam Agent backup jobs and Veeam Backup jobs for VMs.  Enables copying of all backup files from the performance extents to the capacity extent. If you do not provide this parameter, the cmdlet will copy only the latest backup files.  Note: To activate the copy policy, you must provide the EnableCapacityTierCopyPolicy parameter.  Default: False. | SwitchParameter | False | Named | False |
| CapacityTierHealthCheckOptions | Specifies the health check schedule options. | Accepts the VBRHealthCheckOptions object. To create this object, run the [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md) cmdlet. | False | Named | False |
| ForceStrictPlacementPolicy | Defines that the cmdlet will enable strict placement policy. If you provide this parameter, Veeam Backup & Replication will not create a backup if it violates the backup placement policy and may result in that a backup job will fail.  Default: False. | SwitchParameter | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding New Extent to Scale-Out Repository

|  |  |
| --- | --- |
| This example shows how to add a new extent to the scale-out repository.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "Veeam Scale-Out Repository" -ScaleOut  Set-VBRScaleOutBackupRepository –Repository $repository –Extent “Backup Repository 1”, “Backup Repository 2”, “Backup Repository 3” |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get the repository. Specify the Name parameter value. Provide the ScaleOut parameter. Save it to the $repository variable. 2. Run the Set-VBRScaleOutBackupRepository cmdlet. Set the $repository variable as the Repository parameter value. Specify the Extent parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Scale-Out Repository Policy

|  |  |
| --- | --- |
| This example shows how to modify the scale-out repository policy.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "Veeam Scale-Out Repository" -ScaleOut  Set-VBRScaleOutBackupRepository –Repository $repository –PolicyType DataLocality -Extent “Backup Repository 1”, “Backup Repository 2”, “Backup Repository 3” |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get the repository. Specify the Name parameter value. Provide the ScaleOut parameter. Save it to the $repository variable. 2. Run the Set-VBRScaleOutBackupRepository cmdlet.  Set the $repository variable as the Repository parameter value. Set the DataLocality option for the PolicyType parameter. Specify the Extent parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
