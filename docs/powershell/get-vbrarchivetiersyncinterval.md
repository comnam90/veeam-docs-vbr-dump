---
title: "Get-VBRArchiveTierSyncInterval"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrarchivetiersyncinterval.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Get-VBRArchiveTierSyncInterval

In this article

Short Description

Returns a time period of checkpoints in the archive tier that are available for synchronization.

Applies to Amazon S3 Glacier

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a time period of checkpoints that are available for synchronization.

|  |
| --- |
| Get-VBRArchiveTierSyncInterval -Repository <VBRScaleOutBackupRepository>  [<CommonParameters>] |

* Get a time period of checkpoints that are available for synchronization for the specified job.

|  |
| --- |
| Get-VBRArchiveTierSyncInterval -Repository <VBRScaleOutBackupRepository> -Job <VBRJob>  [<CommonParameters>] |

* Get a time period of checkpoints that are available for synchronization for the specified backup.

|  |
| --- |
| Get-VBRArchiveTierSyncInterval -Repository <VBRScaleOutBackupRepository> -Backup <CBackup>  [<CommonParameters>] |

* Get a time period of checkpoints that are available for synchronization for the specified cloud tenant backup.

|  |
| --- |
| Get-VBRArchiveTierSyncInterval -Repository <VBRScaleOutBackupRepository> -TenantBackupId <Guid>  [<CommonParameters>] |

* Get a time period of checkpoints that are available for synchronization for the specified cloud tenant.

|  |
| --- |
| Get-VBRArchiveTierSyncInterval -Repository <VBRScaleOutBackupRepository> -TenantId <Guid>  [<CommonParameters>] |

Detailed Description

This cmdlet returns a time period of checkpoints in the archive tier that are available for synchronization. You may want to run this cmdlet before you synchronize the state of backup chains with the state of backup chains on the archive tier for the specific period of time. When you synchronize the state of backup chains with state of backup chains on the archive tier, the state of backup chains on the capacity tier does not change.

Run the [Sync-VBRSOBREntityState](sync-vbrsobrentitystate.md) cmdlet to synchronize the state of the backup chains.

|  |
| --- |
| Important |
| Use this cmdlet only with archive storage that support the immutability option. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies a scale-out backup repository. The cmdlet will return a time period that contains checkpoints that were moved from this scale-out backup repository but are still available on the archive tier. | Accepts the [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet and provide the ScaleOut parameter. | True | Named | True (ByValue) |
| Job | Specifies a job. The cmdlet will return a time period that contains checkpoints on the archive tier for this job. | Accepts the VBRJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | False |
| Backup | Specifies a backup. The cmdlet will return a time period that contains checkpoints on the archive tier for this backup. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | False |
| TenantBackupId | Specifies an ID of the cloud tenant backup. The cmdlet will return a time period that contains checkpoints on the archive tier for this backup. | Guid | True | Named | False |
| TenantId | Specifies an ID of the cloud tenant. The cmdlet will return a time period that contains checkpoints on the archive tier created by this tenant. | Guid | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRArchiveTierSyncInterval object contains details on a time period of checkpoints in archive tier that are available for synchronization.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Time Period for all Checkpoints Available on Archive Tier

|  |  |
| --- | --- |
| This example shows how to get a time period with contains checkpoints on archive tier that are available for synchronization.  |  | | --- | | $repository = Get-VBRBackupRepository -ScaleOut  Get-VBRArchiveTierSyncInterval -Repository $repository    StartDateUtc                                                EndDateUtc  ------------                                                ----------  2/20/2020 1:54:26 PM                                        2/20/2020 1:54:26 PM |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter value. Save the result to the $repository variable. 2. Run the Get-VBRArchiveTierSyncInterval cmdlet. Set the $repository variable as the Repository parameter value.   The cmdlet output will contain the following details on the time period for the checkpoints: StartDateUtc and EndDateUtc. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Time Period of Checkpoints for Specific Job

|  |  |
| --- | --- |
| This example shows how to get a time period that contains checkpoints on archive tier that you can synchronize for the Backup05 job.  |  | | --- | | $repository = Get-VBRBackupRepository -ScaleOut  $job = Get-VBRJob -Name "Backup05"  Get-VBRArchiveTierSyncInterval -Repository $repository -Job $job    StartDateUtc                                                EndDateUtc  ------------                                                ----------  2/20/2020 1:54:26 PM                                        2/20/2020 1:54:26 PM |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter value. Save the result to the $repository variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 3. Run the Get-VBRArchiveTierSyncInterval cmdlet. Set the $repository variable as the Repository parameter value. Set the $job variable as the Job parameter value.   The cmdlet output will contain the following details on the time period for the checkpoints: StartDateUtc and EndDateUtc. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Time Period of Checkpoints for Specific Backup

|  |  |
| --- | --- |
| This example shows how to get a time period that contains details on checkpoints on archive tier that you can synchronize for the Report05 backup.  |  | | --- | | $repository = Get-VBRBackupRepository -ScaleOut  $backup = Get-VBRBackup -Name "Report05"  Get-VBRArchiveTierSyncInterval -Repository $repository -Backup $backup    StartDateUtc                                                EndDateUtc  ------------                                                ----------  2/20/2020 1:54:26 PM                                        2/20/2020 1:54:26 PM |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter value. Save the result to the $repository variable. 2. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 3. Run the Get-VBRArchiveTierSyncInterval cmdlet. Set the $repository variable as the Repository parameter value. Set the $backup variable as the Backup parameter value.   The cmdlet output will contain the following details on the time period for the checkpoints: StartDateUtc and EndDateUtc. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRBackup](get-vbrbackup.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
