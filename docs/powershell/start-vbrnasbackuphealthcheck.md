---
title: "Start-VBRNASBackupHealthCheck (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrnasbackuphealthcheck.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Start-VBRNASBackupHealthCheck (obsolete)

In this article

Short Description

Performs a health check for the latest restore point in the backup chain and its repair if necessary.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Start-VBRUnstructuredBackupHealthCheck](start-vbrunstructuredbackuphealthcheck.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Perform a health check for the latest restore point of a specific job.

|  |
| --- |
| Start-VBRNASBackupHealthCheck -Job <CBackupJob[]> [-Repair] [-RunAsync] [-Force]  [<CommonParameters>] |

* Perform a health check of backup files created by the file backup job.

|  |
| --- |
| Start-VBRNASBackupHealthCheck -NASBackup <VBRNASBackup[]> [-Repair] [-RunAsync] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet performs a health check for the latest restore point in the backup chain and its repair if necessary. During the health check, Veeam Backup & Replication performs a CRC check for metadata and a hash check for data blocks in backup files to verify their integrity. If the health check returns notifications of some inconsistencies, you can run the backup repair. That requires running the cmdlet again with the Repair option enabled.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a file backup job. The cmdlet will perform a health check for this backup job. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRNASBackupJob](get-vbrnasbackupjob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| NASBackup | Specifies backup files created by the file backup job. The cmdlet will perform a health check for this backup job. | Accepts the VBRNASBackup[] object. To get this object, run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. |  |  |  |
| Repair | Defines that the cmdlet will repair missing data and metadata.  If you provide this parameter, the cmdlet will repair the missing metadata. Otherwise, the cmdlet will perform a health check of backup files and if corruption is detected, it will return a notification.  Note: First, run the cmdlet with this option disabled to perform the health check. After that, if there are any inconsistencies in the backup, run the cmdlet again with this option enabled. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform a health check without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupHealthCheck object that contains results of a health check for file backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing Health Check

|  |  |
| --- | --- |
| This example shows how to perform a health check for a file backup job.  |  | | --- | | $job = Get-VBRNASBackupJob  Start-VBRNASBackupHealthCheck -Job $job |  Perform the following steps:   1. Run the [Get-VBRNASBackupJob](get-vbrnasbackupjob.md) cmdlet. Save the result to the $job variable. 2. Run the Start-VBRNASBackupHealthCheck cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing Backup Repair

|  |  |
| --- | --- |
| This example shows how to perform a repair of corrupted data if the previously run health check detects them.  |  | | --- | | $job = Get-VBRNASBackupJob  Start-VBRNASBackupHealthCheck -Job $job -Repair |  Perform the following steps:   1. Run the [Get-VBRNASBackupJob](get-vbrnasbackupjob.md) cmdlet. Save the result to the $job variable. 2. Run the Start-VBRNASBackupHealthCheck cmdlet. Set the $job variable as the Job parameter value. Provide the Repair parameter. |

Related Commands

[Get-VBRNASBackupJob](get-vbrnasbackupjob.md)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
