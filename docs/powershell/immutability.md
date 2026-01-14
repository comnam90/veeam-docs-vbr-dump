---
title: "Immutability"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/immutability.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Immutability

In this article

Immutability

Immutability is a solution that prevents data deletion from the capacity or archive extent. To prohibit data deletion, Veeam Backup & Replication makes it immutable by applying the [Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) technology provided by Amazon and some S3-Compatible providers. For more information on the Immutability solution, see the [Immutability](https://helpcenter.veeam.com/docs/vbr/userguide/immutability_object_storage_repositories.html?ver=13) section in the User Guide.

The immutability feature can help in the following cases:

* Data on the performance tier and the capacity tier are corrupted.
* Retention policy is set to keep only one restore point.
* Due to the hacker attack retention policy has been modified to a shorter period of time. For example, instead of keeping data for 5 days on the capacity extent, the retention is set to keep it only 1 day.

The Immutability feature allows you to restore data from the capacity tier or archive tier in these or other possible cases when necessary data are not available. When the immutability mode is enabled, Veeam Backup & Replication utilizes checkpoints to keep the necessary data either in the capacity tier or in the archive tier.

Checkpoints

A checkpoint is a storage unit that contains a current state of an entire backup chain for a specific period of time. When Veeam Backup & Replication offloads data from the capacity tier, the current state of backup chains that are located in the capacity tier or in the archive tier, is written to the checkpoints. Veeam PowerShell cmdlets from this section will use these checkpoints to sync data to the state before it was corrupted and therefore restore necessary data. In most cases, the capacity tier keeps only one checkpoint when the immutability mode is disabled. Therefore the previous states of the backup chains are overwritten. If you use the immutability feature, the capacity extent will keep several checkpoints that have been created during the offload session. The retention period of checkpoints is defined in the immutability period settings for the object storage that is added as the capacity tier. When you synchronize the state of data with the Veeam PowerShell, you might want to get details on the time period when checkpoints in object storage are available for synchronization.

How to Synchronize Data with Veam PowerShell

To synchronize the state of data using Veeam PowerShell cmdlets, you must perform the following steps:

1. [Optional] Before you start to synchronize the data to the necessary state, you can get details on the time period when checkpoints on capacity tier are available for synchronization. To get this information run the [Get-VBRCapacityTierSyncInterval](get-vbrcapacitytiersyncinterval.md) cmdlet.

|  |
| --- |
| $repository = Get-VBRBackupRepository -ScaleOut  Get-VBRCapacityTierSyncInterval -Repository $repository  StartDateUtc                                                EndDateUtc  ------------                                                ----------  2/20/2020 1:54:26 PM                                        2/20/2020 1:54:26 PM |

1. Once you get information on the necessary checkpoints, run the [Sync-VBRSOBREntityState](sync-vbrsobrentitystate.md) cmdlet. First, it synchronizes the state of data on the capacity tier from the necessary checkpoint. After that, it removes all data from the performance tier and starts to synchronize the data to the necessary state.

|  |
| --- |
| $repository = Get-VBRBackupRepository -ScaleOut  Get-VBRCapacityTierSyncInterval -Repository $repository  StartDateUtc                                                EndDateUtc  ------------                                                ----------  2/20/2020 1:54:26 PM                                        2/20/2020 1:54:26 PM  Sync-VBRSOBREntityState -Repository $repository -PointInTime "2/20/2020 1:54:26 PM"    CreationTime : 2/20/2020 6:26:59 AM  EndTime      : 2/20/2020 6:28:24 AM  JobId        : 23e57bae-a759-42a2-a47e-06219ac410df  Result       : Success  State        : Stopped  Id           : 10957ec5-adc9-418c-a708-2f24ba11d40e |

When you run the [Sync-VBRSOBREntityState](sync-vbrsobrentitystate.md) cmdlet, it performs the following actions:

1. Removes backup files that are stored on the performance tier.
2. Rebuilds indexes on the performance tier if it is necessary.
3. Downloads metadata of backup files that are stored on the capacity tier to the performance tier for the specified period of time. The backups are not downloaded to the performance tier and are stored on the capacity tier.

In This Section:

* [Get-VBRArchiveTierSyncInterval](get-vbrarchivetiersyncinterval.md)
* [Get-VBRCapacityTierSyncInterval](get-vbrcapacitytiersyncinterval.md)
* [Sync-VBRSOBREntityState](sync-vbrsobrentitystate.md)

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
