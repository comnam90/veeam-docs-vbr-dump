---
title: "Sync-VBRSOBREntityState"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrsobrentitystate.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Sync-VBRSOBREntityState


Short Description

Synchronizes the state of backup chains on performance extents with the state of data on capacity and archive extents of a scale-out backup repositories.

Applies to Amazon S3, S3 compatible

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Synchronizes the state of backup chains on performance extents with the state of data on capacity and archive extents for the specified job.

|  |
| --- |
| Sync-VBRSOBREntityState -Job <VBRJob> -PointInTime <datetime> [-RunAsync] [-ArchiveTier]  [<CommonParameters>] |

* Synchronizes the state of backup chains on extents for the specified scale-out backup repository.

|  |
| --- |
| Sync-VBRSOBREntityState -Repository <VBRScaleOutBackupRepository> -PointInTime <datetime> [-RunAsync] [-ArchiveTier]  [<CommonParameters>] |

* Synchronizes the state of backup chains on extents for the specified backup.

|  |
| --- |
| Sync-VBRSOBREntityState -Backup <CBackup> -PointInTime <datetime> [-RunAsync] [-ArchiveTier]  [<CommonParameters>] |

* Synchronizes the state of backup chains on extents for the specified tenant backup.

|  |
| --- |
| Sync-VBRSOBREntityState -TenantBackupId <Guid> -PointInTime <DateTime> [-ArchiveTier] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet synchronizes the state of backup chains on performance extents of scale-out backup repositories with the state of data on capacity and archive extents of scale-out backup repositories for the specific period of time.

Run the [Get-VBRCapacityTierSyncInterval](get-vbrcapacitytiersyncinterval.md) cmdlet to get details on the period of time when checkpoints in the capacity tier are available for synchronization.

Run the [Get-VBRArchiveTierSyncInterval](get-vbrarchivetiersyncinterval.md) cmdlet to get details on the period of time when checkpoints in the archive tier are available for synchronization.

|  |
| --- |
| Important |
| Use this cmdlet only with object storage that support the immutability option. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a job. The cmdlet will synchronize data for a specified period in time from the capacity extent for this job. | Accepts the VBRJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet | True  Note: This parameter is required when you want to synchronize data for a specific job. | Named | False |
| Repository | Specifies a scale-out backup repository. The cmdlet will synchronize data for a specified period in time from the capacity extent for this repository. | VBRScaleOutBackupRepository | True | Named | False |
| Backup | Specifies a backup. The cmdlet will synchronize data for a specified period in time from the capacity extent for these backups. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet | True  Note: This parameter is required when you want to synchronize data for a specific backup. | Named | False |
| PointInTime | Specifies a period in time to which you want to restore data. The cmdlet will synchronize data from the capacity extent to the specified period. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | True | Named | False |
| TenantBackupId | Specifies a ID of the tenant backup. | Guid | True | Named | False |
| TenantId | Specifies s tenant ID. | Guid | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| ArchiveTier | Defines that the cmdlet will synchronize the state of backup chains on performance extents with the state of backup chains located in the archive tier.  If you do not provide this parameter, the cmdlet will synchronizes the state of backup chains on performance extents with the state of backup chains on the capacity extent.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Synchronizing Data for Specific Job

|  |  |
| --- | --- |
| This example shows how to synchronize data that is stored in the capacity extent for the BackupJob05 job.  |  | | --- | | $job = Get-VBRJob -Name "BackupJob05"  Sync-VBRSOBREntityState -Job $job -PointInTime "2/20/2020 1:54:26 PM"    CreationTime : 2/20/2020 6:26:59 AM  EndTime      : 2/20/2020 6:28:24 AM  JobId        : 876cddc2-2879-484e-9680-7b5b2261fa30  Result       : Success  State        : Stopped  Id           : ae8fccee-78e5-4e73-a98d-0069fd61032f |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Sync-VBRSOBREntityState cmdlet. Set the $job variable as the Job parameter value. Specify the PointInTime parameter value.   The cmdlet output will contain the following details on the time period for the checkpoints: CreationTime, EndTime, JobId, Result, State and Id. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Synchronizing Data for Scale-Out Backup Repository

|  |  |
| --- | --- |
| This example shows how to synchronize data that is stored in the capacity extent for the specified scale-out backup repository.  |  | | --- | | $repository = Get-VBRBackupRepository -ScaleOut  Get-VBRCapacityTierSyncInterval -Repository $repository  StartDateUtc                                                EndDateUtc  ------------                                                ----------  2/20/2020 1:54:26 PM                                        2/20/2020 1:54:26 PM  Sync-VBRSOBREntityState -Repository $repository -PointInTime "2/20/2020 1:54:26 PM"    CreationTime : 2/20/2020 6:26:59 AM  EndTime      : 2/20/2020 6:28:24 AM  JobId        : 23e57bae-a759-42a2-a47e-06219ac410df  Result       : Success  State        : Stopped  Id           : 10957ec5-adc9-418c-a708-2f24ba11d40e |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter value. Save the result to the $repository variable. 2. Run the [Get-VBRCapacityTierSyncInterval](get-vbrcapacitytiersyncinterval.md) cmdlet. Set the $repository variable as the Repository parameter value. 3. Run the Sync-VBRSOBREntityState cmdlet. Set the $repository variable as the Repository parameter value. Specify the PointInTime parameter value.   The cmdlet output will contain the following details on the time period for the checkpoints: CreationTime, EndTime, JobId, Result, State and Id. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Synchronizing Data for Specific Backup

|  |  |
| --- | --- |
| This example shows how to synchronize data that is stored on extents for the specified backup.  |  | | --- | | $backup = Get-VBRBackup -Name "BackupJob05"  $date = Get-Date -Year 2020 -Month 2 -Day 2 -Hour 0 -Minute 0 -Second 0  Sync-VBRSOBREntityState -Backup $backup -PointInTime $date    CreationTime : 2/20/2020 6:26:59 AM  EndTime      : 2/20/2020 6:28:24 AM  JobId        : a1116d74-6d0e-4449-813e-08d094d355c1  Result       : Success  State        : Stopped  Id           : 3cb43bcc-86fc-48a2-b08b-c79d4bfb7183 |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $date variable. 3. Run the Sync-VBRSOBREntityState cmdlet. Set the $backup variable as the Backup parameter value. Set the $date variable as the PointInTime parameter value.   The cmdlet output will contain the following details on the time period for the checkpoints: CreationTime, EndTime, JobId, Result, State and Id. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRCapacityTierSyncInterval](get-vbrcapacitytiersyncinterval.md)
* [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)


