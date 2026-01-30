---
title: "Updated Cmdlets"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/updated_cmdlets_12.1.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Updated Cmdlets


This section contains information on cmdlets updated in Veeam PowerShell v12.1.

Backup Infrastructure Components

Object Storage Repositories

In this version, you can use new parameter sets to perform the following actions:

* Roll back checkpoints in object storage repositories for the specified cloud tenant backup.
* Synchronize the state of backup chains on extents for the specified tenant backup.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Sync-VBRObjectStorageRepositoryEntityState](deleted.md) | New parameter set added: Sync-VBRObjectStorageRepositoryEntityState -TenantBackupId <Guid> -PointInTime <DateTime> [-RunAsync]  [<CommonParameters>] | | Sync-VBRSOBREntityState | New parameter set added: Sync-VBRSOBREntityState -TenantBackupId <Guid> -PointInTime <DateTime> [-ArchiveTier] [-RunAsync]  [<CommonParameters>] | |

Backup

In this version, the following scenarios are supported:

* You can remove backups and restore points from archive tier and capacity tier.
* When you copy backups to a repository, a local or shared folder, you can specify the type of the retention policy and the period of time to keep the copied data.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Remove-VBRBackup](remove-vbrbackup.md) | Parameter updated: The Backup parameter accepts the [VBRSOBRObjectStorageBackup](vbrsobrobjectstoragebackup.md) type. | | [Remove-VBRRestorePoint](remove-vbrrestorepoint.md) | Parameter updated: The Oib parameter accepts the [VBRSOBRObjectStorageRestorePoint](vbrsobrobjectstoragerestorepoint.md) type. | | [Copy-VBRBackup](copy-vbrbackup.md) | New parameters added: RetentionPeriodType, RetentionNumber | |

Jobs

Sessions

In this version, you can get new types of jobs sessions.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRSession](get-vbrsession.md) | Parameter update: The Type parameter includes new enums for the following types of job session:   * SureBackupLite * SureBackupLite * SureBackupLiteAdHoc * SimpleCopyExternalBackupWatcher * BestPracticeAnalyzer * MalwareDetection * SureBackupLite * SureBackupLiteAdHoc * KmsKeyRotation * ShadowAncillarySession | |

Replication

In this version, you can perform failback of the replica to a specific VM for the following scenarios:

* When you perform failback of VMware VMs to a production host.
* When you perform failback from a CDP replica to the production VM.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRViReplicaFailback](start-vbrvireplicafailback.md) | New parameter added: VmName | | [Start-VBRCDPReplicaFailback](start-vbrcdpreplicafailback.md) | New parameter added: VmName | |

SureBackup

In this version, you can exclude specific VMs from processing by the SureBackup job,

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRSureBackupVM](new-vbrsurebackupvm.md) | New parameters added: Exclude | |

Data Recovery

In this version, the following scenarios are supported:

* You can specify the backup proxy that you want to use during restore of the entire VMware VM.
* You can define whether to mount disks to the original server and use it as a helper host when you run a restore session of Linux-based or Unix-based guest OS files.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRRestoreVM](start-vbrrestorevm.md) | New parameter added: Proxy. | | [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) | New parameters added: MountToOriginalHost. | |

Agent Management

In this version, you can specify the Linux package type when you get Veeam Agent for Linux packages.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VBRProtectionGroupLinuxPackage](get-vbrprotectiongrouplinuxpackage.md) | New parameter added: Type. | |


