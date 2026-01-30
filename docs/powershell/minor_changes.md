---
title: "Minor Non-Breaking Changes"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/minor_changes.html"
last_updated: "11/25/2024"
product_version: "13.0.1.1071"
---

# Minor Non-Breaking Changes


The following minor non-breaking changes were introduced in Veeam PowerShell 12.1.

Backup Infrastructure

Logging

In this version, you can run the [Export-VBRLogs](export-vbrlogs.md) cmdlet to get logs of the cloud tenants.

|  |
| --- |
| Note |
| The cmdlet does not return logs of VMware Cloud Director and Active Directory tenant accounts. |

Backup

Job Options

In this version, the [Set-VBRJobOptions](set-vbrjoboptions.md) cmdlet is deprecated for the following types of jobs:

* Backup copy jobs. Run the [Set-VBRBackupCopyJob](set-vbrbackupcopyjob.md) cmdlet instead.
* Veeam Agent jobs and policies. Run the [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) cmdlet instead.

Managing Backups

In this version, you can run the [Remove-VBRBackup](remove-vbrbackup.md) cmdlet to remove the backups and restore points stored in archive extents and capacity extents of scale-out backup repositories. For this operation, you must provide the FromDisk parameter.

Continuous Data Protection (CDP)

In this version, when you run the [Start-VBRCDPReplicaFailback](start-vbrcdpreplicafailback.md) cmdlet and want to specify the network mapping settings, you do not need to provide both DRNetwork and ProductionNetwork parameters. You can omit the DRNetwork parameter if you do not need to specify disaster recovery site networks.

Data Recovery

Restore to Amazon EC2

In this version, in the following cmdlets parameters were changed from obligatory to non-required:

| Cmdlet | Parameter |
| --- | --- |
| [New-VBRAmazonEC2DiskConfiguration](new-vbramazonec2diskconfiguration.md) | Include |
| [Start-VBRVMRestoreToAmazon](start-vbrvmrestoretoamazon.md) | DiskConfiguration |


